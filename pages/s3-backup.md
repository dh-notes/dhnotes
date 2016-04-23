These directions assume some comfort with command line tools. I suggest a managed solution (like Dropbox or Jungle Disk) if these steps are too difficult for the reader.

- Approximate costs for [S3](http://aws.amazon.com/s3/pricing/) and [Glacier](http://aws.amazon.com/glacier/pricing/).

- In your AWS Console navigate to Identity and Access Management (IAM) console. Create a new user. Attach the Amazon S3 full access policy. Note Access Key ID and Secret Access Key.

- Back in the AWS Console, navigate to S3. Create a bucket to store your backup. Give it a name. Select a reasonable region near you.

- Navigate to the bucket. Enable versioning in the properties. In the "Lifecycle" tab create a rule to archive objects XX days after creation. This will help keep the costs down.

- Back on your machine `pip install aws-cli` or [follow the directions from Amazon](http://docs.aws.amazon.com/cli/latest/userguide/installing.html) to install aws-cli.

- In your home directory `mkdir .aws/` and `touch config`. Edit `config` to include:

```
[default]
aws_access_key_id=XXXXXXXXXXXXX
aws_secret_access_key=XXXXXXXXXXXXXXXXXXXXXXXXXXXX

# optionally limit the number of concurrent requests
# the default is 10
s3 =
  max_concurrent_requests = 5
```
- Set up `aws-cli` [auto completion](http://docs.aws.amazon.com/cli/latest/userguide/cli-command-completion.html).

- Run the first backup manually: `aws s3 sync SOURCE s3://TARGET-BUCKET --exclude "*.git/*"`

- Optionally, [install](http://monkey.org/~marius/pages/?page=trickle) `trickle` to limit bandwidth. Wrap `aws` with `trickle` like so: `trickle -s -d 1000 -u 500 aws s3 sync SOURCE s3://TARGET-BUCKET`

- Create log and bin directories in your home. In `~/bin/` create and edit your backup script for automation. Save as `aws-backup.sh` or something along the lines.
```
#!/bin/bash
logpath=/home/USERNAME/log/backup.log
stamp="$(date --iso-8601)"

# i am only logging the last backup attempt
echo "last backup on $stamp" > $logpath

# run aws and output to log file
aws s3 sync ~/gDrive s3://YOUR-BUCKET --exclude "*.git/*" >> $logpath
```
- For *nix-based distributions: Set up `anacron` to run daily or weekly. `man anacron` and `man anacrontab` first. Then edit `/etc/anacrontab`. I set mine up to backup every three days, following a 10 minute delay after the machine starts.

```
#  .------------------------ frequency in days
#  |     .------------------ delay after starting in minutes
#  |     |       .---------- unique job identifier (no spaces)
#  |     |       |               .------ command
#  |     |       |               |   
#  |     |       |               |  
# ---	---     -----      -------------------------

3       10 	backup		sh ~/bin/aws-backup.sh
```
- On a Mac use [Automator](https://en.wikipedia.org/wiki/Automator_%28software%29) + [iCal](http://web.archive.org/web/20150626000635/https://support.apple.com/en-us/HT201747) to schedule.
