Represent inputs and weights as vectors

```python
w = np.array([1.0, 2.5, -1.3])
b = 4
x = np.array([10, 20, 30])

f = np.dot(w, x) + b
```

The above code uses numpy to compute the dot product of the weights and inputs
1. simpler code
2. runs much faster due to numpy running the calculation on parallel processing

$$\frac{3}{4}$$