# Contributing to Textile Import Forecasting

Thank you for your interest in contributing to this project! This document provides guidelines and instructions for contributing.

## 🌟 How to Contribute

### Reporting Issues

1. **Check Existing Issues**: Search [existing issues](https://github.com/yourusername/textile-import-forecasting/issues) to avoid duplicates
2. **Create Detailed Reports**: Include:
   - Clear description of the problem
   - Steps to reproduce
   - Expected vs actual behavior
   - Your environment (OS, Python version, package versions)
   - Error messages and stack traces

### Suggesting Enhancements

- Open an issue with the `enhancement` label
- Describe the feature and its benefits
- Provide use cases and examples

### Code Contributions

#### Setup Development Environment

```bash
# Fork and clone the repository
git clone https://github.com/Yashwanth-Chintapalli/textile-import-forecasting.git
cd textile-import-forecasting

# Create virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Install development dependencies
pip install pytest black flake8 mypy
```

#### Development Workflow

1. **Create a Branch**

   ```bash
   git checkout -b feature/your-feature-name
   ```

2. **Make Changes**
   - Write clean, documented code
   - Follow PEP 8 style guidelines
   - Add docstrings to functions/classes

3. **Format Code**

   ```bash
   black *.py
   flake8 *.py
   ```

4. **Test Changes**

   ```bash
   pytest tests/
   ```

5. **Commit**

   ```bash
   git add .
   git commit -m "Add: Brief description of changes"
   ```

6. **Push and Create Pull Request**

   ```bash
   git push origin feature/your-feature-name
   ```

## 📝 Coding Standards

### Python Style Guide

- Follow [PEP 8](https://peps.python.org/pep-0008/)
- Use type hints where appropriate
- Maximum line length: 88 characters (Black default)

### Documentation

- Add docstrings to all functions/classes:

  ```python
  def forecast_imports(data: pd.DataFrame, model: str) -> pd.Series:
      """
      Generate import forecasts using specified model.
      
      Args:
          data: Historical trade data with exogenous variables
          model: Model type ('sarimax' or 'xgboost')
          
      Returns:
          Series of forecasted values with datetime index
          
      Raises:
          ValueError: If model not in ['sarimax', 'xgboost']
      """
      pass
  ```

### Testing

- Add unit tests for new functions
- Maintain >80% code coverage
- Use pytest fixtures for test data

## 🔍 Areas for Contribution

### High Priority

- [ ] Implement ensemble model combining SARIMAX + XGBoost
- [ ] Add LSTM/GRU models for deep learning comparison
- [ ] Create interactive Plotly/Dash dashboard
- [ ] Improve handling of structural breaks (COVID-19, etc.)

### Documentation

- [ ] Add tutorials for beginners
- [ ] Create video walkthrough
- [ ] Translate README to other languages

### Performance

- [ ] Optimize SARIMAX grid search
- [ ] Add GPU acceleration for XGBoost
- [ ] Implement parallel processing for multiple countries

### New Features

- [ ] Real-time data ingestion from APIs
- [ ] Automated hyperparameter tuning (Optuna/Ray Tune)
- [ ] Scenario analysis ("what-if" simulations)

## 🤝 Community Guidelines

- Be respectful and inclusive
- Provide constructive feedback
- Help newcomers get started
- Acknowledge contributions from others

## 📜 License

By contributing, you agree that your contributions will be licensed under the MIT License.

## ❓ Questions?

- Open a [GitHub Discussion](https://github.com/Yashwanth-Chintapalli/textile-import-forecasting/discussions)

---

**Thank you for contributing! 🎉**
