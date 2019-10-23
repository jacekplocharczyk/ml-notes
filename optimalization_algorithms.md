# Optimalization algorithms

Typical cost function:

$$
J(\theta) = \mathop{\mathbb{E}}\ _{x, y	\sim  \hat p_{data}} L(f(\pmb{x}; \pmb{\theta}), y)
$$

where $L$ is per-example loss function and $\hat p_{data}$ is the empirical distribution.
 
## Empirical Risk Minimization
Cost function over the real distribution called $p_{data}$ is known as the **risk**. Because we don't have an access to the uderling true distribution we can minimize the **empirical risk**:

$$
\mathop{\mathbb{E}}\ _{x, y	\sim  \hat p_{data}} L(f(\pmb{x}; \pmb{\theta}), y) = \frac{1}{m}\sum^m_{i=1} L(f(\pmb{x}^{(i)}; \pmb{\theta}), y^{(i)})
$$

> Training process based on minimizing this average training error is known as **empirical risk minimization**.

Hints:
* The most basic concept - train using all available samples.
* It is prone to overfitting.
* Not feasible for deep learning.

## Batch and Minibatch Algorithms

Confusingly optimization algorithms that use the entire training set are called **batch** or **deterministic** gradient methods.  
Whereas most often word **batch** reffers to to describe minibatch used in stochastic gradient descent.

> Most algorithms used for deep learning are using more tha one but fewer than all the training examples. These were traditionally called minibatch or minibatch stochastic methods, and it is now common to call them simply stochastic methods.

> Minibatch sizes are generally driven by the following factors
> * Larger batches probide a more accurate estimate of the gradient, but with less than linear returns.
> * Multicore architectures are usually underutilized by extremely small batches. This motivates using some absolute minimum batch size, below which there is no reduction it the time to process a minibatch.
> * If all examples in the batch are to be processed in parallel, then the amount of memory scales with the batch size. For many hardware setups this is the limiting factor in batch size.
> * Some kindes of hardware architecture achieve better runtime with specific sizes of arrays. Especially when using GPUs, it is common for power of 2 batch sizes to offer better runtime. Typical power of 2 batch sizes range from 32 to 256, with 16 sometimes being attempted for large models.
> * Small batches can offer a regularizing effect, perhaps due to the noise they add to the learning process. Generalization error is often best for a batch size of 1. Training with such small batch size might require a small learning rate to maintain stability because of the high vaiance and its total runtime can be very high too.

Hints:
* For first-order methods batch size ca. 100 should be OK.
* For second-order methods batch size should be bigger, ca. 10000.


## Ill conditioning
If even very small gradient step increases the cost function we are dealing with ill-conditioning of the Hessian matrix.

> To determine whether ill-conditioning is detrimental to a neural network training task, one can monitor the squred gradient norm $\pmb{g}^\text{T}\pmb{g}$ and the $\pmb{g}^\text{T}\pmb{H}\pmb{g}$ term.
> In many, cases, the gradient norm does not shrink significantly throughout learning, but the $\pmb{g}^\text{T}\pmb{H}\pmb{g}$ term grows by more than an order of magnitude.

## Basic Algorithms














Credits:
1. _Deep Learning_, I. Goodfellow, Y. Bengio, A. Courville, MIT Press 2016