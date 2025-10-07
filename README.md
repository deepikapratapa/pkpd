# Monte Carlo Pharmacokinetic/Pharmacodynamic (PK/PD) Simulation

> **Author:** Deepika Sarala Pratapa  
> **University of Florida · M.S. in Applied Data Science (Bioinformatics Specialization)**  
> **Project Type:** Pharmacometric Modeling & Simulation  
> **Language:** Python (NumPy · Pandas · Matplotlib · Streamlit)  

---

## Overview
This project implements a **Monte Carlo simulation** of a one-compartment pharmacokinetic (PK) model with first-order absorption to explore population variability in exposure and probability of target attainment (PTA).  
It simulates **2000 virtual subjects**, randomly sampling inter-individual variability in clearance (CL), volume of distribution (V), and absorption rate constant (kₐ).  
Each subject’s steady-state profile is used to compute:

- **Cmax:** Maximum plasma concentration  
- **AUC₀–τ:** Area under the concentration–time curve per dosing interval  
- **Ctrough:** Minimum concentration before next dose  
- **%T>MIC:** Percent of time above the minimum inhibitory concentration  

This workflow mimics professional pharmacometric analyses used in model-informed drug development and dose optimization.

---

## Objectives
- Quantify **population-level variability** using Monte Carlo methods.  
- Assess **dose adequacy** via PK/PD metrics (Cmax, AUC, Ctrough, %T>MIC).  
- Visualize **distributions and steady-state concentration profiles**.  
- Demonstrate reproducible PK simulation and analysis using open-source Python tools.  

---

## Model Summary
A one-compartment model with first-order absorption and elimination:

\[
C(t) = \frac{F D k_a}{V (k_a - k)} 
\left(\frac{1 - e^{-k_a t}}{1 - e^{-k_a \tau}} - \frac{1 - e^{-k t}}{1 - e^{-k \tau}}\right)
\]
where  
- \( F \): Bioavailability (assumed = 1)  
- \( D \): Dose  
- \( k_a \): Absorption rate constant  
- \( k = CL/V \): Elimination rate constant  
- \( τ \): Dosing interval  

Variability modeled as **log-normal distributions** for CL, V, and kₐ.

---

## Tech Stack
| Category | Tools |
|-----------|-------|
| **Languages** | Python 3.12 |
| **Libraries** | `numpy`, `pandas`, `matplotlib`, `scipy`, `streamlit` |
| **Data Storage** | CSV (pkpd_sim_results.csv) |
| **Visualization** | Matplotlib histograms, Streamlit dashboard |
| **Reproducibility** | Jupyter Notebook, GitHub repository |

---

## Installation
```bash
# Clone the repository
git clone https://github.com/deepikapratapa/pkpd-montecarlo-simulation.git
cd pkpd-montecarlo-simulation

# Create a clean environment
conda create -n pkpd python=3.12 -y
conda activate pkpd

# Install dependencies
pip install numpy pandas matplotlib scipy streamlit
