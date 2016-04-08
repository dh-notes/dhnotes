# Data Types and Iterables

```
# starting here we are in an editor
# use nano for simplicity of sublime for the cool factor
# talk about plain text vs. word
# variable scoping

global_var = 'foo'
def scoping():
    local_var = 'bar'
    print global_var
    print local_var

# note the inline comment
scoping()
print global_var
print local_var  # this gives an error

# lists
a = [apple, orange, banana]

# list comprehension
colors = [ "red", "green", "yellow", "blue" ]
things = [ "house", "car", "tree" ]

colored_things = [ (x,y) for x in colours for y in things ]

# note that print is kind of an exception as far as functions go (in 2.7, at
least)
print coloured_things
```

**Explore:** [Git, list authors sorted by the time of their first
contribution](https://gehrcke.de/2015/06/git-list-authors-sorted-by-the-time-of-their-first-contribution/),
by Jan-Philip Gehrcke
