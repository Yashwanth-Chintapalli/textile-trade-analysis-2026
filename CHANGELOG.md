# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.0.0] - 2024-01-04

### Added

- Initial release of Textile Import Forecasting project
- Complete SARIMAX implementation with grid search
- XGBoost model with 18 engineered features
- SHAP explainability analysis
- Comprehensive residual diagnostics (Ljung-Box, Shapiro-Wilk, Jarque-Bera)
- Window experiment testing training period length
- 10+ high-quality visualizations
- Automated CSV output generation for all results
- Complete documentation (README, CONTRIBUTING, LICENSE)

### Features

- Analysis of 45,413 historical trade records (2011-2022)
- 6 country-HS code combinations (India/China × 3 HS codes)
- 144-month time series with gap filling
- Exogenous variables: Cotton PPI, Textile PPI, Exchange Rates, GDP, Industrial Production
- Train-test split: 132 months training, 12 months testing
- Statistical significance testing (paired t-test)

### Results

- XGBoost outperforms SARIMAX in 83.3% of cases
- Average MAPE: SARIMAX 5,147.76% vs XGBoost 2,819.04%
- Statistically significant difference (p = 0.0146)

### Documentation

- Comprehensive README with hyperlinks
- Installation and usage instructions
- Methodology and technical specifications
- Future work and limitations

## [Unreleased]

### Planned

- Ensemble model (SARIMAX + XGBoost)
- LSTM/Transformer models
- Interactive web dashboard
- API deployment for live predictions
- Extended country coverage
- Real-time data integration

---

## Version History

### [1.0.0] - 2024-01-04

- Initial public release

---

For detailed changes in each release, see the [GitHub Releases](https://github.com/Yashwanth-Chintapalli/textile-import-forecasting/releases) page.
