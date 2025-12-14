# Machine Learning Reanalysis of AKI Proteomics Data

A comparative analysis demonstrating how machine learning methods complement traditional statistical approaches in proteomics biomarker discovery.

## Project Overview

This project reanalyzes LC-MS/MS proteomics data from an acute kidney injury (AKI) study, comparing traditional univariate statistical methods with complementary machine learning approaches (PCA and LASSO regression).

**Key Finding:** ML methods identified 22 additional biomarker candidates with substantial fold changes (up to 2.17x) that were missed by traditional statistical analysis due to limited statistical power (n=3 samples per group).

## Dataset

- **Source:** LC-MS/MS proteomics analysis of AKI samples
- **Samples:** 6 total (n=3 AKI+Treatment, n=3 AKI Control)
- **Proteins:** 2,561 quantified proteins after quality filtering
- **Design:** Treatment vs control comparison

## Methods Compared

### 1. Traditional Statistical Analysis
- Shapiro-Wilk normality testing
- Mann-Whitney U test / t-test for differential expression
- Benjamini-Hochberg FDR correction (q < 0.05)
- Effect size filtering (|log2 FC| > 0.5)
- **Result:** 53 significant proteins

### 2. Principal Component Analysis (PCA)
- Unsupervised dimensionality reduction
- Identifies variance-driving proteins regardless of group labels
- **Result:** Top 20 proteins by PC1 loading magnitude

### 3. LASSO Regularized Regression
- Supervised feature selection with L1 regularization
- Identifies minimal predictive protein set
- Cross-validation for optimal regularization strength
- **Result:** 10 predictive proteins

## Key Results

| Finding | Description |
|---------|-------------|
| **Validation** | LASSO confirmed 8/20 top traditional proteins (40% overlap) |
| **Novel Candidates** | 22 proteins identified by ML but not in traditional top 20 |
| **Complementarity** | Zero overlap between PCA and LASSO selections |
| **Value of ML** | ML captured biological signal despite p > 0.05 |

## Project Structure

```
proteomics-ml-reanalysis/
├── README.md
├── notebooks/
│   └── Proteomics_ML_Reanalysis.ipynb
├── requirements.txt
└── .gitignore
```

## Installation

### Requirements
- Python 3.8+
- Jupyter Notebook or JupyterLab

### Setup
```bash
# Clone the repository
git clone https://github.com/a-avasilenko/proteomics-ml-reanalysis.git
cd proteomics-ml-reanalysis

# Install dependencies
pip install -r requirements.txt

# Launch Jupyter
jupyter notebook
```

## Usage

Open `notebooks/Proteomics_ML_Reanalysis.ipynb` and run cells sequentially. The notebook is fully annotated with:
- Methodology explanations
- Result interpretations
- Method comparisons
- Limitations and considerations

## Main Conclusions

1. **Integration is powerful:** Combining traditional statistics with ML provides more comprehensive biomarker discovery than either approach alone

2. **Small sample limitations:** With n=3, p-values have limited power, but ML methods can still extract meaningful patterns through multivariate analysis

3. **Methodological complementarity:** Different approaches capture different biological aspects:
   - Traditional: High-confidence individual proteins
   - PCA: Variance-driving proteins (unsupervised)
   - LASSO: Predictive protein combinations (supervised)

## Skills Demonstrated

- Implementation of classical proteomics statistical pipeline
- Application of unsupervised (PCA) and supervised (LASSO) ML methods
- Critical comparison of complementary analytical approaches
- Understanding of multiple testing correction and regularization
- Data visualization and interpretation
- Recognition of method limitations and appropriate contexts

## Limitations

- Small sample size (n=3) limits statistical power and generalizability
- Novel ML candidates require validation in independent cohorts
- PCA variance may include technical as well as biological variation
- LASSO selection can be unstable with highly correlated features

## Future Directions

Validation of the 22 novel ML candidates would require:
- Larger sample sizes for statistical confirmation
- Independent validation cohort
- Targeted quantification (e.g., parallel reaction monitoring)
- Functional characterization to establish biological relevance

## License

This project is available for educational and research purposes.

## Contact

For questions or collaboration opportunities, please open an issue in this repository.

## Acknowledgments

This analysis builds upon dissertation work in proteomics biomarker discovery for acute kidney injury.
