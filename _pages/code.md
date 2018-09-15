```python
from math import pow

## Function to calculate power means
def pmeans(filepath, p):
    with open(filepath, 'r') as f:
        total_lines = f.readlines()

    n = len(total_lines[0].split(' ')[1:-1])
    doc2vec = [0] * n

    for e in total_lines:
        data = [float(x) for x in e.split(' ')[1:-1]]
        for i in range(len(data)):
            doc2vec[i] = doc2vec[i] + pow(data[i], p)

    for i, element in enumerate(doc2vec):
        doc2vec[i] = pow((element / n), (1.0 / p))

    return doc2vec
    
site2vec = pmeans('vectors.txt',2)
```
