# Monte Carlo Pharmacokinetic/Pharmacodynamic (PK/PD) Simulation

> **Author:** Deepika Sarala Pratapa  
> **University of Florida · M.S. in Applied Data Science**  
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

$[
C(t) = \frac{F D k_a}{V (k_a - k)} 
\left(\frac{1 - e^{-k_a t}}{1 - e^{-k_a \tau}} - \frac{1 - e^{-k t}}{1 - e^{-k \tau}}\right)
]$
where  
- $( F )$: Bioavailability (assumed = 1)  
- $( D )$: Dose  
- $( k_a )$: Absorption rate constant  
- $( k = CL/V )$: Elimination rate constant  
- $( τ )$: Dosing interval  

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
bash
# Clone the repository
git clone https://github.com/deepikapratapa/pkpd-montecarlo-simulation.git
cd pkpd-montecarlo-simulation

# Create a clean environment
conda create -n pkpd python=3.12 -y
conda activate pkpd

# Install dependencies
pip install numpy pandas matplotlib scipy streamlit
```
pkpd_montecarlo_project/
│
├── README.md              # Project overview, usage, and interpretation
├── pkpd_monte_carlo.ipynb # Jupyter notebook (simulation + plots)
├── pkpd_report.pdf        # LaTeX report
│
└── 📂 results/
    ├── pkpd_sim_results.csv   # Output data (2000 subjects)
    ├── cmax_hist.png
    ├── auc_hist.png
    ├── ctrough_hist.png
    ├── pctT_MIC_hist.png
    └── profiles_examples.png
```
## ⚙️ Usage
1. Launch the notebook:
   ```bash
   jupyter notebook pkpd_monte_carlo.ipynb
2.	Run all cells to:
	•	Simulate 2000 subjects using Monte Carlo sampling.
	•	Calculate Cmax, AUC₀–τ, Ctrough, and %T>MIC.
	•	Export results to results/pkpd_sim_results.csv.
	•	Generate histograms and example concentration–time profiles.
	3.	All plots and summary statistics will be stored in the results/ directory.

---

### Results Summary

| Metric | Median | 5th Percentile | 95th Percentile |
|:--------|:-------:|:---------------:|:---------------:|
| **Cmax (mg/L)** | 6.78 | 5.22 | 8.79 |
| **AUC₀–τ (mg·h/L)** | 50.25 | 35.15 | 73.57 |
| **Ctrough (mg/L)** | 1.80 | 0.77 | 3.60 |
| **%T>MIC (%)** | 100.00 | 89.47 | 100.00 |

## Key Insights
- Demonstrates realistic **inter-patient variability** in drug exposure.  
- Over **90% of simulated subjects** achieved target %T>MIC, indicating strong therapeutic coverage.  
- Observed spread in AUC and trough levels reflects **population diversity** in clearance and volume.  
- Monte Carlo sampling provides a reproducible approach for **dose–response uncertainty analysis**.

## Visualizations
All generated figures are saved in the `results/` folder.

| Figure | Description |
|:-------|:-------------|
| `cmax_hist.png` | Distribution of Cmax |
| `auc_hist.png` | Distribution of AUC₀–τ |
| `ctrough_hist.png` | Distribution of Ctrough |
| `pctT_MIC_hist.png` | Distribution of %T>MIC |
| `profiles_examples.png` | Representative concentration–time profiles |

## Interpretation
Monte Carlo simulations capture **stochastic biological variability** in a virtual population.  
Results demonstrate consistent exposure above the MIC threshold, suggesting effective pharmacodynamic coverage.  
Such simulations are integral to **model-informed drug development (MIDD)**, enabling dose justification and population-level risk evaluation.

## References
1. Gabrielsson J. & Weiner D. (2016). *Pharmacokinetic and Pharmacodynamic Data Analysis: Concepts and Applications.* CRC Press.  
2. Mouton J.W. et al. (2005). *Time over MIC as a predictor of β-lactam efficacy.* *Clinical Pharmacokinetics.*  
3. Ette E.I. & Williams P.J. (2007). *Pharmacometrics: The Science of Quantitative Pharmacology.* Wiley-Interscience.

## Future Work
- Extend to **two-compartment** or **nonlinear PK models**.  
- Incorporate **covariates** (weight, renal function) for population heterogeneity.  
- Add **bootstrap resampling** for uncertainty quantification.  
- Build a **Streamlit dashboard** for interactive visualization.  
- Validate model with **real-world clinical PK datasets**.

##  Author
**Deepika Sarala Pratapa**  
M.S. Applied Data Science, University of Florida  
 [deepikapratapa27@gmail.com](mailto:deepikapratapa27@gmail.com)  
