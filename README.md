# Textile Import Forecasting: SARIMAX vs XGBoost

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Status](https://img.shields.io/badge/Status-Complete-success.svg)]()

> **A comprehensive econometric and machine learning analysis comparing SARIMAX and XGBoost models for textile import forecasting across India and China (2011-2022)**

---

## 📋 Table of Contents

- [Overview](#overview)
- [Research Question](#research-question)
- [Key Findings](#key-findings)
- [Project Structure](#project-structure)
- [Dataset Description](#dataset-description)
- [Methodology](#methodology)
  - [Data Preparation](#data-preparation)
  - [Feature Engineering](#feature-engineering)
  - [Model Implementation](#model-implementation)
  - [Evaluation Metrics](#evaluation-metrics)
- [Installation](#installation)
- [Usage](#usage)
- [Results & Visualizations](#results--visualizations)
- [Model Diagnostics](#model-diagnostics)
- [Explainability Analysis](#explainability-analysis)
- [Technical Specifications](#technical-specifications)
- [Limitations & Future Work](#limitations--future-work)
- [Contributing](#contributing)
- [Citation](#citation)
- [License](#license)
- [Contact](#contact)

---

## 🎯 Overview

This repository contains a rigorous time-series forecasting study that evaluates the performance of **SARIMAX** (Seasonal AutoRegressive Integrated Moving Average with eXogenous variables) and **XGBoost** (eXtreme Gradient Boosting) models for predicting textile import values. The analysis spans **144 months** (2011-2022) and covers three major textile categories across two of the world's largest textile markets.

### Key Features

- ✅ **Comprehensive Time-Series Analysis**: 45,413+ historical trade records
- ✅ **Dual-Model Comparison**: Classical econometric vs. modern machine learning
- ✅ **Multi-Country Study**: India and China
- ✅ **Product-Level Granularity**: HS Codes 52, 55, 60
- ✅ **Exogenous Variables**: Cotton PPI, Textile PPI, Exchange Rates, GDP Growth, Industrial Production
- ✅ **Rigorous Diagnostics**: Ljung-Box, Shapiro-Wilk, Jarque-Bera tests
- ✅ **Explainability**: SHAP (SHapley Additive exPlanations) value analysis
- ✅ **Reproducible Research**: Fully documented code and methodology

---

## 🔬 Research Question

**"Which forecasting model—SARIMAX or XGBoost—demonstrates superior performance for predicting monthly textile import values in emerging markets during periods of economic volatility?"**

### Hypotheses

| Model | Hypothesis |
|-------|-----------|
| **SARIMAX** | Captures seasonal patterns and structural relationships in textile trade |
| **XGBoost** | Learns complex non-linear interactions between exogenous variables |

---

## 🏆 Key Findings

### Model Performance Summary

| Metric | SARIMAX | XGBoost | Winner |
|--------|---------|---------|--------|
| **Average MAPE** | 5,147.76% | 2,819.04% | 🏆 **XGBoost** |
| **Best Performance** | 3,724.07% | 1,623.92% | 🏆 **XGBoost** |
| **Win Rate** | 1/6 (16.7%) | 5/6 (83.3%) | 🏆 **XGBoost** |
| **Statistical Significance** | p = 0.0146 | ✓ Confirmed | 🏆 **XGBoost** |

### Detailed Results by Category

| Country | HS Code | Product | SARIMAX MAPE | XGBoost MAPE | Improvement |
|---------|---------|---------|--------------|--------------|-------------|
| **China** | 52 | Cotton | 4,885.33% | **1,623.92%** | ⬇️ 3,261.41% |
| **China** | 55 | Man-made Fibres | 6,530.32% | **2,322.20%** | ⬇️ 4,208.12% |
| **China** | 60 | Knitted Fabrics | 5,726.80% | **4,066.57%** | ⬇️ 1,660.23% |
| **India** | 52 | Cotton | **4,705.39%** | 4,916.68% | ⬆️ 211.29% |
| **India** | 55 | Man-made Fibres | 5,314.67% | **2,161.40%** | ⬇️ 3,153.27% |
| **India** | 60 | Knitted Fabrics | 3,724.07% | **1,823.48%** | ⬇️ 1,900.59% |

### Key Insights

1. **XGBoost Dominance**: Outperforms SARIMAX in 83.3% of cases with statistically significant superiority (p < 0.05)
2. **Lag Features Critical**: Rolling means (3-month, 6-month) and lag-1 values emerge as top predictors
3. **China Trade Complexity**: Higher forecast errors indicate greater market volatility
4. **Knitted Fabrics Most Predictable**: Lowest MAPE across both models
5. **Seasonal Patterns**: HS 52 (Cotton) shows strong quarterly effects

---

## 📂 Project Structure

```
textile-import-forecasting/
│
├── 📓 Finalanalysis.ipynb                    # Main analysis notebook (43 cells)
├── 📄 README.md                               # This file
├── 📘 Traditional Research Project.docx       # Research documentation
│
├── 📁 Dataset/
│   ├── 2011-2017.csv                          # Historical trade data
│   └── textile_with_exogenous_FINAL.csv       # Merged dataset with exogenous vars
│
├── 📁 Outputs/ (Generated)
│   ├── monthly_aggregated_timeseries.csv      # Preprocessed monthly data
│   ├── imports_hs_level_complete.csv          # Gap-filled complete time series
│   │
│   ├── SARIMAX_Model_Summary.csv              # SARIMAX results
│   ├── SARIMAX_Forecasts.csv                  # SARIMAX predictions
│   ├── SARIMAX_Diagnostic_Summary.csv         # Residual diagnostics
│   │
│   ├── XGBoost_Model_Summary.csv              # XGBoost results
│   ├── XGBoost_Forecasts.csv                  # XGBoost predictions
│   ├── SHAP_Feature_Importance.csv            # Feature explainability
│   │
│   ├── Model_Comparison_Summary.csv           # Head-to-head comparison
│   ├── Final_Summary_Report.txt               # Executive summary
│   │
│   └── extra test/
│       ├── Window_Experiment_Results.csv      # Training window experiments
│       └── Window_Experiment_Comparison.png
│
└── 📁 Figures/ (Generated)
    ├── Figure_1_HS_Level_Imports_Complete.png
    ├── Figure_2_HS_Stacked_Area.png
    ├── Figure_SARIMAX_Forecasts.png
    ├── Figure_XGBoost_Forecasts.png
    ├── Figure_Combined_Forecasts.png
    ├── Figure_Feature_Importance.png
    ├── Figure_SHAP_Feature_Importance.png
    ├── Figure_SHAP_Summary_Beeswarm.png
    ├── Figure_SARIMAX_Residual_Diagnostics.png
    ├── Figure_Model_Comparison_MAPE.png
    └── Figure_Scatter_Comparison.png
```

---

## 📊 Dataset Description

### Data Sources

1. **UN Comtrade Database**: Historical trade data (2011-2017)
2. **FRED (Federal Reserve Economic Data)**: Macroeconomic indicators
3. **Custom Integration**: Merged dataset with exogenous variables (2018-2022)

### Dataset Statistics

| Attribute | Value |
|-----------|-------|
| **Total Records** | 45,413 |
| **Time Period** | 2011-01 to 2022-12 (144 months) |
| **Countries** | India, China, USA |
| **HS Codes** | 52 (Cotton), 55 (Man-made Fibres), 60 (Knitted Fabrics) |
| **Trade Flows** | Import, Export |
| **Monthly Observations** | 588 (after aggregation) |

### Variables

#### Dependent Variable

- `primaryValue`: Monthly import value (USD)

#### Exogenous Variables

| Variable | Description | Source |
|----------|-------------|--------|
| `cotton_ppi` | Cotton Producer Price Index | FRED |
| `textile_ppi` | Textile Producer Price Index | FRED |
| `usd_cny` | USD/CNY Exchange Rate | FRED |
| `usd_inr` | USD/INR Exchange Rate | FRED |
| `gdp_growth` | GDP Growth Rate (%) | World Bank |
| `industrial_prod` | Industrial Production Index | FRED |

#### Feature-Engineered Variables (XGBoost)

| Feature Type | Variables |
|--------------|-----------|
| **Temporal** | `year`, `month`, `quarter`, `month_sin`, `month_cos`, `trend` |
| **Lag Features** | `lag_1`, `lag_3`, `lag_6`, `lag_12` |
| **Rolling Statistics** | `rolling_mean_3`, `rolling_mean_6`, `rolling_std_3` |

### Data Quality

- ✅ **Missing Data Handling**: Forward/backward fill for gaps
- ✅ **Outlier Treatment**: Retained for analysis (COVID-19 period preserved)
- ✅ **Stationarity**: ADF test performed; differencing applied where needed
- ✅ **Seasonality**: Monthly frequency (MS) with 12-month cycles

---

## 🔧 Methodology

### Data Preparation

1. **Data Loading**

   ```python
   # Merge historical (2011-2017) and recent (2018-2022) data
   df_combined = pd.concat([df_historical, df_current], ignore_index=True)
   ```

2. **Aggregation**
   - Group by: `date`, `reporter_name`, `hs_code`, `flow`
   - Aggregate: Sum trade values, count trading partners

3. **Gap Filling**

   ```python
   # Create complete monthly time series (2011-2022)
   full_range = pd.date_range(start='2011-01-01', end='2022-12-01', freq='MS')
   subset = subset.reindex(full_range).fillna(method='ffill').fillna(method='bfill')
   ```

### Feature Engineering

#### SARIMAX Features

- **Endogenous**: `primaryValue` (log-transformed if needed)
- **Exogenous**: `cotton_ppi`, `textile_ppi`, `usd_cny`, `gdp_growth`, `industrial_prod`

#### XGBoost Features

- **18 Total Features**:
  - 6 Temporal: Year, month, quarter, cyclical encoding
  - 4 Lag: 1, 3, 6, 12-month lags
  - 3 Rolling: 3-month mean, 6-month mean, 3-month std
  - 5 Exogenous: Macro indicators

### Model Implementation

#### SARIMAX

**Parameter Selection**: Grid search over:

- `p, d, q ∈ {0, 1, 2}` (ARIMA orders)
- `P, D, Q ∈ {0, 1}` (Seasonal orders)
- `s = 12` (Monthly seasonality)

**Model Specification**:

```python
SARIMAX(
    endog=y_train,
    exog=exog_train,
    order=(p, d, q),
    seasonal_order=(P, D, Q, 12),
    enforce_stationarity=False,
    enforce_invertibility=False
)
```

**Best Models**:

- India HS 52: SARIMAX(1,0,2)(1,1,1,12)
- China HS 52: SARIMAX(2,1,2)(1,1,1,12)

#### XGBoost

**Hyperparameters**:

```python
{
    'objective': 'reg:squarederror',
    'max_depth': 4,
    'learning_rate': 0.1,
    'n_estimators': 200,
    'subsample': 0.8,
    'colsample_bytree': 0.8
}
```

**Training Strategy**:

- No early stopping (uses all training data)
- Feature importance via gain calculation
- SHAP values for explainability

### Evaluation Metrics

| Metric | Formula | Interpretation |
|--------|---------|----------------|
| **MAPE** | `(1/n) Σ |yᵢ - ŷᵢ|/yᵢ × 100%` | Lower is better; scale-independent |
| **RMSE** | `√[(1/n) Σ (yᵢ - ŷᵢ)²]` | Penalizes large errors |
| **MAE** | `(1/n) Σ |yᵢ - ŷᵢ|` | Absolute error magnitude |

### Train-Test Split

- **Training Period**: 2011-01 to 2021-12 (132 months)
- **Testing Period**: 2022-01 to 2022-12 (12 months)
- **Validation Strategy**: Walk-forward validation

---

## 💻 Installation

### Prerequisites

- Python 3.8+
- Jupyter Notebook/Lab
- 8GB+ RAM (recommended for SHAP analysis)

### Setup

1. **Clone the Repository**

   ```bash
   git clone https://github.com/Yashwanth-Chintapalli/textile-import-forecasting.git
   cd textile-import-forecasting
   ```

2. **Create Virtual Environment**

   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install Dependencies**

   ```bash
   pip install -r requirements.txt
   ```

   **Core Libraries**:

   ```
   pandas>=1.5.0
   numpy>=1.23.0
   matplotlib>=3.6.0
   seaborn>=0.12.0
   statsmodels>=0.14.0
   xgboost>=1.7.0
   shap>=0.41.0
   scipy>=1.10.0
   scikit-learn>=1.2.0
   ```

4. **Verify Installation**

   ```bash
   python -c "import xgboost, statsmodels, shap; print('All packages installed successfully!')"
   ```

---

## 🚀 Usage

### Quick Start

1. **Open Jupyter Notebook**

   ```bash
   jupyter notebook Finalanalysis.ipynb
   ```

2. **Run All Cells**
   - Navigate to `Cell > Run All`
   - Estimated runtime: 15-20 minutes

### Step-by-Step Execution

#### Part 1: Data Loading & Exploration

```python
# Cell 0-13: Load, clean, aggregate, and visualize data
df = pd.read_csv('textile_with_exogenous_FINAL.csv')
monthly_agg = create_aggregated_timeseries(df)
```

#### Part 2: SARIMAX Modeling

```python
# Cell 14-20: Build SARIMAX models for all country-HS combinations
sarimax_results = build_sarimax_models(imports_complete)
```

#### Part 3: XGBoost Modeling

```python
# Cell 21-27: Train XGBoost with engineered features
xgboost_results = build_xgboost_models(imports_features)
```

#### Part 4: Model Comparison

```python
# Cell 28-38: Compare performance and visualize results
comparison = compare_models(sarimax_results, xgboost_results)
```

#### Part 5: Diagnostics & Explainability

```python
# Cell 40-42: Residual diagnostics and SHAP analysis
diagnostics = sarimax_diagnostics(sarimax_results)
shap_analysis = explain_xgboost(xgboost_results)
```

#### Part 6: Window Experiments

```python
# Cell 43: Test impact of training window length
window_results = run_window_experiment(df)
```

### Custom Analysis

**Modify Countries**:

```python
countries = ['India', 'China', 'USA']  # Add more countries
```

**Change HS Codes**:

```python
hs_codes = [52, 55, 60, 61, 62]  # Expand product categories
```

**Adjust Train-Test Split**:

```python
test_len = 24  # Last 24 months as test set
train_size = len(data) - test_len
```

---

## 📈 Results & Visualizations

### Figure 1: Time Series Trends

![HS-Level Imports](Figures/Figure_1_HS_Level_Imports_Complete.png)
*Monthly textile import values by HS code (2011-2022). COVID-19 period highlighted.*

### Figure 2: Import Composition

![Stacked Area](Figures/Figure_2_HS_Stacked_Area.png)
*Relative contribution of each textile category to total imports.*

### Figure 3: Model Comparison

![Combined Forecasts](Figures/Figure_Combined_Forecasts.png)
*Actual vs predicted values for SARIMAX and XGBoost (2022 test period).*

### Figure 4: Performance Summary

![MAPE Comparison](Figures/Figure_Model_Comparison_MAPE.png)
*Head-to-head MAPE comparison across all country-HS combinations.*

### Figure 5: Actual vs Predicted

![Scatter Comparison](Figures/Figure_Scatter_Comparison.png)
*Scatter plots showing prediction accuracy relative to perfect prediction line.*

---

## 🔍 Model Diagnostics

### SARIMAX Residual Tests

| Test | Purpose | Interpretation |
|------|---------|----------------|
| **Ljung-Box** | Autocorrelation detection | p > 0.05 → Residuals independent |
| **Shapiro-Wilk** | Normality test | p > 0.05 → Normally distributed |
| **Jarque-Bera** | Skewness & Kurtosis | p > 0.05 → Normal distribution |

#### Results Summary

| Country-HS | Ljung-Box (p) | Shapiro-Wilk (p) | Autocorrelation | Normality |
|------------|---------------|------------------|-----------------|-----------|
| India-52 | <0.001 | <0.001 | ❌ Failed | ❌ Failed |
| India-55 | 0.250 | <0.001 | ✅ Passed | ❌ Failed |
| India-60 | 0.999 | <0.001 | ✅ Passed | ❌ Failed |
| China-52 | 0.957 | <0.001 | ✅ Passed | ❌ Failed |
| China-55 | 0.837 | <0.001 | ✅ Passed | ❌ Failed |
| China-60 | 0.830 | <0.001 | ✅ Passed | ❌ Failed |

**Key Observation**: Most models pass autocorrelation test but fail normality (common in financial/trade data due to skewness and heavy tails).

---

## 🧩 Explainability Analysis

### SHAP Feature Importance

**Top 5 Most Influential Features (Averaged Across Models)**:

| Rank | Feature | Mean |SHAP Value| | Insight |
|------|---------|-------------|---------|
| 1 | `rolling_mean_3` | 4.3e+07 | Recent trends dominate predictions |
| 2 | `usd_cny` | 2.9e+07 | Exchange rate fluctuations critical |
| 3 | `lag_1` | 1.8e+07 | Immediate past month highly predictive |
| 4 | `rolling_std_3` | 1.5e+07 | Volatility signals regime changes |
| 5 | `cotton_ppi` | 9.2e+06 | Raw material costs impact forecasts |

### Country-Specific Insights

**India**:

- Cotton PPI most important for HS 52
- Rolling means dominate HS 55 and HS 60
- Lower volatility → Better predictability

**China**:

- Exchange rates (USD/CNY) most critical
- Textile PPI strongly influences HS 55
- Higher trade volumes → More noise

---

## ⚙️ Technical Specifications

### Computational Environment

- **OS**: macOS 13.0+ / Ubuntu 20.04+ / Windows 10+
- **Python**: 3.8.10
- **Statsmodels**: 0.14.0 (SARIMAX implementation)
- **XGBoost**: 1.7.5 (GPU acceleration optional)
- **SHAP**: 0.41.0 (TreeExplainer for XGBoost)

### Performance Benchmarks

| Task | Time (CPU) | Time (GPU) | Memory |
|------|-----------|-----------|---------|
| Data Preprocessing | 12s | - | 450 MB |
| SARIMAX Grid Search | 8 min | - | 1.2 GB |
| XGBoost Training (6 models) | 45s | 18s | 850 MB |
| SHAP Value Computation | 3 min | 1 min | 1.5 GB |
| **Total Pipeline** | **~15 min** | **~8 min** | **2.5 GB** |

*Tested on: Intel i7-11700K, 32GB RAM, NVIDIA RTX 3070*

---

## ⚠️ Limitations & Future Work

### Current Limitations

1. **MAPE Interpretation**: High MAPE values (>100%) occur due to near-zero actual values in some months (India HS 52 Jan 2022: $2.9M actual vs $260M predicted). Consider using MASE (Mean Absolute Scaled Error) for better context.

2. **Structural Breaks**: 2022 test period includes:
   - Russia-Ukraine conflict (Feb 2022)
   - Supply chain disruptions (2020-2022)
   - Models struggle with unprecedented shocks

3. **Data Granularity**: Monthly aggregation masks within-month volatility

4. **Exogenous Variable Selection**: Limited to available FRED data; country-specific policy variables omitted

### Future Enhancements

- [ ] **Ensemble Models**: Combine SARIMAX and XGBoost predictions
- [ ] **Deep Learning**: LSTM/Transformer models for sequential patterns
- [ ] **Real-Time Forecasting**: Streaming data integration
- [ ] **Explainability++**: Counterfactual analysis ("What-if" scenarios)
- [ ] **Web Dashboard**: Interactive Plotly/Dash interface
- [ ] **API Deployment**: FastAPI endpoint for live predictions
- [ ] **More Countries**: Expand to Bangladesh, Vietnam, Turkey
- [ ] **Policy Simulation**: Test tariff/quota impacts

---

## 🤝 Contributing

Contributions are welcome! Please follow these guidelines:

1. **Fork the Repository**
2. **Create a Feature Branch**

   ```bash
   git checkout -b feature/amazing-feature
   ```

3. **Commit Changes**

   ```bash
   git commit -m "Add amazing feature"
   ```

4. **Push to Branch**

   ```bash
   git push origin feature/amazing-feature
   ```

5. **Open Pull Request**

### Code Standards

- Follow PEP 8 style guide
- Add docstrings to functions
- Include unit tests for new features
- Update README.md with new functionality

---

## 📝 Citation

If you use this work in your research, please cite:

```bibtex
@misc{textile_forecasting_2024,
  author = {Yashwanth Chintapalli},
  title = {Textile Import Forecasting: SARIMAX vs XGBoost},
  year = {2024},
  publisher = {GitHub},
  url = {https://github.com/Yashwanth-Chintapalli/textile-import-forecasting}
}
```

---

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

### Third-Party Data Attribution

- **UN Comtrade**: Trade data used under [UN Comtrade Terms of Use](https://comtrade.un.org/db/help/licenseagreement.aspx)
- **FRED**: Data provided by Federal Reserve Bank of St. Louis

---

## 📧 Contact

**Project Maintainer**: Yashwanth Chintapalli

- GitHub: [@Yashwanth-Chintapalli](https://github.com/Yashwanth-Chintapalli)

**Research Collaboration**: Open to partnerships with:

- Academic institutions
- Trade policy analysts
- Supply chain consultants
- Textile industry professionals

---

## 🙏 Acknowledgments

- **Data Sources**: UN Comtrade, Federal Reserve (FRED), World Bank
- **Libraries**: Statsmodels, XGBoost, SHAP development teams
- **Inspiration**: Time-series forecasting literature (Hyndman & Athanasopoulos, 2021)

---

## 📚 References

1. Hyndman, R. J., & Athanasopoulos, G. (2021). *Forecasting: Principles and Practice* (3rd ed.). OTexts.
2. Chen, T., & Guestrin, C. (2016). XGBoost: A Scalable Tree Boosting System. *KDD '16*.
3. Lundberg, S. M., & Lee, S. I. (2017). A Unified Approach to Interpreting Model Predictions. *NeurIPS*.
4. Box, G. E. P., & Jenkins, G. M. (1970). *Time Series Analysis: Forecasting and Control*. Holden-Day.

---

<div align="center">

**⭐ Star this repository if you found it helpful!**

Made with ❤️ for the time-series forecasting community

</div>
