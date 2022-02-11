# Simple-ANN
Shape Reference
Here is a quick shape reference to not get confused with shapes later. 

•	neurons = number of neurons in the given layer

•	inputs = number of inputs to the layer

•	samples (or m) = number of training samples

•	Input to the network, X_train.shape = (dimension of X, samples)

•	W.shape = (neurons, inputs)

•	b.shape = (neurons, 1)

•	Z.shape = (neurons, samples)

•	A.shape = Z.shape

•	dZ.shape = Z.shape

•	dW.shape = W.shape

•	db.shape = b.shape

•	dA.shape = A.shape

## The Feedforward Function

The feedforward function propagates the inputs through each layer of the network until it reaches the output layer and produces some output. Every neuron takes in inputs, multiplies it by the weights, adds a bias and applies an activation function to generate its output.

•	The 𝐴_prev term is the output from the previous layer. For our input layer, this will be equal to our input value X.

•	The operation between W and A_prev is a dot operation. Since both are matrices, it is important that their shapes match up (the number of columns in W should be equal to the number of rows in A_prev). This is a fundamental property of matrix multiplications.

•	The output of this layer is A_prev. In the case of the output layer, this will be equal to the predicted output, Y_bar.

## Gradient Descent

Gradient descent is what makes our network learn. Gradient descent is based on the fact that, at the minimum value of a function, its partial derivative will be equal to zero. Here we are interested in minimizing the Cost function.

Cost depends on the weights and bias values in our layers. So, for each layer, we find the derivative of cost with respect to weights and biases for that layer. This derivative value is the update that we make to our current values of weights and biases. The equation used to make this update is called the learning equation.

## The Backpropagation Algorithm

The backpropagation algorithm is basically going back in our network, calculating the value of partial derivative values in each layer and applying the learning equation.
After we get the output, we will calculate the cost.

### Things to note in these equations:
The value of dC/dA is given, ie in code, returned from the previous layer. In case of the output layer, this is a direct calculation since the cost is a function of A, and the output Ybar = A.

d_act is the derivative of the activation function used in that particular layer.

A_prev is the same A_prev we discussed in the Feedforward section. We find its transpose to match shape with dC/dZ. Also remember that the derivatives of a variable, say Z has the same shape as Z.

Finally, we calculate dC/dA_prev to return to the next layer.

In code we ignore the dC term and simply use the denominator to denote the variables, since all variables have the numerator dC. So, for example, in code, the variable dA actually means the value dC/dA.

## Training the Network
### Things to note:

•	m is the number of samples. epochs are the number of iterations we will run this.

•	We perform feedforward, by iterating through each layer and passing the value from the previous layer as input to the next layer.

•	Calculating the cost is optional, here we do it only to plot the graph.

•	For backpropagation, we iterate through the layers backwards, using the reversed() function in the for loop. The value of dA is calculated and passed on to the next layer.

•	Finally, after the loop runs for all the epochs, our network should be trained, ie, all the weights and biases should be tuned. Now we can make predictions using the same feedforward logic we used while training.
