Simple AES encryption with Python
=================================

I am using the [galois package](https://pypi.org/project/galois/) in the mixColumns function. This package is not included in the standard library, so you will need to install it with pip.

```bash 
pip install galois 
```

To use the galois package for a matrix multiplication, you need to convert the matrix to a galois field. This is done with the following code:

```python 
from galois import GF 
gf = GF(2**8, irreducible_poly = 0x11b)

def mixColoums(state):
    mix_matrix = [[0x02, 0x03, 0x01, 0x01],
                  [0x01, 0x02, 0x03, 0x01],
                  [0x01, 0x01, 0x02, 0x03],
                  [0x03, 0x01, 0x01, 0x02]]

    matrix = gf(mix_matrix)

    results = [matrix @ gf(s) for s in state]
    return results
```