---
tutorial: "Command Line Basics"
section: "Unit 2: Files and folders"
author: Dennis Tenen
update: "5/29/15"
---

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
