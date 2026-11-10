# Impact of Training Data Size and Multi-Step Output Strategies on AI-Based Dekadal and Monthly Rainfall Forecasting

Python code accompanying the article:

> Sonon B, et al. Impact of Training Data Size and Multi-Step Output Strategies on AI-Based Dekadal and Monthly Rainfall Forecasting.

The study forecasts rainfall at the Kandi synoptic station (northern Benin) three steps ahead (T+1, T+2, T+3) at dekadal and monthly resolution. It compares six models (SVR, Random Forest, CatBoost, ANN, LSTM, TNN), four multi-step strategies (Direct, Recursive, MIMO, DIRMO) and two historical-data configurations (training 1970–1999 / test 2000–2007, and training 1970–2013 / test 2014–2024), and tests the differences with Friedman, Nemenyi and Wilcoxon tests.

## Content

`rainfall_forecasting_kandi.ipynb` contains the complete workflow:

1. experimental design (periods, look-back windows, horizon, DIRMO blocks, seed)
2. data loading, chronological train/test split, KNN imputation and scaling (fitted on training years only)
3. sliding-window construction of the supervised samples
4. performance metrics (RMSE, MAE, R, R², NSE, KGE)
5. the six models and their hyperparameters
6. hyperparameter search with time-series cross-validation
7. the four multi-step strategies
8. experiments, statistical tests and trend figure

## Data

The meteorological data were acquired under license from the National Meteorological Agency of Benin (Météo-Bénin) and are subject to third-party restrictions. They cannot be redistributed by the authors and are **not included** in this repository.

Researchers can request the data from Météo-Bénin through its official portal (https://www.meteobenin.bj) or by contacting the data management service at contact@meteobenin.bj.

The notebook expects two semicolon-separated files in a `data/` folder:

- `end_kandi.csv` (dekadal): `Year`, `decade_rainfall`, `tmax`, `tmin`, `insola`, `weedpred`, `humidR`, `ETP`
- `Data_Kandi_end.csv` (monthly): `Month` (contains the year), `Rainfall_Amount`, `Hmax`, `Insola`, `Vapeur_tension`, `Vitess_vent`, `Tmax`, `Tmin`

## Requirements

Python 3.10 with numpy 1.26.4, pandas 2.1.4, scipy 1.11.4, scikit-learn 1.3.0, catboost 1.2.2, tensorflow 2.18.0 and matplotlib 3.8.2.
