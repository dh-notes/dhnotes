Instruction assume Debian 64bit

- (AWS Console): Launch your new instance  

- (Local): Download your keys key, and run `$ sudo chmod 600 <PATH>/yourkey.pem` to make sure the file is properly secured

- (AWS Console, optional): Associate an elastic IP (it will save you time later)  

- (AWS Console): Modify your security group in AWS console to allow SSH access. Select `Create a new rule: SSH` > `Source: 0.0.0.0/0` > `Add Rule` > `Apply Rule Changes`     

- (Local): Use `$ ssh -vi path/to/keys.pem admin@instance`. The instructions read "You must use an SSH client to access this instance, authenticating with your SSH key as the user 'admin'; you may then use 'sudo -i' to gain root (administrator) privileges."  

- (Remote): Create your users + groups. Add yourself to sudo by executing `$ sudo usermod -aG sudo <username>`. Then use `$ sudo adduser`, `$ sudo groupadd`, and `$ sudo usermod -aG nameofgroup username` to reflect your project organization and file permission levels.   

- (Remote): Create `.ssh/` directory in your `/home/USERNAME` directory by running `mkdir /home/USERNAME/.ssh`. Run `cp /home/admin/.ssh/authorized_keys /home/USERNAME/.ssh/`. `chown` and `chgrp` the `authorized_key` to the user. Check by running `ls -la`. Optionally, remove key requirement (for people to login with id/password only) by editing `/etc/ssh/sshd_config`, and setting `PasswordAuthentication yes`, then `$ sudo service ssh restart` for changes to take effect. In case you are wondering, "sshd_config is for incoming connections, ssh_config for outgoing."  

- (Remote): Now would be a good time to do a system update. On Debian / Ubuntu run `sudo aptitude update` follwed by `sudo aptitude dist-upgrade`  
 
- (Remote): [[Mount volumes | Working with AWS Elastic Blocks]].
