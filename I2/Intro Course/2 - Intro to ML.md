Machine Learning is...
- patterns in data
- applied stats
- data-based
- subset of AI
VERY data driven

To spot the difference between objects, can look at characteristics/variables. 

Support Vector Machines
- Hyperplane: A substance of one dimension less than the dimension of the full space
- Support vectors: points that are closest to the hyperplane
- Margin: the distance between the hyperplane and the observations closest to the hyperplane (support vectors)
	- larger margin -> better
goal is to maximize the margin! Gives more accurate classifications
- wants to generate the best support vectors

Can make classification model better by adding features! 

# PCA - Principle Component Analysis
- dataset with many features/variables - when too large, difficult to manage/analyze
	curse of dimensionality! Noise in the model
- apply this before you create the SVM -> less data/dimensions, more efficient model
Subtracts the mean of the data, centering around the origin
- PCA decomposes into eigenvalues and eigenvectors, the eigenvalue implies variance
- transforms original data into a new space, reduces the dimensionality because we are now basing the new space on eigenvectors
- this extracts the most important 2 or 3 variables for the model -> gets rid of features that distract from the relationship the model is trying to learn
Benefits
- runs faster with less dimensions
- reduces noise

# Train/Test Splits
Common ratio: 70 : 30
Validation set: Subset of data to tune model hyper parameters and prevent overfitting before final evaluation on the test set
- this is separate from the test set!!!

hyper parameter: chosen setting before training the model, like how fast it learns or how complex it is. These choices affect how well the model works.

**Overfitting** - performs very well on training data, but very poorly on new data. Overtrained itself on data it already has, can't adapt to new data. Good accuracy, but can't be applied to much else.

Training set - given to model for learning
validation set - model runs on this to help us tune hyper parameters
test set - final conclusions are made using the test set

**Confusion Matrix** - a 2 by 2 grid, showing true and false positives. 
**Accuracy** = (true positive + true negative)/total predictions
**Precision** = true positives/(true positives + false positives)
**example:** given a population with 2% infected, the model could just say it's 0% infected. Pretty close! (not) That's why it's important to study the confusion matrix/precision as well as accuracy
