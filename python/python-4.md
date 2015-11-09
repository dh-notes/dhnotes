# Strings

```
# create a sandbox folder
$ mkdir test/
$ cd test/

# redirect a string to the dummy file in terminal
$ echo "Hello world! It is a beautiful day. > test.txt

# make sure it worked
$ ls
$ cat test.txt

# start ipython
$ ipython
```

```
import nltk
from nltk.tokenize import RegexpTokenizer

# create a file object

file = open('test.txt')
type(file)

# create a string object from file object
# at this point, your text is just a long string

strings = file.read()
print(strings)
type(strings)
close('test.txt')

# a more "pythonic" way of doing the above
with open('test.txt', 'r') as f:
    strings = f.read()

# note that you don't have to close
# we expect the following to return True
f.closed

# create a list object from the stirng object
# tokens are just a list of all the words in your string
tokens = nltk.word_tokenize(s)
print(tokens)

# we can use a tokenizer that strips punctuation
# first initialize your tokenizer
# in other words, what kind of custom tokenizer do you want
# to instantiate?
tokenizer = RegexpTokenizer(r'\w+')

# the above tokenizer uses regular expressions
# to accept only the word characthers
# which include lower case [a-z], capitals, [A-Z]
# numerals [0-9], and the underscore [_]
# what other tokenizers can you make?
tokens = tokenizer.tokenize(s)

# turn your list object into the NLTK text object
# the text object was made for exploration in iPython 
# and other interactive shells

text = nltk(tokens)
text?

# read about nltk.Text
nltk.Text?

```

```
# write to file
with open("output.txt, 'w') as file:
    for token in tokens:
        file.write(token+'!\n')

# iPython understands unix commands
# use cat to check your work
cat output.txt
```
