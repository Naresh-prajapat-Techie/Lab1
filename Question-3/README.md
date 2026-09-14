# Problem 3 — Estimate Shadowing Variance

## Overview

This solution provides a clean and self-contained implementation of **Problem 3: Estimate Shadowing Variance** from the laboratory assignment.

The objective is to estimate the **shadowing standard deviation** from the residuals obtained using three different linear regression fitting methods.

The three methods considered are:

1. Closed-form Linear Regression
2. Batch Gradient Descent
3. Stochastic Gradient Descent (SGD)

---

## Objective

The main objective is to:

- Fit the Close-In (CI) path-loss model using three regression methods.
- Calculate the residuals between measured and predicted path-loss values.
- Estimate the shadowing variance from the residuals.
- Compute the corresponding shadowing standard deviation.
- Compare the estimated parameters obtained from all three methods.

---

## Regression Model

The Close-In (CI) path-loss model is expressed as:

$$
PL(d) = FSPL(d_0) + 10n\log_{10}\left(\frac{d}{d_0}\right) + \varepsilon
$$

where:

- $PL(d)$ — measured path loss in dB
- $FSPL(d_0)$ — free-space path loss at reference distance $d_0$
- $n$ — path-loss exponent
- $d$ — transmitter-receiver separation distance
- $d_0$ — reference distance
- $\varepsilon$ — shadowing error

The model is written as a linear regression problem:

$$
y = \theta_0 + \theta_1x + \varepsilon
$$

where:

$$
x = \log_{10}\left(\frac{d}{d_0}\right)
$$

and:

$$
\theta_0 = FSPL(d_0), \qquad \theta_1 = 10n
$$

The path-loss exponent is obtained from the fitted slope as:

$$
n = \frac{\theta_1}{10}
$$

---

## Shadowing Variance Estimation

After fitting the regression model, the residual for each measurement is calculated as:

$$
\varepsilon_i = y_i - \hat{y}_i
$$

The estimated shadowing variance is calculated using:

$$
\hat{\sigma}^2 =
\frac{1}{N}
\sum_{i=1}^{N}\varepsilon_i^2
$$

The corresponding shadowing standard deviation is:

$$
\hat{\sigma} =
\sqrt{
\frac{1}{N}
\sum_{i=1}^{N}\varepsilon_i^2
}
$$

where:

- $N$ — number of measurements
- $\varepsilon_i$ — residual for the $i$-th measurement
- $\hat{\sigma}^2$ — estimated shadowing variance
- $\hat{\sigma}$ — estimated shadowing standard deviation

---

## Methods Implemented

### 1. Closed-form Linear Regression

The closed-form solution directly calculates the optimal regression parameters by minimizing the least-squares error.

This provides the reference solution against which the iterative methods can be compared.

### 2. Batch Gradient Descent

Batch Gradient Descent updates the model parameters using the gradient calculated over the complete dataset at every iteration.

### 3. Stochastic Gradient Descent

Stochastic Gradient Descent updates the parameters using individual samples, resulting in faster but potentially noisier convergence.

Since all three methods minimize the same least-squares objective, their fitted parameters and residual statistics should be approximately identical after convergence.

---
