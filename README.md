# Traffic Prediction with LSTM

This repository implements **traffic demand forecasting** using **LSTM** (Long Short-Term Memory) neural networks. The goal is to predict future traffic volumes based on historical traffic data, including features like weather conditions and time-related features.

## Table of Contents
- [Overview](#overview)
- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
- [Evaluation](#evaluation)
- [Results](#results)
- [License](#license)

## Overview

Predicting traffic demand is a challenging yet critical task for urban planning and management. This project uses **LSTM**, a type of recurrent neural network (RNN), to model the temporal dependencies in traffic data and forecast future traffic volumes.

## Features

- **Data Preprocessing**: Clean, normalize, and one-hot encode categorical data.
- **LSTM Model**: Forecast traffic demand based on historical data.
- **Evaluation Metrics**: Mean Squared Error (MSE) to assess model performance.
- **Visualization**: Graphs comparing actual vs predicted traffic counts.
- **Data**: Supports traffic, temperature, and weather condition data.

## Installation

To get started, clone the repository and install the required dependencies.

1. Clone the repository:
    ```bash
    git clone https://github.com/Niloy190448/Traffic-Prediction-with-LSTM.git
    cd Traffic-Prediction-with-LSTM
    ```

2. Install dependencies:
    ```bash
    pip install tensorflow pandas numpy scikit-learn matplotlib
    ```

## Usage

1. **Prepare your dataset**: Ensure the dataset contains columns for `timestamp`, `traffic_count`, `temperature`, `rainfall`, `hour`, `day`, and `month`.

2. **Preprocess the data**: The script will preprocess the data, including:
   - One-hot encoding categorical features (`hour`, `day`, `month`).
   - Normalizing numerical features (`traffic_count`, `temperature`, etc.).
   - Filling or dropping missing values.

3. **Train the LSTM model**:
   - The model uses the last 24 hours of data to predict the traffic count for the next hour.
   
4. **Run the prediction**:
    ```bash
    python traffic_prediction_lstm.py
    ```

## Evaluation

The model performance is evaluated using **Mean Squared Error (MSE)**. The script plots:
- Actual vs predicted traffic counts.
- Training and validation loss curves.

## Results

After training, you can visualize the performance of the model:
- The predicted traffic counts are compared with the actual traffic counts in a graph.
- Loss curves show how well the model learned the traffic patterns over time.



---

## Acknowledgments

- Thanks to the authors of LSTM-related papers and tutorials that helped shape this implementation.
