# Biostatistics Computational Lab – CNV and GC-Bias Modeling

This repository documents my semester-long work in the Biostatistics Laboratory course, focusing on statistical modeling of genomic coverage, GC-content bias correction, and simulation-based validation.  
The project gradually builds a full CNV (Copy Number Variation) analysis pipeline using real and simulated sequencing data.

---

### **Week 1 – Data Exploration and Mapping**
The lab began with processing raw sequencing reads into genomic bins and mapping them to reference regions.  
I explored variability in coverage and examined GC-content bias patterns using descriptive statistics and visual tools.  
This stage built the foundation for understanding systematic bias in sequencing data.

---

### **Week 2 – Statistical Modeling of GC Bias**
I developed regression models to describe the relationship between read coverage and GC content.  
Both **Weighted Least Squares (WLS)** and **Cubic Spline regression** were fitted to estimate the smooth function *f(GC)* representing expected coverage as a function of GC content.  
This established the baseline for normalization and later CNV detection.

---

### **Week 5 – Model Comparison and Residual Analysis**
This lab focused on comparing performance across different bin resolutions (1K, 2.5K, 5K, and 10K).  
I evaluated bias–variance trade-offs using **MAE**, **Median Absolute Error**, and visual residual analysis.  
Models included **LOESS** and **Cubic Spline** corrections. The results guided the choice of optimal bin size for robust CNV detection.

---

### **Week 6 – Model Refinement and Simulation Design**
This stage bridged empirical modeling and theoretical simulation.  
I refined the spline-based correction model and introduced **Poisson regression**, modeling coverage as  
$$Y_k \sim \text{Poisson}(\Lambda_k), \quad \Lambda_k = f(GC_k) + \varepsilon_k.$$  
Different estimation strategies were explored — **MLE**, **Method of Moments**, and **MAD** — for the variance parameter $σ^2$.  
The analysis also examined **UnderSpread** and **OverSpread** behavior using **Cubic** vs. **Natural Splines**, forming the basis for the later simulation study.

---

### **Week 7 – Data Cleaning and Copy Number Estimation**
Using the cleaned coverage data (2.5K-bin resolution), I applied spline-based correction to compute copy number estimates (*aᵢ*).  
Outlier filtering via **LOESS residuals** and **IQR trimming** improved the normalization process.  
The resulting *aᵢ* distribution confirmed diploid coverage near 1 and identified local CNV deviations.

---

### **Week 8 – Simulation and Model Validation**
The final lab implemented a **Poisson-based simulation framework** to mimic GC-dependent sequencing bias.  
I estimated the Poisson variance parameter (*σ*), generated synthetic datasets with realistic coverage variability, and compared them to observed data using **RMSE** between fitted and true *f(GC)* curves.  
This simulation validated the reliability and interpretability of the modeling approach.

---

### **Summary**
Across all stages, I integrated statistical reasoning, computational modeling, and visualization in **R** to analyze and correct sequencing coverage data.  
Each lab reflected a deeper layer of insight — from exploratory analysis to model fitting, correction, and simulation — culminating in a reproducible CNV detection pipeline grounded in sound biostatistical principles.

---

*Created by Eden Malka, 2025*
