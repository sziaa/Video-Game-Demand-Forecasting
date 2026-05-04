# Video-Game-Demand-Forecasting
Time-series forecasting project predicting next-month video game demand using Random Forest and lag-based features, achieving 24% improvement over baseline and analyzing model performance on volatile, event-driven games.

The goal is to understand how player demand evolves over time and identify the key drivers of forecasting performance.

**Problem Statement**

Accurately forecasting player demand is critical for:
- game studios planning updates and releases
- platform operators managing infrastructure and engagement
- understanding player behavior dynamics

This project aims to predict next-month average player counts using historical data and evaluate model performance across different game behaviors.

**Dataset**


Source: SteamCharts + Steam metadata APIs

Scope: 100+ popular video games

Time horizon: Monthly player data across multiple years

Each data point includes:
- historical player counts
- lagged features (previous months)
- rolling averages
- growth and momentum signals
- volatility and lifecycle indicators

**Methodology**

1. Feature Engineering

Constructed time-series features including:

- Lag features (lag_1, lag_2, lag_3, lag_6)
- Rolling averages (rolling_mean_3, rolling_mean_6)
- Momentum (growth_1, growth_3)
- Volatility (volatility_3)
- Spike detection and lifecycle (recent_spike, drop_from_peak)

2. Modeling

Evaluated multiple supervised learning models:

- Linear Regression
- Random Forest
- XGBoost
- LightGBM

Final model: Random Forest

3. Evaluation

Metrics used:

- Mean Absolute Percentage Error (MAPE)
- Mean Absolute Error (MAE)
- Root Mean Squared Error (RMSE)

Results:

- Best Model (Random Forest): 14.40% MAPE
- Baseline: 19.05% MAPE
- Improvement: 24.39%

**Key Findings**

- Demand is highly autocorrelated
  - ~95% of predictive signal comes from recent player activity
  - Lag and rolling features dominate feature importance
- Forecasting works best for stable games
  - Low-volatility games: ~11.7% error
  - High-volatility games: ~17.2% error
- Event-driven spikes are the main source of error
  - Largest errors occur on games with: updates, viral growth, seasonal spikes
- Model shows slight overprediction bias
  - ~54% of predictions overestimate demand
  - Indicates difficulty capturing post-spike declines
- Lifecycle alone is not a strong predictor
  - Distance from peak does not strongly explain short-term growth

**Limitations**

- Model relies solely on historical player data
- Does not incorporate external signals such as: game updates, DLC releases, marketing events
- Struggles with highly volatile, event-driven games

**Future Improvements**

- Incorporate external data sources (news, updates, release schedules)
- Use sequence-based models (LSTM, Transformer)
- Add classification layer to detect spike events
- Improve forecasting for high-volatility segments

**Tech Stack**

- Python
- Pandas / NumPy
- Scikit-learn
- XGBoost / LightGBM
- Matplotlib / Seaborn

Built by [Sehrish Zia]
