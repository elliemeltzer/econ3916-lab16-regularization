# Regularization: Buying Bias to Sell Variance

## Objective

I examined how LASSO and Ridge reduce prediction error in a model with many predictors and limited useful signal.

## Methodology

- I simulated a dataset with 200 predictors, 105 training observations, and only 5 predictors with real effects.
- I compared OLS, LASSO, and Ridge using training and test mean squared error.
- I traced the LASSO coefficient path as the penalty changed.
- I selected a LASSO penalty using 5-fold cross-validation with scaling performed separately inside every fold.
- I compared the variables selected by LASSO with the known true predictors.
- I examined how LASSO and Ridge handled two nearly identical predictors.
- I prompted an AI to write the cross-validation loop and checked its results against my own calculations.

## Key Findings

OLS had a test MSE of **12.9587**, while Ridge reduced it to **10.1128** and LASSO reduced it to **1.4219**. LASSO performed best because the simulated design contained only a small number of useful predictors.

All five true predictors entered the LASSO path by step **6**, while the first noise variable entered at step **17**. Five-fold cross-validation selected a penalty of **0.1995**, with a CV MSE of **1.5502**.

LASSO found **5 of 5** true predictors but also selected **11** false positives. This showed that strong prediction performance did not mean its selected-variable list was perfect.

When two predictors were nearly identical, LASSO placed **4.462** on one and zero on the other. Ridge divided the weight between them, assigning **1.618** and **1.609**.

I used **2 rounds** of prompting for the cross-validation function. In the final check, its selected penalties and CV errors matched my results for both penalty grids, with every comparison differing by **0%**.
