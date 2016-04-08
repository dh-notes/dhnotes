# Strings

## Hunting the Whale
<sup>†</sup><sub>Mimics a [similar excercise](https://github.com/xpmethod/dhnotes/blob/master/command-line/109-text.md#hunting-the-whale) in the command line tutorial</sub>


```
# open file and read contents into a list of lines
with open('moby.txt', 'r') as f:
    lines = f.read().splitlines()
```

```
# replace whale for chicken in every line and print results
for line in lines:
    if 'whale' in line:
        print(line.replace('whale', 'chicken'))
```

```
from string import punctuation
from collections import Counter

tokens = []

for line in lines:
    for word in line.split():
        tokens.append(word.strip(punctuation).lower())

# display 100 most common types
types = Counter(tokens)
types.most_common(100)
```
