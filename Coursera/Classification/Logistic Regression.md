- fits a sigmoid/logistic function to the data
$$ g(z) = \frac{1}{1 + e^{-z}}$$
- only outputs values between 0 and 1, with z ranging from $-\infty$ to $\infty$, or whatever the max and min of the input x is

to get to the tunable logistic regression model...
$$z = w \cdot x + b$$
$$ g(z) = \frac{1}{1 + e^{-z}}$$
Combining the two, 
$$f_{\vec{w},b} (\vec{x}) = g(\vec{w} \cdot \vec{x} + b) = \frac{1}{1 + e^{-(\vec{w} \cdot \vec{x} + b)}}$$

**Interpreting the ouput of logistic regression**
f(x) is the probability that classification is 1, given input of x

When reading research papers:
![[Screenshot 2024-09-24 at 7.32.26 PM.png]]
