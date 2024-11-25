Given multiple features,
cost function: $J(\vec{w}, b)$
**Gradient descent:**
$$x_j = x_j - a\frac{d}{d x_j} J(\vec{w}, b)$$
repeat for all weights + b:
$$ w_1 = w_1 - a \frac{1}{m} \sum_{i = 1}^{m}(f_{\vec{w}, b} (\vec{x}^i) - y^{i})x_1^{i}$$

**An alternative for gradient descent**
- only for linear regression
- solve for w, b, without iterations

Possible to use advanced linear algebra to solve without iterations
- doesnt generalize to other learning algorithms
- slow if # of features is large ( > 10,000)
- may be used by ML libraries in the backend

gradient descent is recommended
[[Feature Scaling]]