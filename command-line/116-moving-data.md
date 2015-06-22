---
tutorial: "Command Line Fundamentals"
section: "Unit 16: Moving Data"
author: Dennis Tenen
update: "6/19/15"
---

In this section we will learn how to move data between local and remote
machines, to sync, and to back up files across the network.

## Secure Copy (scp)

```
# remote to local
# it seems obvious in retrospect, but the directions assume you are working

# This will copy the file from your current local directory to some path on your
# your remote, starting with the home directory for `your_username`. Use -r flag
# to move a directory vs. file.

# the remote path is relative to the home directory (the stuff after the colon)

scp your_username@remotehost.edu:path/to/foobar.txt /some/local/directory`
```

```
# local to remote

scp foobar.txt your_username@56.727.xxx.90:some/path/on/your/server

```

```
# with keys
scp -i /path/keys.pem source target
```

```
# rsync
coming soon
```
