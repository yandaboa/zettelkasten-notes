Feature and Parameter Values
When using multiple features that have different value ranges, the weight for the larger value range will be smaller, while the weight for the smaller value range will be bigger
- this results in a lopsided contour plot
However, when performing gradient descent on the lopsided contour plot, the weights might "bounce," not moving correctly to the minimum

**solution: scale the input values to be from 0 to 1**

**Ways to scale:**

- could divide each original feature value by the maximum that appears
- mean normalization: rescale so that features are centered around 0
	- results in values between 1 and -1
	- ![[Screenshot 2024-09-22 at 11.31.48 PM.png]]
- Z-score normalization: calculate mean and standard deviation, then calculate the z score for each value to normalize

Can verify that features all have similar ranges by plotting them