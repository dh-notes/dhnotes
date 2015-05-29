---
title: "Intro to Operating Systems and Command Line Interfaces (CLI)"
author: Dennis Tenen
---

## Why command line?

- core skill
- simple
- powerful
- lasting
- universal
- hackable
- fun

## Bash

> Bash is the GNU Project's shell. Bash is the Bourne Again SHell. Bash is an
sh-compatible shell that incorporates useful features from the Korn shell (ksh)
and C shell (csh). It is intended to conform to the IEEE POSIX P1003.2/ISO
9945.2 Shell and Tools standard. It offers functional improvements over sh for
both programming and interactive use. In addition, most sh scripts can be run
by Bash without modification.<sup>1</sup>

1. http://www.gnu.org/software/bash/

## Table of contents

- [Unit 1: Finidng your way](https://github.com/denten/dhnotes/blob/master/cli-basics.md#level-1-finding-your-way)
- [Unit 2: Files and folders](https://github.com/denten/dhnotes/blob/master/cli-basics.md#level-2-files-and-folders)
- [Unit 4:]()
- [Unit 5:]()
- [Unit 6:]()
- [Unit 7:]()
- [Unit 8:]()
- [Unit 9:]()
- [Unit 10:]()
- [Unit 11:]()
- [Unit 12:]()

## Unit 1: Finding your way

```
ls
ls -l
pwd
man man (q to exit)
mkdir test/
cd test
cd ..
cd ~
cd /
history
```

**Notes**: Tab complete everything. Do not advance until you understand the difference
between relative and absolute paths. Man everything, *nix has amazing
documentation.

**Explore**: [Filesystem Hierarchy Standard](http://www.pathname.com/fhs/)

**Bonus**: `pushd`, `popd`, `cd -`

## Unit 2: Files and folders

```
man man
mkdir
touch filename
cp oldpath/oldfile newpath/newfile
mv oldpath/file newpath/file
rm -i path/filname
rm -r foldername
cat filename
head filename
tail filename
```

![Anatomy of a UNIX Command.](images/cmd-anatomy.jpg)

> *Figure 1* Anatomy of a UNIX Command. Via
[Texas A\&M High Performance Research Computing](http://web.archive.org/web/20150529023907/http://sc.tamu.edu/help/general/unix/unix.html)

**Notes**: File names are case sensitive. Think of the syntax as "verb, adverb,
object noun". What separates these? Blank space. What happens to blank space in
file names? For this reason, it is good hygiene not to use spaces or capitals
when naming files. Rename with `mv`. Open your graphical file manager and
follow along as you move / create / delete files. `cat` a `.pdf` file, `.docx`,
and `.txt`. `rm` is dangerous! Consider creating an `archive/` folder and using
`mv` instead of `rm` for a safer alternative. The `-i` flag will ask for
confirmation at least.

**Explore**: [Take the Linux Filesystem Tour](http://web.archive.org/web/20140224004333/http://tuxradar.com/content/take-linux-filesystem-tour#null)

**Bonus**: `ctr+shift+R [start typing one of the commands you used above]`, repeat to
cycle through

## Unit 3: Permissions

```
cd /
touch test.txt
sudo !!
cd -
touch test.txt
chmod u-w test.txt
nano test.txt
man sudo
```

![List view.](images/perm.png)

> *Figure 2* Via
[Via UC Irvine](http://www.ics.uci.edu/computing/linux/file-security.php)

**Notes**: Think twice before sudo.

**Explore**: [IBM developerWorks: Manage file permissions and ownership](http://www.ibm.com/developerworks/library/l-lpic1-v3-104-5/)

**Bonus**: 

octal | decimal   | ls -l |permission
------|-----------|-------|--------------
000   | 0 (0+0+0) | ---   | none
001   | 1 (0+0+1) | --x   | execute
010   | 2 (0+2+0) | -w-   | write
011   | 3 (0+2+1) | -wx   | write + execute
100   | 4 (4+0+0) | r--   | read
101   | 5 (4+0+1) | r-x   | read + execute
110   | 6 (4+2+0) | rw-   | read + write
111   | 7 (4+2+1) | rwx   | read + write + execute

## Unit 4: Pipes and redirects

```
cat filename | less
man less
echo "hello world"
echo "hello world" > test.txt
echo "hello world 2" > test.txt
echo "hello world 3" >> test.txt
```

## Unit 5: Search

up and down to cycle through history, `history`, pipes!, `history | less`,
`history | grep "test.txt"`, `nano`, `cat`

Bonus: `ctrl-r`, repeat to cycle

`grep`, `find`, `awk`

Note the complimentary use of `-print0` and `-0` to handle white spaces in file names.
`find -name "*.pdf" -print0 | xargs -0 lpr`

## Unit 6: Networking

TBA

## Unit 7: Users & Groups

TBA

## Unit 8: Text manipulation

TBA

## Unit 9: Scripting

TBA

## Unit 10: Scheduling
## Unit 11: Package management

## Resources

- [commandlinefu.com](http://www.commandlinefu.com)
