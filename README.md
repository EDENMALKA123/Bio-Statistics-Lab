# Biostatistics Computational Lab – CNV and GC-Bias Modeling

This repository documents our semester-long work in the Biostatistics Laboratory course, focusing on statistical modeling of genomic coverage, GC-content bias correction, and simulation-based validation.  
The project gradually builds a full CNV (Copy Number Variation) analysis pipeline using real and simulated sequencing data.

---

### **Week 1 – Data Exploration and Mapping**
We began by processing raw sequencing reads into genomic bins and mapping them to reference regions.  
We explored variability in coverage and examined GC-content bias patterns using descriptive statistics and visual tools.  
This stage built the foundation for understanding systematic bias in sequencing data.

---

### **Week 2 – Statistical Modeling of GC Bias**
We developed regression models to describe the relationship between read coverage and GC content.  
Both **Weighted Least Squares (WLS)** and **Cubic Spline regression** were fitted to estimate the smooth function *f(GC)* representing expected coverage as a function of GC content.  
This established the baseline for normalization and later CNV detection.

---

### **Week 5 – Model Comparison and Residual Analysis**
This lab focused on comparing performance across different bin resolutions (1K, 2.5K, 5K, and 10K).  
We evaluated bias–variance trade-offs using **MAE**, **Median Absolute Error**, and residual analysis.  
Models included **LOESS** and **Cubic Spline** corrections. The results guided the choice of optimal bin size for robust CNV detection.

---

### **Week 6 – Model Refinement and Simulation Design**
This stage bridged empirical modeling and theoretical simulation.  
We refined the spline-based correction model and introduced **Poisson regression**, modeling coverage as  
$$Y_k \sim \text{Poisson}(\Lambda_k), \quad \Lambda_k = f(GC_k) + \varepsilon_k.$$  
Different estimation strategies were explored — **MLE**, **Method of Moments**, and **MAD** — for the variance parameter $σ^2$.  
The analysis also examined **UnderSpread** and **OverSpread** behavior using **Cubic** vs. **Natural Splines**, forming the basis for the later simulation study.

---

### **Week 7 – Data Cleaning and Copy Number Estimation**
Using the cleaned coverage data (2.5K-bin resolution), we applied spline-based correction to compute copy number estimates (*aᵢ*).  
Outlier filtering via **LOESS residuals** and **IQR trimming** improved normalization accuracy.  
The resulting *aᵢ* distribution confirmed diploid coverage near 1 and identified local CNV deviations.

---

### **Week 8 – Simulation and Model Validation**
The final lab implemented a **Poisson-based simulation framework** to mimic GC-dependent sequencing bias.  
We estimated the Poisson variance parameter (*σ*), generated synthetic datasets with realistic coverage variability, and compared them to observed data using **RMSE** between fitted and true *f(GC)* curves.  
This simulation validated the reliability and interpretability of the modeling approach.

---

### **Final Presentation – Comprehensive CNV Analysis**
The final presentation summarized the complete CNV detection pipeline developed throughout the semester.  
We compared the performance of **Model B, Model C, and Model D**, each representing a variation in GC-correction and residual filtering using **LOESS** and **Cubic Spline** functions.  
Key evaluation criteria included the proportion of bins retained after IQR-based outlier filtering, **Mean Absolute Error**, and the stability of coverage across genomic regions (e.g., 26.5M–28.5M).  
The analysis demonstrated that combining GC correction with adaptive smoothing (Spline + LOESS) provided the most consistent and biologically interpretable results.  
This final stage integrated all prior modeling, simulation, and correction steps into a cohesive and validated CNV detection workflow.

---

### **Summary**
Across all stages, we integrated statistical reasoning, computational modeling, and visualization in **R** to analyze and correct sequencing coverage data.  
Each lab reflected a deeper layer of insight — from exploratory analysis to model fitting, correction, and simulation — culminating in a reproducible CNV detection pipeline grounded in sound biostatistical principles.

---

*Created by Eden Malka, Salome Baranes, and Omer Abuhatzira – 2025*
