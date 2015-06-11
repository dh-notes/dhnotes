---
title: "Python for Human{s|ists}"
author: Dennis Tenen
update: "5/29/15"

---

## What is a programming language?

control structures + data types + built-in functions + syntax + interpreter

## Why Python

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

- [Unit 1: Finding your way](https://github.com/denten/dhnotes/blob/master/cli-basics/101-gps.md)
- [Unit 2: Files and folders](https://github.com/denten/dhnotes/blob/master/cli-basics/102-files.md)
- [Unit 3: Permissions](https://github.com/denten/dhnotes/blob/master/cli-basics/103-permissions.md)
- [Unit 4: Pipes and redirects](https://github.com/denten/dhnotes/blob/master/cli-basics/104-pipes.md)
- [Unit 5: Search](https://github.com/denten/dhnotes/blob/master/cli-basics/105-search.md)
- [Unit 6: Filters](https://github.com/denten/dhnotes/blob/master/cli-basics/106-filters.md)
- [Unit 7: Networking](https://github.com/denten/dhnotes/blob/master/cli-basics/107-network.md)
- [Unit 8: Users and Groups](https://github.com/denten/dhnotes/blob/master/cli-basics/108-users.md)
- [Unit 9: Text Manipulation](https://github.com/denten/dhnotes/blob/master/cli-basics/109-text.md)
- [Unit 10: Scripting](https://github.com/denten/dhnotes/blob/master/cli-basics/110-script.md)
- [Unit 11: Scheduling](https://github.com/denten/dhnotes/blob/master/cli-basics/111-schedule.md)
- [Unit 12: Package management](https://github.com/denten/dhnotes/blob/master/cli-basics/112-package.md)

## Resources

- [commandlinefu.com](http://www.commandlinefu.com)
## Types & Variables

```
$ python
a = "hello world!"
b = 57
c = 75
d = b + c
d = a + b [!]
type(a)
type(c)
```

## Operator overload & weak typing

```
exit()
$ ipython
a = "hello"
b = "world"
c = a + b
print(c)
```

## Functions

[https://docs.python.org/2/library/functions.html][1]

[1]: https://docs.python.org/2/library/functions.html 

```
a.[tab]

def print_twice(bob):
    print(bob)
    print(bob)

a = "hello world!"

print_twice(a)

```


