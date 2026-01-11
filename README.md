# Extended Newsvendor Optimization Model
Extended Newsvendor model with price–demand optimization and bootstrap analysis.
This project extends the classic Newsvendor Model by incorporating:
- Rush production costs
- Disposal costs for overproduction
- A price–demand relationship estimated from historical data

The goal is to jointly optimize **price** and **production quantity** to maximize expected profit under uncertainty.

This was completed as part of *Optimization I – Project 3 (Nonlinear Programming)* at UT Austin.

## Contributors
- Jack Feen  
- Mihir Jeshurun Gandham  
- Radha Pawar  
- Ishrak Wasif Udoy  

---

## Problem Overview

In the standard newsvendor model, only the production quantity is optimized.  
This project extends that framework by:

1. Adding operational realism:
   - Rush printing cost (g)
   - Disposal cost for unsold inventory (t)

2. Modeling demand as a function of price:
   \[
   D = \beta_0 + \beta_1 p + \epsilon
   \]

3. Jointly optimizing:
   - Price \(p\)
   - Quantity \(q\)

4. Using:
   - Linear Programming (LP) for fixed price
   - Quadratic Programming / QCP for joint price–quantity optimization
   - Bootstrap simulation to assess robustness

---

## Files

- `Opti_Project3.ipynb` – Full analysis and optimization pipeline  
- `price_demand_data.csv` – Historical price–demand data  
- `README.md` – Project overview  

---

## Key Steps in the Notebook

1. Fit a linear regression: Demand ~ Price  
2. Use residuals to simulate demand at fixed price \(p = 1\)  
3. Solve extended newsvendor LP to find optimal quantity  
4. Formulate and solve joint price–quantity optimization (QCP/QP)  
5. Run bootstrap simulations:
   - Refit regression
   - Re-optimize \(p^*\) and \(q^*\)
   - Build empirical distributions
6. Compare:
   - Standard Newsvendor model
   - Extended model with price sensitivity and operational costs

---

## Results (from report)

- Optimal price: ≈ **0.95**
- Optimal quantity: ≈ **535 units**
- Extended model improves mean profit by **~35%**
- Outperforms the standard NV model in **100%** of bootstrap samples
- Produces **higher and more stable** profit distributions

---

## How to Run

1. Open `Opti_Project3.ipynb`
2. Ensure you have:
   - `numpy`
   - `pandas`
   - `matplotlib`
   - `scikit-learn`
   - `gurobipy` (or modify to use scipy if needed)
3. Run cells top-to-bottom

The notebook is fully self-contained and reproduces all results.

---

## Why This Matters

This project demonstrates how:
- Optimization models improve when aligned with real operational constraints
- Pricing and production decisions must be made jointly
- Bootstrap analysis reveals the stability and risk of optimal policies

It bridges **optimization theory**, **econometrics**, and **simulation** into a production-ready decision framework.

