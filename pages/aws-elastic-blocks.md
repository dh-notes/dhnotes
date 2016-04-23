### Attaching a Volume
- Create a volume from the AWS panel
- SSH into your instance
- Run `lsblk` "to view your available disk devices and their mount points"
- You will likely need to create a file system on a new drive. Run `sudo file -s /dev/xvdXXX` to list system type.
- If the file type is "sticky data" and you know the drive is empty, run `sudo mkfs -t ext4 /devx/xvdXXX` to build a Linux filesystem on the drive.
- Use `$ sudo mkdir` to create a mount point. It is in good form to mount under `/mnt`
- Mount by running `sudo mount /dev/DEVICE_NAME /mnt/MOUNT_POINT`
- `$ df -h` to see if everything mounted correctly
- Optionally, make symbolic links from the mount point into your home directory, or wherever else. 
- Think about group ownership and permissions to the mount point. Use `$ chgrp`, `$ chmod` to fix this, depending on your setup.

### Automate attachment on server reboot
- Don't touch anything until you take the [filesystem tour](http://web.archive.org/web/20140224004333/http://tuxradar.com/content/take-linux-filesystem-tour/).
- Make a copy of your fstab by running `$ sudo cp /etc/fstab /etc/fstab.orig`
- Tread carefully here, if you brick *fstab* your server will hang on boot--if that happens, detach root volume from your instance, attach to a new instance as a secondary volume, restore *fstab* and reattach to the original instance
- `$ man fstab` before touching anything
- Edit *fstab*. It should look something like this:  
```Shell
# <source>      <mount point>           <type>          <options>                     <dump> <pass>
/dev/xvda1      /                       ext4            defaults,barrier=0            1       1
/dev/xvdb       /mnt/osp-archive-mount  ext4            nofail,defaults               1       2
```
*xvda1* in this case is my root (setup automatically), and *xvdb* is the one I added. The `nofail` option is quite important--it will ignore the drive if the system is not able to mount it on boot
- `$ sudo umount /dev/xvdb` to unmount the disk
- `$ sudo sudo mount -a` to try mounting using your new *fstab* options
- Say a little prayer and stop + restart your instance through the AWS console. If all goes well you will be able to login after restart and your drive will be mounted. (Don't forget to re-associate your elastic IP).

### Nightly Backup to Glacier
We now want to automate backups to Amazon's cheap Glacier storage. We are going to be using the [AWS Snapshot Tool](https://github.com/evannuil/aws-snapshot-tool) by *evannuil*.
- Begin by installing python package manager [*pip*](http://web.archive.org/web/20140120043532/http://www.pip-installer.org/en/latest/installing.html). It will look something like: `sudo aptitude install python-pip`
- Install [Boto](http://web.archive.org/web/20140120044946/http://docs.pythonboto.org/en/latest/getting_started.html), the Python interface to Amazon Web Services. It will probably look something like this: `sudo pip install boto` 
- Create the `boto.cfg` file which will hold your credentials. `sudo vim /etc/boto.cfg' Follow the instructions [here](http://web.archive.org/web/20140120045226/http://docs.pythonboto.org/en/latest/boto_config_tut.html). In my case it looks something like this:
```Shell
[Credentials]
aws_access_key_id = <your_access_key_here>
aws_secret_access_key = <your_secret_key_here>
```
- Change permissions to *boto.cfg* to read / write access by sudo only. `sudo chmod 600 boto.cfg`
- Setup IAM through AWS console.
```Shell
"Action": [
        "ec2:CreateSnapshot",
        "ec2:CreateTags",
        "ec2:DeleteSnapshot",
        "ec2:DescribeAvailabilityZones",
        "ec2:DescribeSnapshots",
        "ec2:DescribeTags",
        "ec2:DescribeVolumeAttribute",
        "ec2:DescribeVolumeStatus",
        "ec2:DescribeVolumes"
      ],
```
- Setup messaging.
- Install AWS Snapshot Tool.
- Configure AWS Snapshot Tool:
```Python
config = {
    'ec2_region_name': 'us-east-1',
    'ec2_region_endpoint': 'ec2.us-east-1.amazonaws.com',
    'tag_name': 'tag:MakeSnapshot',
    'tag_value':    'True',
    'keep_day': 5,
    'keep_week': 5,
    'keep_month': 11,
    'log_file': '/tmp/makesnapshots.log',
}
```
- Tag volumes 
- Crontab:
```Shell
$ crontab -l

# mon-fri 30 3 * * 1-5 /home/zope/aws-snapshot-tool/makesnapshots.py day

# every sat 30 3 * * 6 /home/zope/aws-snapshot-tool/makesnapshots.py week

# first sun 30 3 1-7 * 0 /home/zope/aws-snapshot-tool/makesnapshots.py month
```

### Growing Volumes
- Stop instance (through the AWS panel)
- Detach volume (in AWS panel)
- Make a snapshot of the old volume (in AWS panel)
- Create a new, larger volume form the snapshot. Make sure it is in the same zone.
- Attach new volume.
- Log into the server. Run `$ e2fsck -f /dev/sdx2` to check the file system on the new block.
- Run `$ resize2fs -p /dev/sdx2` to resize.
- Run `$ e2fsck -f /dev/sdx2` and `$ tune2fs -l /dev/sdx2` for diagnostics. `e2fsck` might be in `/sbin`.
- Mount the volume by running `$ mount /dev/sdx2 /mnt/ebs2`
- `$ df -h` to see disk space usage

#### Sources + Useful Links
- [http://web.archive.org/web/20140118041157/http://edoceo.com/blog/2009/02/amazon-ebs-how-to-grow-storage]
- [http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-using-volumes.html]
- [http://web.archive.org/web/20140120042715/http://www.coresoftwaregroup.com/blog/automated-amazon-ebs-volume-snapshots-with-boto]
- [http://web.archive.org/web/20140120044946/http://docs.pythonboto.org/en/latest/getting_started.html]
