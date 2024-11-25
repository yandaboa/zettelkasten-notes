You can create new features by transforming or combining existing features of a model
- this is done based on existing knowledge/intuition
- example: instead of just having frontage/depth of a house's lot, also include its area by multiplying the two features

Useful to note that you can engineer features that turn linear regression into polynomial regression
- the model would then emphasize the feature(s) that are most representative of the relationship between x and y (maximizing the relevant feature's weights and minimizing others)
- make sure to apply feature scaling when engineering polynomial features