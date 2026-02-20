# 📈 SPY Volatility Breakout Prediction Model

A machine learning system that predicts SPY volatility breakouts using XGBoost on 1-minute market data. This model identifies periods when the market is likely to experience significant price movements (±5 ATRs) within the next 30 minutes.

## 🎯 Recommended Use Case

**This model is best utilized as a volatility filter for directional trading strategies rather than as a standalone options trading system.**

The model helps identify high-probability volatility periods, which can be combined with directional signals to improve trading strategy performance by filtering out low-movement periods.

## 📊 Performance Metrics

| Metric | Value | Description |
|--------|-------|-------------|
| **AUC Score** | 0.6485 | Marginal but statistically detectable signal |
| **Calibration** | Excellent | Predicted vs actual rates closely aligned |
| **Backtest Return** | +10.9% | Combined puts & calls strategy |
| **Sharpe Ratio** | 0.037 | Low risk-adjusted performance |
| **Max Drawdown** | -9.2% | Peak-to-trough decline |

*Note: Backtest period covers available data using walk-forward validation*

## 📁 Repository Structure

```
big_movement_model/
├── big_movement.ipynb                 # Model development and training
├── backtest_big_movement.ipynb        # Options trading strategy backtest
├── volatility_breakout_model.json     # Trained XGBoost model
├── big_movement_predictions.csv       # Out-of-sample predictions dataset
└── README.md                          # This file
```

## 🔧 Technical Features

- **Walk-Forward Validation**: Time-series validation to prevent look-ahead bias
- **Engineered Features**: 9 custom features including:
  - Volatility ratios (current vs historical)
  - VWAP distance metrics
  - Volume patterns and anomalies
  - Price momentum indicators
- **Real Market Data**: Historical options data from Polygon.io
- **Comprehensive Analysis**: Performance analysis with calibration curves

## 🚀 Getting Started

### Prerequisites

```bash
# Core dependencies
pandas
numpy
xgboost
scikit-learn
matplotlib
seaborn
```

### Usage

1. **Model Training**
   ```python
   # Open big_movement.ipynb
   # Run all cells to train the model
   ```

2. **Backtesting**
   ```python
   # Open backtest_big_movement.ipynb
   # Run all cells to see strategy performance
   ```

3. **Loading the Model**
   ```python
   import xgboost as xgb
   
   model = xgb.XGBClassifier()
   model.load_model('volatility_breakout_model.json')
   ```

## 📈 How It Works

1. **Data Collection**: 1-minute SPY market data with volume, OHLC prices
2. **Feature Engineering**: Calculate volatility ratios, VWAP distance, volume patterns
3. **Target Definition**: Binary classification of ±5 ATR moves in next 30 minutes
4. **Model Training**: XGBoost with time-series cross-validation
5. **Prediction**: Probability scores for upcoming volatility breakouts

## ⚠️ Important Warnings

**NOT RECOMMENDED FOR LIVE OPTIONS TRADING** without significant modifications.

### Key Considerations:
- Transaction costs and slippage not fully accounted for
- Execution constraints in live markets
- Marginal profitability may disappear in real trading conditions
- Model should be used as a filter, not a standalone signal

### Best Implementation:
✅ Combine with directional trading strategies  
✅ Use as a volatility regime filter  
✅ Paper trade extensively before any live deployment  
❌ Do not use standalone for options trading  
❌ Do not expect backtest returns in live trading  

## 📚 Model Insights

The model demonstrates:
- **Calibration**: Predicted probabilities align well with actual outcomes
- **Signal Quality**: AUC of 0.6485 indicates real but weak predictive power
- **Strategy Enhancement**: Best used to avoid low-volatility periods rather than timing entries

## 🤝 Contributing

Contributions, issues, and feature requests are welcome! Feel free to check the issues page.

## 📝 License

This project is provided as-is for educational and research purposes.

## ⚡ Future Improvements

- [ ] Incorporate additional market regime indicators
- [ ] Test on other equity indices and ETFs
- [ ] Implement transaction cost modeling
- [ ] Create web dashboard for visualization

## 📧 Contact

For questions or collaboration opportunities, please open an issue.

---

**Disclaimer**: This model is for educational and research purposes only. Not financial advice. Past performance does not guarantee future results.
