# # LSTM Model for Stock Price Prediction

## Overview

This project uses an LSTM (Long Short-Term Memory) model to predict the closing price of a stock based on historical data from Alpha Vantage API. The model is trained on historical stock prices and validated on unseen data to evaluate its prediction performance. The project includes data downloading, preprocessing, model training, and prediction visualization.

## Requirements

- Python 3.x
- Libraries: `numpy`, `torch`, `matplotlib`, `alpha_vantage`
- Alpha Vantage API key (you can get one from [here](https://www.alphavantage.co/support/#api-key))

## Configuration

```python
config = {
    "alpha_vantage": {
        "key": "YOUR_API_KEY",  # Replace with your API key
        "symbol": "IBM",  # Replace with the desired stock symbol
        "outputsize": "full",  # Data size (full or compact)
        "key_adjusted_close": "5. adjusted close",  # Key for adjusted close prices
    },
    "data": {
        "window_size": 20,  # Number of previous days to consider for prediction
        "train_split_size": 0.80,  # Percentage of data for training (80% in this case)
    },
    "plots": {
        "xticks_interval": 90,  # Show a date every 90 days
        "color_actual": "#001f3f",  # Color for actual data
        "color_train": "#3D9970",  # Color for training data
        "color_val": "#0074D9",  # Color for validation data
        "color_pred_train": "#3D9970",  # Color for predicted training data
        "color_pred_val": "#0074D9",  # Color for predicted validation data
        "color_pred_test": "#FF4136",  # Color for predicted test data
    },
    "model": {
        "input_size": 1,  # Using only close price as feature
        "num_lstm_layers": 2,  # Number of LSTM layers
        "lstm_size": 32,  # Size of LSTM layers
        "dropout": 0.2,  # Dropout rate for regularization
    },
    "training": {
        "device": "cpu",  # Device for training ("cuda" for GPU, "cpu" for CPU)
        "batch_size": 64,  # Batch size for training
        "num_epoch": 100,  # Number of training epochs
        "learning_rate": 0.01,  # Learning rate for optimizer
        "scheduler_step_size": 40,  # Scheduler step size for learning rate decay
    }
}
