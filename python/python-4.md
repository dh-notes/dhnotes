# NLTK

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

s = file.read()
print(s)
type(s)

# create a list object from the stirng object
# tokens are just a list of all the words in your string
# we are using a tokenizer that strips punctuation
# you can also use the less complicated tokenizer
# to preserve punctuation like this
# tokens = nltk.word_tokenize(s)

tokenizer = RegexpTokenizer(r'\w+')
tokens = tokenizer.tokenize(s)

# turn your list object into the NLTK text object
text = nltk(tokens)
```
