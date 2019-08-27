# Activation Functions
This is the short overview of the most popular activation functions used both in the hidden and the output layers.

General form of the layer equation:
$$
\pmb h = g(\pmb{W}^\top x + \pmb b)
$$

$$
\pmb z = \pmb{W}^\top x + \pmb b
$$


## Linear Unit
Skips the activation function and use only the affine transformation.  
Form:
$$
\pmb h =\pmb  z
$$

Hints:
* It can be used to reduce parameters number in the network by replacing one affine transformation with two.  
  For details see [paragraph 6.3.3 in this book](https://www.deeplearningbook.org/contents/mlp.html).
* It does not increase the network capacity.
* Can work well in the output layer.



## Rectified Linear Unit (ReLU)
Most popular and universal activation function.  
It has the following form:
$$
g(\pmb{z})_i = \text{max}(0, z_i) 
$$

Hints:  
* When initializing the parameters of the affine transformation, it can be a good practice to set all elements of **_b_** to a small positive elements, such as 0.1.
* One drawback of ReLU is that it cannot learn on examples for which their activation is zero.



There are three generalizations of ReLU and all of them share the general form:
$$
g(\pmb{z})_i = \text{max}(0, z_i) + \alpha\ \text{min}(0, z_i)
$$
They are:
1. __Absolute value rectification__  
  It fixes $\alpha$ to -1 making the activiation function to be $g(\pmb{z})_i=|z_i|$
2. __Leaky ReLU__  
  Fixes $\alpha$ to some small value like $0.01$
3. __Parametric ReLU (PReLU)__  
  Makes $\alpha$ a learnable parameter


## Logistic Sigmoid and Hyperbolic Tangent
Sigmoid function:
$$ 
g(\pmb{z})_i = \sigma(z_i) = \frac{e^{z_i}}{1 + {e^z_i}} = \frac{1}{1 + e^{-z_i}}
$$


Hyperbolic Tangent
$$ 
g(\pmb{z})_i = \text{tanh}(z_i) = \frac{e^{z_i} - e^{-z_i}}{e^{z_i} + e^{-z_i}} = \frac{e^{2z_i} - 1}{e^{2z_i} + 1}
$$

They are closely related beacuse:
$$
\text{tanh}(z) = 2\sigma(2z) - 1 
$$

Hints:  
* The widespread saturation of sigmoidal units can make gradient-based learning very difficult. For this reason, their use as hidden units in feedforward neural networks is now discouraged.
* They need appropriate loss function in case of using them as a output layer.
* Hyperbolic tangent typically performs better (it is more close to linear function for small activations).
* Sigmoidal activation functions are more common in settings other than feedforward networks.

## Softmax
One of the most popular activation functions for the output layer in the multiclass classficication problems.  
Has the following form:  
$$
\text{softmax}(\pmb z)_i  = \frac{\text{exp}(z_i)}{\sum_j{\text{exp}(z_j)}}
$$

Hints:
* Because its gradinet saturates for components much lesser than the $\text{argmax}(\pmb z)$, it should not be used with cost functions without the $\text{log}$ function to compensate the $\text{exp}$ function.
* It can be used in a hidden layer for encoding some signals inside the network.
 

## Less common activation functions
Short description of less popular activation functions:
1. __Radial basis function (RBF)__  
  Form:
  $$
  h(\pmb{x})_i = \text{exp}(- \frac{1}{\sigma_i^2}||\pmb{W}_{:,i} - \pmb{x}||^2)
  $$
  It is more active when $\pmb{x}$ approaches the template $\pmb{W}_{:,i}$.  
  Because it saturates to 0 for most $\pmb{x}$, it can be difficult to optimize.
1. __Hard tanh__  
  Form:
  $$
  g(\pmb z)_i = \text{log}(1+e^{z_i})
  $$




Credits:
1. _Deep Learning_, I. Goodfellow, Y. Bengio, A. Courville, MIT Press 2016