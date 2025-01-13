Traffic Prediction Using LSTM
This project implements traffic demand forecasting using a Long Short-Term Memory (LSTM) model. The model predicts traffic counts based on historical traffic data along with additional features such as weather data, hour of the day, day of the week, and month. The goal is to build a robust time series forecasting model to help transportation planners predict future traffic volumes for better planning and optimization.

Features:
Predict future traffic demand using past traffic counts and weather data.
Incorporate temporal features like hour, day of the week, and month.
Use LSTM (Long Short-Term Memory) for sequential prediction.
Implement data preprocessing (scaling, one-hot encoding, handling missing values).
Visualize results (actual vs. predicted traffic) and model performance (training and validation loss).
Table of Contents:
Requirements
Data Description
Installation
Usage
Results
License
Requirements
Before you can run this project, make sure you have the following libraries installed:

Python 3.x
TensorFlow >= 2.x
Pandas
NumPy
Matplotlib
scikit-learn
You can install the required packages using the following commands:

bash
Copy code
pip install tensorflow pandas numpy matplotlib scikit-learn
Data Description
The dataset should contain historical traffic demand data along with additional features such as weather data. The dataset should have the following columns:

timestamp: Date and time of the observation.
traffic_count: Traffic demand (vehicle count) at a specific time.
temperature: Temperature at the time of observation.
rainfall: Amount of rainfall at the time of observation.
hour: The hour of the day (0 to 23).
day: The day of the week (0 to 6, where 0 = Monday).
month: The month of the year (1 to 12).
Example CSV structure:
timestamp	traffic_count	temperature	rainfall	hour	day	month
2023-01-01 00:00:00	150	22.1	0.0	0	0	1
2023-01-01 01:00:00	130	21.8	0.1	1	0	1
2023-01-01 02:00:00	120	21.5	0.2	2	0	1
The dataset should be saved as a CSV file (e.g., advanced_travel_demand.csv).

Installation
Clone this repository to your local machine:

bash
Copy code
git clone https://github.com/yourusername/traffic-prediction-lstm.git
cd traffic-prediction-lstm
Install the dependencies (as mentioned in the Requirements section):

bash
Copy code
pip install tensorflow pandas numpy matplotlib scikit-learn
Make sure you have your traffic data CSV file (advanced_travel_demand.csv) in the project directory.

Usage
Once the environment is set up, you can run the code to train and evaluate the LSTM model for traffic prediction.

Run the Jupyter notebook or Python script:

Open the notebook in Jupyter and execute the code, or run the script directly.
bash
Copy code
python traffic_prediction_lstm.py
Data Preprocessing:

The script will load the traffic data and perform preprocessing steps:
One-hot encoding for the day of the week.
Scaling numeric features such as traffic counts, temperature, and rainfall using MinMaxScaler.
Handling missing values by forward filling (ffill).
Model Training:

The LSTM model is trained with the past 24 hours of data to predict future traffic counts.
The model includes an LSTM layer, a Dropout layer to prevent overfitting, and a Dense layer for output.
Training uses early stopping to stop the process once the model stops improving.
Model Evaluation:

After training, the model’s predictions are compared against actual traffic counts from the test set.
The results are visualized as a line plot showing actual vs. predicted traffic demand.
The model's performance is evaluated using Mean Squared Error (MSE).
Future Prediction:

The model can predict the traffic demand for the next hour based on the last 24 hours of data.
Example Code:
python
Copy code
# Load dataset and preprocess
df = pd.read_csv("advanced_travel_demand.csv", parse_dates=["timestamp"], index_col="timestamp")

# Preprocessing: Feature engineering and scaling
# (steps outlined in the code)

# Train the LSTM model
model.fit(X_train, y_train, epochs=50, batch_size=32, validation_data=(X_test, y_test))

# Evaluate and visualize results
y_pred = model.predict(X_test)
plt.plot(df.index[-len(y_test):], y_test_rescaled, label="Actual Traffic Demand")
plt.plot(df.index[-len(y_test):], y_pred_rescaled, label="Predicted Traffic Demand", linestyle='--')
plt.show()
Results
Once the model is trained and evaluated, you'll see the following:

Prediction Visualization: A graph comparing actual and predicted traffic counts.
Training History: A plot showing the model's loss over epochs during training.
Mean Squared Error: The model’s performance metric to assess the prediction accuracy.
License
This project is licensed under the MIT License - see the LICENSE file for details.
