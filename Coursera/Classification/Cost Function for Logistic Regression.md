The cost for logistic regression is slightly different than for linear regression — using the same cost function would result in a cost curve that is not convex - meanig the model would get stuck in numerous local minima.
\
Given that the cost function is:
$$ \frac{1}{m}\sum_{i = 1}^{m} \frac{1}{2}(\vec{x}^i - y^i)^2$$
It can also be rewritten by designating the parts being summed the *loss* function:
$$ L(f_{\vec{w}, b} (\vec{x}^i) - y^i)$$
then,
$$ \frac{1}{m}\sum_{i = 1}^{m}L(f_{\vec{w}, b} (\vec{x}^i) - y^i)$$
So basically, the cost function is the average of all the loss functions.

## Logistic loss Function
$$L(f_{\vec{w}, b}(\vec{x}^i), y^i) = \begin{cases}
-log(f_{\vec{w}, b} (\vec{x}^i)) & \text{if } y^i = 1,\\
-log(1-f_{\vec{w}, b}(\vec{x}^i))  & \text{if } y^i = 0 \\
\end{cases}$$
This piecewise function is used so that in both cases, the algorithm is incentivized to produce functions that are closer to the true value.

A visual explanation for the loss function:
![[Screenshot 2024-09-25 at 10.55.01 PM.png]]

The same logistic loss function, but when it is a negative result.
![[Screenshot 2024-09-25 at 10.57.15 PM.png]]