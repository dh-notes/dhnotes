---
tutorial: "Command Line Basics"
section: "Unit 7: Networking"
author: Dennis Tenen
update: "5/29/15"

---

## Unit 7: Networking

```
ping
traceroute
ssh -LD
wget
curl
rsync
dig
ip
ifconfig
netstat
mtr
```

**Excercise:** Parse the following code which mirrors a single page along with all
visible dependencies (like images and styles). From [dannguyen/wget-snapshotpage.md]
(https://gist.github.com/dannguyen/03a10e850656577cfb57).

```
# short form
wget -E -H -k -K -nd -N -p -P thepageslug \
     http://www.thepage.to/save/four/posterity.html
```

```
# long form
wget --adjust-extension --span-hosts --convert-links --backup-converted \
     --no-directories --timestamping --page-requisites \
     --directory-prefix=thepageslug \
     http://www.thepage.to/save/four/posterity.html
```

