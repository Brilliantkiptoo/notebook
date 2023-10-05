from flask import Flask, request, jsonify
from statsmodels.tsa.statespace.sarimax import SARIMAX
import pandas as pd
import joblib

app = Flask(__name__)

# Load your pre-trained SARIMA model
model = joblib.load('pretrained_sarima_model.pkl')

@app.route('/forecast', methods=['POST'])
def forecast_sales():
    try:
        # Get input data from JSON request
        data = request.get_json()

        # Assuming the input contains the start date and forecast period
        start_date = pd.to_datetime(data['start_date'])
        forecast_period = int(data['forecast_period'])

        # Generate forecasts for the specified period
        forecast = model.get_forecast(steps=forecast_period, start=start_date)

        # Get the forecasted sales values
        forecasted_sales = forecast.predicted_mean

        # Convert the forecasted sales to a dictionary for response
        forecast_dict = {'start_date': start_date.strftime('%Y-%m-%d'),
                         'forecast_period': forecast_period,
                         'forecasted_sales': forecasted_sales.tolist()}

        return jsonify(forecast_dict)

    except Exception as e:
        return jsonify({'error': str(e)})

if __name__ == '__main__':
    app.run(debug=True, port=8080, use_reloader=False)
