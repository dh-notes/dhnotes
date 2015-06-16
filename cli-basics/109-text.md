---
tutorial: "Command Line Basics"
section: "Unit 9: Text Manipulation"
author: Dennis Tenen
update: "5/29/15"

---

## Unit 9: Text manipulation

```
cut
paste
join
strings
```

### Popping the hood

```
wget link/moby.pdf (use curl on macs)
pdftotext moby.txt``
cat moby.txt
cat moby.pdf
clear
xxd moby.txt
xxd moby.pdf
echo "how many words does it take?" > test.txt
wc -w test.txt
wc -l test.txt
wc -m test.txt
man wc
```

### Putting all your fruits into one basket

> lines and words, destructive vs. non-destructive transformations
> (munging), more pipes

1. add your fruits  
`   echo "orange banana pear tomato banana pear orange apple apple strawberry nectarine" > fruit.txt`

2. add another one  
`    echo "banana" >> fruit.txt`

3. substitute space for newlines  
`    sed 's/\s/\n/g'` (Linux)  
`    sed 's/[[:space:]]/\'$'\n/g' fruits.txt` (Mac)  

4. remove bad fruit  
`    echo "nectarine" > bad-fruit.txt`  
`    echo "tomato" >> bad-fruit.txt`  
`    cat fruit.txt | grep -vf bad-fruit.txt`  
`    cat fruit.txt` (to see if it worked)  

5. sort and count  

`    sort fruits.txt > sorted-fruits.txt`  
`    uniq -c sorted-fruits.txt`  

### Rewriting *Moby Dick*  

> dataflow programming, bag of words, stop words

1. find the whale  
`    grep "whale" moby.txt`

2. substitute whale for chicken globally  
`    cat moby.txt | sed 's/whale/chicken/g' > chicken.txt`

3. find the remaining whales  
`    grep "Whale" chicken.txt`

4. remove punctuation  
`    cat file.txt | tr -d "[:punct:]" > moby-nopunct.txt`

5. translate all upper case into lower  
`    cat moby-nopunct.txt | tr '[:upper:]' '[:lower:]' > moby-clean.txt`

6. sort by word frequency  
`    cat file.txt | sed 's/\s/\n/g' | sort | uniq -c | sort -hr > test.txt`
(Linux)  
`    cat file.txt | sed 's/[[:space:]]/\'$'\n/g' | sort | uniq -c | sort -k1 >
file_wc.txt` (Mac)
