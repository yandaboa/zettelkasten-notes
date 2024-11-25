[[Coursera Notes]]

Predicts numbers, infinitely many possible outputs


Data set used to train the model = training set

**Notation:**
$x =$ "input" variable, also called a feature
$y =$ "output" variable, also "target" variable
$m =$ number of training examples
$(x, y) =$ single training example
$(x^i, y^i) = ith$ training example

**process**
training set -> learning algorithm -> $f$ 
$f$ is a function, or the model
x is a feature, and the prediction is $\hat{y}$

for a straight line:
$f_{w,b}(x) = wx + b$
specifically, this is linear regression with one variable
univariate linear regression

$w, b$ = weights/parameters

***Cost Function***
for linear regression:
$J(w,b) = \frac{1}{2m} \cdot \sum_{i=1}^{m}(\hat{y}^i - y^i)^2$
Minimize cost function - find $w, b$
this way, $\hat{y}$ is close to $y$ for all $(x^i, y^i)$

Optimizing J(w), we should pick w = 1:

![[Screenshot 2024-09-12 at 5.40.19 PM.png]]

When adding b back in, the plot of the cost function looks like a 3D shape
- the 3d shape can also be represented as a contour plot

![[Screenshot 2024-09-12 at 5.47.23 PM.png]]

To minimize cost - [[Gradient Descent]]
When using multiple features: [[Multiple Linear Regression]]