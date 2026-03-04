HK Stock Analysis Pipeline — Introduction
What Is This Project?
This project is an end-to-end stock analysis and price forecasting pipeline designed specifically for Hong Kong (HKEX) listed stocks. It automatically fetches historical price data, computes technical indicators, performs statistical and machine learning analysis, and generates short-term to medium-term price forecasts using state-of-the-art deep learning models.
The pipeline is split into four notebooks, each serving a distinct stage of the analysis workflow — from raw data collection all the way through to deep learning-based price predictions.

Who Is It For?
This project is intended for:

Quantitative analysts and traders who want a reproducible, automated pipeline for HK equity research.
Data scientists exploring financial time-series modelling using classical ML and deep learning.
Students and researchers studying technical indicator-based stock prediction methods.


What Can It Do?
The pipeline provides the following capabilities:

Automated Data Fetching — Downloads 5 years of historical OHLCV (Open, High, Low, Close, Volume) data from Yahoo Finance for any HK-listed stock, and computes a full suite of technical indicators.
Descriptive Statistics & Visualisation — Generates summary statistics, price trend charts, return distributions, and correlation heatmaps to understand a stock's historical behaviour.
Feature Selection via LASSO & Random Forest — Uses both Random Forest importance scores and LASSO regression with cross-validation to identify the most predictive technical indicators for price forecasting.
Batch XGBoost Analysis — Runs Bayesian-optimised XGBoost models across an entire folder of stock files at once, producing feature importance rankings for each stock automatically.
Deep Learning Forecasting (LSTM & TCN) — Uses XGBoost to select the top 2 most important indicators per stock, then trains both a Long Short-Term Memory (LSTM) network and a Temporal Convolutional Network (TCN) to forecast the next 30 days of closing prices.


The Four Notebooks at a Glance
NotebookPurposedata_fetching_code.ipynbFetch raw data from Yahoo Finance and compute technical indicatorsdescriptive_statistics_and_LASSO_MODELS_0005.ipynbExploratory analysis, feature importance (Random Forest + LASSO), and 3-day price predictionPatch_data_analysis_of_overall_stock_bysten_model.ipynbBatch XGBoost feature importance analysis across multiple stocksTransfromer_and_LSTM_analysis__user_input_.ipynbInteractive single-stock analysis with XGBoost → LSTM → TCN forecasting pipeline

Target Stocks
The pipeline is designed for Hong Kong Exchange (HKEX) stocks, identified by tickers in the format XXXX.HK (e.g., 0005.HK for HSBC, 0700.HK for Tencent, 0388.HK for HKEX itself). However, the data fetching logic can be extended to any Yahoo Finance-supported ticker.

Technical Indicators Computed
The pipeline automatically computes the following indicators from raw OHLCV data:

SMA_20 — 20-day Simple Moving Average
EMA_20 / EMA_50 — 20-day and 50-day Exponential Moving Averages
Moving_Average — Blended average of SMA_20 and EMA_20
MACD — Moving Average Convergence Divergence (12-day EMA minus 26-day EMA)
ROC — Rate of Change over 12 days (percentage)
Daily_Returns — Day-over-day percentage price change
VFI — Volume Flow Indicator (volume z-score relative to 20-day window)
MFI — Money Flow Index (14-day momentum oscillator combining price and volume)
RSI_14 — 14-day Relative Strength Index
Bollinger Bands (Upper & Lower) — 20-day rolling mean ± 2 standard deviations
ATR_14 — 14-day Average True Range (volatility proxy)


Output Files Produced
Depending on which notebooks you run, the pipeline saves the following files to your configured Stock data directory:
FileDescription{TICKER}.xlsxRaw data + computed technical indicators{TICKER}_cleaned.xlsxCleaned data with NaN and zero rows removed{TICKER}_selected_features.xlsxTop 2 XGBoost-selected features for LSTM/TCN input{TICKER}_LSTM_predictions.xlsx30-day LSTM price forecast{TICKER}_TCN_predictions.xlsx30-day TCN price forecast

Quick Summary
This is a complete quantitative research toolkit for HK stocks. You start by fetching and cleaning data, explore it statistically, use machine learning to identify the most predictive signals, and finally generate month-ahead price forecasts using deep learning. Each notebook is self-contained and can be run independently once the data files are in place.
