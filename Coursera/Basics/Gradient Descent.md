[[Coursera Notes]]

An algorithm that can be used to minimize the cost function: $min_{w, b} J(w,b)$

Outline:
start with some $w, b$
keep changing $w, b$ to minimize J
until we settle at a minimum
![[Screenshot 2024-09-13 at 12.08.10 AM.png]]
At each step, take the mathematically steepest descent, until a "valley" (lowest cost) is reached
However, the lowest cost is only a local minima, since there can be multiple valleys

**Implementation**
gradient descent algorithm:
$w = w - \alpha \cdot \frac{d}{dw}J(w,b)$
$\alpha =$ learning rate, how large each step is down hill. large alpha = very aggressive gradient descent
$\frac{d}{dw}J(w,b)$ = derivative term, the direction of the steps to take
for b, the algorithm looks like:
$b = b-\alpha \cdot \frac{d}{db}J(w, b)$
For gradient descent, the above two steps are repeated until they converge - until neither change much. Also, while updating, w and b should be simultaneously updated.

Correct: simultaneous update
$tmp\_w= w - \alpha \cdot \frac{d}{dw}J(w,b)$
$tmp\_b = b-\alpha \cdot \frac{d}{db}J(w, b)$
$w = tmp\_w$
$b = tmp\_b$

Choosing a learning rate: [[Learning Rate]]

"Batch" gradient descent
- batch means that all of the training examples are used during gradient descent
