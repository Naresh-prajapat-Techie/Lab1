## Objective

Estimate the free-space path loss at the reference distance, $\mathrm{FSPL}(d_0)$, and the path-loss exponent $n$ jointly using linear regression.

## Methods Implemented

The following three fitting methods are implemented:

1. Closed-form solution
2. Batch Gradient Descent
3. Stochastic Gradient Descent (SGD)

## Model

We rearrange the Close-In (CI) path-loss model into a linear regression form:

$$
y = \mathrm{FSPL}(d_0) + 10n\log_{10}(d/d_0) + \varepsilon
$$

where the measured path loss $y$ is the target and

$$
x = \log_{10}(d/d_0)
$$

is the regression feature.

Thus, the model can be written as:

$$
\hat y = \theta_0 + \theta_1 x
$$

where $\theta_0 = \mathrm{FSPL}(d_0)$ and $\theta_1 = 10n$.

All three methods fit the same linear model using the same design matrix

$$
\Phi = [\mathbf{1}, x].
$$

Therefore, after convergence, the iterative methods should produce results that closely agree with the closed-form solution.

## Learning Rate Selection

Since the feature $x = \log_{10}(d/d_0)$ lies approximately in the range $[1, 3.3]$, explicit feature scaling is not necessary and gradient descent remains well-behaved.

A quick learning-rate sweep was performed to identify a value that provides fast and stable convergence. Learning rates of $\mathrm{lr} \geq 0.2$ caused divergence, while smaller learning rates converged more slowly. A learning rate of $\mathrm{lr}=0.05$ provided a good balance between convergence speed and stability.

Therefore, $\mathrm{lr}=0.05$ and $\mathrm{epochs}=1500$ were used for both Batch Gradient Descent and SGD.

## Training Loss vs. Epochs

The training loss of both iterative methods is plotted against the number of epochs using a logarithmic y-axis.

Batch Gradient Descent decreases smoothly and monotonically because every parameter update is calculated using the gradient over the complete dataset.

In contrast, SGD produces a noisier loss curve because each parameter update is based on a single randomly selected training sample. Individual updates may temporarily increase the loss, although the overall trend moves toward the optimum.

Both iterative methods eventually converge to approximately the same final MSE obtained by the closed-form solution.

## Result

The three methods successfully estimate the intercept $\mathrm{FSPL}(d_0)$ and the slope $10n$. The path-loss exponent is then obtained as

$$
n = \frac{\theta_1}{10}.
$$

The Batch GD and SGD solutions converge toward the closed-form solution, confirming that all three approaches correctly minimize the same convex least-squares objective.
