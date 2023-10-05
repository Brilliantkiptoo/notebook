# notebook/prediction1
# Load your trained model 
rf_modelmodel = joblib.load('best_random_forest_model.pkl')

@app.route('/predict', methods=['POST'])
def predict_sales():
    try:
        # Get input data from JSON request
        data = request.get_json()

        # Prepare input data (must match the features used for training)
        input_features = [data['sell_price'], data['lag_1_sales'], data['lag_2_sales'],
                          data['lag_3_sales'], data['day_of_week'], data['is_weekend'],
                          data['event_indicator']]

        # Make a prediction using the loaded model
        predicted_sales = model.predict([input_features])[0]

        # Create a response JSON
        response = {'predicted_sales': predicted_sales}

        return jsonify(response)

    except Exception as e:
        return jsonify({'error': str(e)})

if __name__ == '__main__':
    app.run(debug=True)
