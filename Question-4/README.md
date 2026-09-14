# Visualization of Wireless Path-Loss Model

## Overview

This solution provides a clean and self-contained implementation of **Visualization** from the laboratory assignment.

The objective is to visualize the measured wireless path-loss data and compare it with the fitted linear regression model derived from the **Close-In (CI) path-loss model**.

---

## Objective

The main objective is to:

- Load wireless path-loss measurement data.
- Prepare the regression feature.
- Fit a linear regression model.
- Estimate the path-loss relationship.
- Visualize the measured data and fitted path-loss curve.

---

## Model

The Close-In (CI) path-loss model is given by:

$$
PL(d) = FSPL(d_0) + 10n\log_{10}\left(\frac{d}{d_0}\right) + \varepsilon
$$

where:

- $PL(d)$ — measured path loss in dB
- $FSPL(d_0)$ — free-space path loss at reference distance $d_0$
- $n$ — path-loss exponent
- $d$ — transmitter-receiver separation distance
- $d_0$ — reference distance
- $\varepsilon$ — shadowing/random error

The model is rearranged into a linear regression form:

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

---

## Scope

Only the components required for **Visualization** are included:

1. Data loading
2. Synthetic data generation when the dataset is unavailable
3. Feature preparation
4. Linear regression model implementation
5. Model fitting
6. Visualization of measured and predicted path-loss values



---

