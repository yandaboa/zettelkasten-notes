0.5 is a common choice - if f > 0, predict 1. Else, 0. When does this happen?

![[Screenshot 2024-09-24 at 8.54.02 PM.png]]

following this logic, we can look at a model where there are two features

$$f_{\vec{w}, b} (\vec{x}) = g(z) = g(w_1 x_1 + w_2 x_2 + b)$$

As deduced earlier, predicting 1 or 0 hinges on the value of z... Thus, this is the **decision boundary:**
$$z = \vec{w} \cdot \vec{x} + b = 0$$
plugging in the above example of two features instead of the vectorized forms of w and x, with $w_1$ and $w_2$ both being equal to 1 and $b = -3$
$$ z = x_1 + x_2 - 3 = 0$$
$$x_1 + x_2 = 3$$
Visually, this looks like:

![[Screenshot 2024-09-24 at 8.59.15 PM.png]]

Similar intuition can be used to draw a non-linear decision boundary!

![[Screenshot 2024-09-24 at 9.00.34 PM.png]]

Keep increasing the degree of polynomial terms to get ever more complex decision boundaries (drawing ever more complex "shapes")
