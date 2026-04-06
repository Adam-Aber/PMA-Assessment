# Weather Trend Forecasting — Advanced Analysis

## PM Accelerator Mission

> *"Our mission is to accelerate the careers of product managers by providing world-class education, mentorship, and community. We are committed to democratizing access to product management knowledge and empowering the next generation of product leaders worldwide."*
>
> Learn more at [pmaccelerator.io](https://www.pmaccelerator.io/)

## Project Overview

This project analyzes the [Global Weather Repository](https://www.kaggle.com/datasets/nelgiriyewithana/global-weather-repository) dataset (133K+ records, 41 features, 211 countries) to forecast weather trends and uncover global climate patterns. It fulfills the **Advanced Assessment** requirements for PM Accelerator's Data Scientist/Analyst tech assessment.

## Methodology

### Data Cleaning & Preprocessing
- DateTime parsing of `last_updated` with temporal feature extraction
- IQR-based outlier detection (outliers retained as genuine extreme weather events)
- MinMaxScaler normalization for modeling features

### Exploratory Data Analysis
- Temperature and precipitation distributions, seasonal patterns
- Correlation heatmap across 14+ numerical features
- Wind, humidity, pressure trend analysis
- Weather condition frequency analysis

### Anomaly Detection
- Isolation Forest algorithm on 6 key weather features
- ~5% of data identified as anomalous (extreme weather events)
- Visual analysis of anomaly characteristics

### Forecasting Models (London Temperature)
| Model | Description |
|-------|-------------|
| **SARIMA** | Classical time series with auto-tuned parameters |
| **Prophet** | Facebook's seasonal decomposition model |
| **XGBoost** | Gradient boosting with lag features and cyclical encoding |
| **LSTM** | Deep learning with 30-day lookback sequences |
| **Ensemble** | Weighted average (inverse-RMSE weighting) |

All models evaluated with MAE, RMSE, and MAPE metrics.

### Unique Analyses
- **Climate Analysis**: Continental temperature distributions, monthly heatmaps, extreme region identification
- **Environmental Impact**: Air quality vs weather correlations (PM2.5, Ozone, CO)
- **Spatial Analysis**: Interactive Folium world map, Plotly geo scatter, latitude-temperature gradient
- **Feature Importance**: Random Forest, Permutation, and Correlation-based methods compared

## How to Run

### Prerequisites
```bash
pip install -r requirements.txt
```

### Dataset
Download from Kaggle:
```bash
kaggle datasets download -d nelgiriyewithana/global-weather-repository --unzip
```
Or download manually from: https://www.kaggle.com/datasets/nelgiriyewithana/global-weather-repository

Place `GlobalWeatherRepository.csv` in the project root.

### Run the Notebook
```bash
jupyter notebook weather_trend_forecasting.ipynb
```
Run all cells sequentially (Cell > Run All).

## File Structure
```
PMA Assessment/
├── weather_trend_forecasting.ipynb   # Main analysis notebook
├── GlobalWeatherRepository.csv       # Dataset (download from Kaggle)
├── requirements.txt                  # Python dependencies
└── README.md                         # This file
```

## Key Results
- Ensemble model achieves the best forecasting performance by combining strengths of all four models
- Clear latitude-temperature gradient confirmed across 257 global cities
- Wind speed inversely correlates with PM2.5 levels (dispersal effect)
- Asian cities show highest air pollution; African cities are warmest on average

## Tech Stack
Python 3.11 | pandas | numpy | matplotlib | seaborn | plotly | folium | scikit-learn | statsmodels | Prophet | XGBoost | TensorFlow/Keras
