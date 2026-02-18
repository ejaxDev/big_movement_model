# Volatility Breakout Prediction Model

## Overview
A machine learning system that predicts SPY volatility breakouts using XGBoost on 1-minute market data. The model identifies periods when the market is likely to experience significant price movements (±5 ATRs) within the next 30 minutes.

## Key Performance Metrics
- **AUC Score**: 0.6489 (marginal but detectable signal)
- **Calibration**: Excellent (predicted vs actual rates closely aligned)
- **Backtest Return**: +95.9% vs SPY's +82.1% (2023-2025)
- **Sharpe Ratio**: 0.07 (low risk-adjusted performance)
- **Max Drawdown**: -23%

## 🎯 **Recommended Use Case**

**This model is best utilized as a volatility filter for directional trading strategies rather than as a standalone options trading system.**

### Optimal Implementation Strategy:
- **Pair with directional signals**: Use the volatility predictions to filter out low-movement periods when directional strategies underperform

## Files Structure
- `big_movement.ipynb` - Model development and training
- `backtest_big_movement.ipynb` - Options trading strategy backtest
- `volatility_breakout_model.json` - Trained XGBoost model
- `big_movement_predictions.csv` - Out-of-sample predictions dataset

## Technical Features
- Walk-forward time-series validation
- 9 engineered features (volatility ratios, VWAP distance, volume patterns)
- Real historical options data from Polygon.io
- Comprehensive performance analysis with calibration curves

## Usage Warning
**Not recommended for live options trading without significant modifications.** The standalone options strategy shows marginal profitability that would likely disappear after realistic transaction costs, slippage, and execution constraints.
