- What is Deep Learning? (DL)
- NN
	- conceptual
	- forward prop
	- back prop

# Deep Learning
advanced subset of ML
implies:
- computational intensity
- increased power
- fewer theoretical guarantees
- empirical decisions
- non-linear/non-convex

# NN - the Poster Child
input -> hidden -> output
- each node is a neuron
- each edge has a weight

NN is a data-based function approximator
- given large amount of inputs and outputs, a NN can approximate underlying function that creates outputs from inputs
pattern recognizers
- features CAN BE LEARNED - (ex. with a cat: the ears, the whiskers, face)

# Forward Propagation
Data -> input, then ran through initially semi-random weights at each layer
- can use sigmoid function as an activation function
- tanh
- ReLU
- bunch of others

## Soft Max Activation Function
converts output logis (raw final values) into probabilities
- used at output layer
- each output divded by sum of all outputs

Activation functions introduce nonlinearity
- if sigmoid not applied, then all matrix multiplies can just be one
- lose the power of depth

# Back Prop (Gradient Update)
- finding best weight matrices

1. randomly initialized in beginning
2. find individual losses, square them, sum all together (sum of squared errors, can convert to MSE when using a batch to train)
3. Find the gradient, travel in the opposite direction from it -> gradient descent
	1. not necessarily convex
4. back propagate the gradient, updating the weights

**ML**
- theoretical guarantees, local minima
- closed form solutions are possible
- more interpretable than DL
typically on structured data (dataframes)

**DL**
- nonlinearities make loss landscape much worse, no guaranteed global minima
- usually requires GPU
- REALLY powerful models
- model design decisions can seem arbitrary
typically for unstructured data 