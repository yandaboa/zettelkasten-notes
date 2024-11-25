Can fit more complex models than just linear lines 
$$f(\vec{w}, b) = w_1x + w_2 x^2 + b$$
However, the quadratic above wouldn't work for something like predicting house prices based on size, since the quadratic implies the size eventually decreases.
$$f(\vec{w}, b) = w_1x + w_2 x^2 +w_3 x^3 + b$$
Would likely fit better

Or, even better:
$$f(\vec{w}, b) = w_1x + w_2 \sqrt{x} + b$$
