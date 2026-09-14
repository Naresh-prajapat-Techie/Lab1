Visualization of Wireless Path-Loss Model

Overview

This deliverable contains a clean and self-contained implementation of Problem 4: Visualization from the laboratory assignment.

The objective is to visualize measured path-loss data and compare it against the fitted linear regression model derived from the Close-In (CI) path-loss formulation.

Scope

Only the components required for Problem 4 have been retained:

Data loading (or synthetic data generation when the dataset is unavailable)

Feature preparation

Linear regression model implementation

Model fitting

Visualization of measured and predicted path-loss values

The following items were intentionally removed because they are not required for Problem 4:

Learning-rate experiments

Gradient Descent implementation

Stochastic Gradient Descent implementation

Loss-history analysis

Shadowing variance estimation (Problem 3)

Notebook-specific outputs and exploratory code

Input Data

The script searches for:

pathloss.txt

Required Packages

pip install numpy matplotlib

Execution

Run the program using:

python Question-4-Clean.py

Output

The program generates a visualization containing:

Measured path-loss samples

Regression-based fitted path-loss curve

This plot provides a visual assessment of how effectively the regression model captures the propagation trend present in the dataset.