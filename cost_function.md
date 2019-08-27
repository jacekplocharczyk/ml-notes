# Cost functions
Overview of the popular cost functions used in deep learning.


## Mean Squared Error (MSE) / L2 Loss


$$
J(\theta) = \frac{\sum_{i=1}^n (y_i -\hat y_i)^2}{n}
$$


## Mean Absolute Error (MAE) / L1 Loss


$$
J(\theta) = \frac{\sum_{i=1}^n |y_i -\hat y_i|}{n}
$$





## Maximum Likelihood (Cross-Entropy)


$$
J(\theta) = - \mathop{\mathbb{E}}\ _{x, y	\sim  \hat p_{data}} \text{log} \ p_{\text{model}}(y | x)
$$

Or oversimplified version for multiclass classification for signle training sample:
$$
J(\theta) = - \sum_{c=1}^C p(y=c | x)_{data} \cdot \text{log}\ p(y=c | x)_{model}
$$
Where $C$ is the number of classes.
