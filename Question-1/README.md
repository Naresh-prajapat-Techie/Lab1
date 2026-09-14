
## Objective

Implement simple linear regression from scratch using NumPy.

## Methods Implemented

The following three fitting methods are implemented:

1. Closed-form solution
2. Batch Gradient Descent
3. Stochastic Gradient Descent (SGD)

## Model

We implement simple linear regression $\hat y = \theta_0 + \theta_1 x$ with three interchangeable
fitting methods, selected via a single `method` argument: `'closed_form'`, `'batch_gd'`, `'sgd'`.
All three fit the *same* model on the *same* design matrix $\Phi = [\mathbf{1}, x]$, so their
results should agree once the iterative methods have converged -- that agreement is itself a useful
check of correctness.
## Files

* `Question-1.ipynb` — Complete implementation, experiments, and results.

## Libraries Used

* NumPy
* Pandas
* Matplotlib
* SciPy

## Result

The notebook compares the three regression methods and verifies that the iterative methods converge toward the closed-form solution.
