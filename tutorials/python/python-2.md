## Comparisons

https://docs.python.org/3/library/stdtypes.html#comparisons

| Operation | Meaning                 |
|-----------|-------------------------|
| `<`       | strictly less than      |
| `<=`      | less than or equal      |
| `>`       | strictly greater than   |
| `>=`      | greater than or equal   |
| `==`      | equal                   |
| `!=`	    | not equal               |
| `is`      | object identity         |
| `is not`  | negated object identity |

```
# Booleans
# this differs from assignment
5 == 5
5 == 6
a = "hello"
b = "world"
c = "hello"
a == b
a == c

# other relational operators
# try to take a guess at the result
# before pressing enter
a != b
a = 5
b = 7
a != b               # a is not equal to b
a > b                # a is greater than b
a < b                # a is less than b
a >= b               # a is greater than or equal to b
a <= b               # a is less than or equal to b
```

## Control structures

```
a = 5
b = 6

if a > 0:
    print "a is positive"

# my first infinite loop
while a > 0:
    print "i am the most positive person ever!!!!"

if (a > 0) and (b > 0):
   print "sucess"

# does it exist?
if a:
   print a

if c:
   print c

# this is a better way to do it
try:
    c
except NameError:
    print "nothing to see here folks!"

# alternative execution
def test_even(bob):
   if bob%2 == 0:
      print 'number is even'
   else:
      print 'number is odd'

test_even(4)
test_even(5)

# chained conditional
# in pseudocode
# only one (first matched) branch is executed
if condition a:
    do something
elif
    do something else
elif
    do yet another thing
else
    do something else entirely

# nested conditionals
if a == b:
    if b == c:
        if c == d:
            do something
        else:
            do something else
    else:
        do someting else
else:
    do something else

# recursion!
# lets step through this
def countdown(n):
    if n <= 0:
        print 'Blastoff!'
    else:
        print n
        countdown(n-1)

# infinite recursion wooooo....
def and_beyond():
    print "to the infinity!"
    and_beyond()

# challenge: count maximum recursion depth

# raw input
text = raw_input()

# challenge: do something cool with input and control structures
```
