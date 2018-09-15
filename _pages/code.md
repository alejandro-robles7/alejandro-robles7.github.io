---
permalink: /code/
---

```python
## Function to calculate power means
from math import pow

def pmeans(filepath, p):
    with open(filepath, 'r') as f:
        total_lines = f.readlines()

    n = len(total_lines[0].split(' ')[1:-1])
    doc2vec = [0] * n

    for word in total_lines:
        data = [float(x) for x in word.split(' ')[1:-1]]
        for i, weight in enumerate(data):
            doc2vec[i] = doc2vec[i] + pow(weight, p)

    for i, element in enumerate(doc2vec):
        doc2vec[i] = pow((element / n), (1.0 / p))

    return doc2vec

site2vec = pmeans('vectors.txt',2)
```
