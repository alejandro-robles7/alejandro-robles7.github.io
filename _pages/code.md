---
permalink: /code/
---

```python
## Function to calculate power means
from math import pow

def pmeans(filepath, p):
    with open(filepath, 'r') as f:
        all_words = f.readlines()

    n = len(all_words) # Number of words
    m = len(all_words[0].split(' ')[1:-1]) # Number of weights representing each word
    doc2vec = [0] * m

    for word in all_words:
        data = [float(x) for x in word.split(' ')[1:-1]]
        for i, weight in enumerate(data):
            doc2vec[i] = doc2vec[i] + pow(weight, p)

    return [pow((numerator / n), (1.0 / p)) for numerator in doc2vec]

site2vec = pmeans('vectors.txt',2)
```
