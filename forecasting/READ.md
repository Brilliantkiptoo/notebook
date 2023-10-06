# Sales Forecasting API

This repository contains the code for a sales forecasting API developed using SARIMA model. The model is trained on historical sales data and can forecast future sales based on the learned patterns.

## 📊 Model Overview
- **Model**: Seasonal Autoregressive Integrated Moving Average (SARIMA)
- **Data**: Daily sales data featuring various aspects like item sales, store sales, and event indicators.
- **Forecast**: Capable of forecasting daily sales for a specified period.

## 🚀 API Usage
The Flask API is simple to use and returns a sales forecast for a given period.

### API Endpoint:
- **Forecast Sales**: 
  - **Endpoint**: `/forecast`
  - **Method**: `POST`
  - **Data**: 
    ```json
    {
      "start_date": "YYYY-MM-DD",
      "forecast_period": integer
    }
    ```
  - **Response**:
    ```json
    {
      "start_date": "YYYY-MM-DD",
      "forecast_period": integer,
      "forecasted_sales": [array_of_sales]
    }
    ```
## 💼 Project Structure
- `model_training.py`: Script for training the SARIMA model and saving it.
- `api.py`: Flask API to serve the trained model.
- `pretrained_sarima_model.pkl`: Serialized pre-trained SARIMA model.

## 🛠️ Setup & Installations
1. Clone the repository:
   ```sh
   git clone [repo-link]

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
