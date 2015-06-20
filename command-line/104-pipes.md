---
tutorial: "Command Line Basics"
section: "Unit 4: Pipes and redirects"
author: Dennis Tenen
update: "5/29/15"

---

## Unit 4: Pipes and redirects

```
cat filename | less
```
```
# what is a paginator?
man less
```
```
# read about "standard input" and "standard output"
echo "hello world"
echo "hello world" > test.txt
echo "hello world 2" > test.txt
echo "hello world 3" >> test.txt
```
```
# what does the -e flag do?
# research "backslash escape"
echo -e "hello\nworld!" >> test.txt
```
```
# save your session!
history
history | tail -5
history | tail -5 >> history-dump.txt
wc -l < history-dump.txt >
```
