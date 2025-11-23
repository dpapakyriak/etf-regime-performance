# Multi Asset ETF Market Regime Detection

This project presents a complete quantitative workflow for identifying market regimes within a diverse set of global exchange traded funds. The goal is to understand how different asset classes behave across distinct market environments using unsupervised learning techniques.  
The analysis is built using a unique dataset sourced from Bloomberg which contains high quality historical prices and net asset values for 27 ETFs covering major asset classes.

The project is exploratory by design and serves as a foundation for more advanced work such as regime driven portfolio construction, reinforcement learning based allocation models, and macro risk monitoring systems I plan doing and publishing.

---

## Project Scope

The notebook follows a clear research oriented structure designed for both interpretability and practical relevance.

### 1. Data Import and Preparation  
The dataset contains 27 ETFs across equities, bonds, commodities, credit, and global exposures.  
Each ETF includes daily historical prices and net asset values.  
The dataset originates from the Bloomberg Terminal and is structured into separate sheets, one per ETF.  
After import, all series are aligned on a common date index.

### 2. Feature Engineering  
To capture market structure and asset behavior we compute a set of cross asset features including:

• daily returns  
• twenty day realized volatility  
• twenty day momentum, defined as twenty day return  
• rolling drawdown depth  
• NAV premium, defined as (price minus NAV) divided by NAV  
• premium volatility  
• rolling correlations across representative ETF pairs  
• principal components of the full feature matrix  


### 3. Dimensionality Reduction  
Given the size of the feature matrix, Principal Component Analysis is applied to reduce dimensionality and stabilize clustering.  
The first several components aim to capture the primary macro drivers, such as global risk appetite, duration sensitivity, and commodity influence.

### 4. Market Regime Detection with K Means  
K Means clustering is applied to the PCA reduced feature set to discover natural market states without relying on prior labels.  
Each day in the dataset is assigned a regime label.  
These regimes represent environments in the markets which a further analysis could label accordingly, such as risk on, risk off, and commodity or inflation driven conditions (not in the scope of this project, I mainly focus on identifying that different regimes exist and observing assets performance in these regimes).

### 5. Asset Behavior Across Regimes  
For each ETF and each regime we compute:  
• average daily return  
• twenty day volatility  
• regime specific profile plots  
• cross asset comparisons  
• radar charts visualizing the performance signature of every ETF  

This part of the notebook highlights how global assets respond differently to market conditions.  

### 6. Visualization  
A comprehensive visualization section includes:  
• bar charts comparing regimes  
• a large grid of radar charts showing regime profiles for every ETF  
• time series of regime labels  


### 7. Conclusions  
The notebook provides a complete pipeline for regime discovery and cross asset interpretation.  
It serves as a foundation toward future work such as regime switching strategies, machine learning based return forecasting, or reinforcement learning for dynamic portfolio allocation.

---

## The Dataset

The dataset used in this project was exported directly from the Bloomberg Terminal.  
It is an exceptionally rich data source containing:

• 27 ETFs  
• daily prices  
• daily net asset values  
• broad representation of global asset classes including  
  equities, bonds, commodities, credit, inflation hedges, factors, and international markets  

Each ETF is stored as a separate sheet within the provided Excel file.  

---

## How to Cite This Project

If you use ideas, code, visualizations, or results from this repository, please cite it as follows:

**APA Style**  
Papakyriakopoulos Dimitrios. (2025). *Market Regime Detection in a Multi Asset ETF Universe.* GitHub Repository.  

**BibTeX**  
@misc{dpapakyriak2025regimes,
  title  = {Market Regime Detection in a Multi Asset ETF Universe},
  author = {Dimitrios Papakyriakopoulos},
  year   = {2025},
  note   = {GitHub Repository},
  url    = {https://github.com/dapakyriak/etf-regime-performance}
}

**General Citation**  
Papakyriakopoulos, Dimitrios (2025). Market Regime Detection in a Multi Asset ETF Universe. Available on GitHub.


