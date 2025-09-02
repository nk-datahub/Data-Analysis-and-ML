# Uber Eats Delivery Time Analysis and Prediction

This project analyzes Uber Eats delivery data to understand delivery time patterns, identify key factors affecting delivery speed, and build predictive models to estimate delivery times. 

## Project Overview
The goal of this project is to:  
- Analyze Uber Eats delivery times across different cities, traffic conditions, weather, and driver characteristics.  
- Identify factors that impact delivery performance.  
- Build predictive models using machine learning (Linear Regression, Random Forest, Gradient Boosting) to estimate delivery times for new orders.  

## Dataset
The dataset used for this project is `uber-eats-sample.csv`. It contains 45,593 delivery records with the following columns:  

- `ID` – Unique identifier for each order  
- `Delivery_person_ID` – Unique ID for each delivery person  
- `Delivery_person_Age` – Age of delivery person  
- `Delivery_person_Ratings` – Ratings given to the delivery person  
- `Restaurant_latitude` & `Restaurant_longitude` – Restaurant location  
- `Delivery_location_latitude` & `Delivery_location_longitude` – Delivery location  
- `Order_Date` – Date of the order  
- `Time_Orderd` & `Time_Order_picked` – Order and pickup timestamps  
- `Weatherconditions` – Weather during delivery  
- `Road_traffic_density` – Traffic condition (Low, Medium, High, Jam)  
- `Vehicle_condition` – Condition of delivery vehicle  
- `Type_of_order` – Type of order (Snack, Buffet, Drinks, etc.)  
- `Type_of_vehicle` – Vehicle used for delivery  
- `multiple_deliveries` – Number of deliveries in a single trip  
- `Festival` – Whether the delivery was during a festival  
- `City` – City type (Urban, Metropolitan, Semi-Urban)  
- `Time_taken(min)` – Delivery time in minutes  
- `Distance_km` – Calculated distance between restaurant and delivery location  

## Data Cleaning & Preprocessing
Key steps in data cleaning:  
1. Removed "min" from `Time_taken(min)` and converted it to numeric.  
2. Converted `Delivery_person_Age` and `Delivery_person_Ratings` to numeric.  
3. Converted `Order_Date`, `Time_Orderd`, and `Time_Order_picked` to datetime objects.  
4. Cleaned categorical columns: stripped spaces, removed prefixes in `Weatherconditions`.  
5. Calculated `Distance_km` using the Haversine formula.  
6. Handled missing values in `multiple_deliveries`, `Road_traffic_density`, `Weatherconditions`, and `City`.  

## Exploratory Data Analysis (EDA)
- **Delivery Time Distribution:** Most deliveries occur between 15–35 minutes, with a peak around 27–28 minutes.  
- **Impact of Traffic:** High and jammed traffic significantly increases delivery times.  
- **Impact of Weather:** Cloudy, foggy, stormy, and sandstorm conditions slightly increase delivery times.  
- **City-wise Analysis:** Metropolitan cities have higher average delivery times compared to Urban and Semi-Urban areas.  
- **Correlation Analysis:**  
  - Older delivery persons tend to take slightly longer.  
  - Higher-rated drivers deliver faster.  
  - Multiple deliveries increase delivery time.  
  - Vehicle condition has a minor effect.  

## Predictive Modeling

### Linear Regression
- Used numeric features: `Delivery_person_Age`, `Delivery_person_Ratings`, `multiple_deliveries`, `Distance_km`, `Vehicle_condition`.  
- Performance:  
  - MAE: 6.14 min  
  - RMSE: 7.73 min  
  - R²: 0.33  

### Random Forest Regression
- Used numeric + categorical features (one-hot encoded):  
  - Categorical: `Road_traffic_density`, `Weatherconditions`, `Type_of_order`, `Type_of_vehicle`, `City`, `Festival`  
- Performance:  
  - MAE: 3.14 min  
  - RMSE: 3.94 min  
  - R²: 0.83  
- Feature importance: traffic, multiple deliveries, and vehicle condition were key predictors.  

### Gradient Boosting Regression
- Slightly worse performance compared to Random Forest:  
  - MAE: 3.48 min  
  - RMSE: 4.34 min  
  - R²: 0.83  

**Conclusion:** Random Forest effectively captures non-linear relationships in delivery time prediction.  

## Key Insights
1. Most deliveries are completed in 25–30 minutes, with outliers above 45 minutes needing attention.  
2. Traffic density and weather significantly affect delivery times.  
3. City type influences delivery efficiency, suggesting potential for geo-targeted optimization.  
4. Multiple deliveries and vehicle condition are strong predictors for delivery time.  

## Technologies Used
- Python (pandas, numpy, matplotlib, seaborn)  
- Machine Learning: scikit-learn (Linear Regression, Random Forest, Gradient Boosting)  
- Data Visualization: Matplotlib, Seaborn  

## Future Work
- Integrate real-time traffic and weather data for dynamic ETA prediction.  
- Explore advanced deep learning models for improved prediction accuracy.  
- Optimize delivery routes using geographic clustering and vehicle routing algorithms.  
