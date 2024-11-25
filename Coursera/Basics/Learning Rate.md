$w = w - \alpha \frac{d}{dw} J(w)$
$\alpha =$ learning rate

if learning rate is too low, gradient descent may be slow.
if learning rate is too large, w will be updated by giant steps that never settle at the local minimum. The cost can increase, resulting in a cycle that gets further and further from the minimum. Aka. fail to converge, diverge
overshooting ^

**Choosing a Learning Rate**

If there are bumps (ups and downs) in the cost function, then the learning rate is probably incorrect. Probably too big. Can decrease alpha to get J to decrease.
- also make sure no bugs with implementation, use negative sign before the derivative
- a small enough $\alpha$ should always decrease -> converge
Can be useful to try different powers of alpha:
0.1, 0.01, 0.001, 1, 10
Then, can start multiplying by 3 or something
0.3, 0.03...
basically, binary search for the proper learning rate

![[Screenshot 2024-09-23 at 12.30.13 AM.png]]