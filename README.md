# Forecasting supply chain costs: Time-series modelling using ARIMA
I spent a semester working as a Student Data Scientist at Apple. This is the project that I worked on, which resulted in cost savings of $20 million yearly.
- Designed desktop application that uses ARIMA models to detect cost errors.
- Created interactive Tableau dashboards depicting costs across components and time.
 
 
## Motivation
Apple purchases components parts for its products from third party suppliers. The prices of these parts can be volatile at times due to trends and seasonalities, which snowballs into significant supply chain cost impacts.

This project uses time-series modelling to predict a reasonable cost range for hundreds of parts in each month, and is used to flag warnings when the true cost of a part is outside of this range. This information can then be used for price negotiations with part suppliers.


## Results: <0.1% Mean Absolute Percentage Error
These models work in the back-end of the desktop application:
<img src="readme_images/desktop_application.png" width="1000">


## Data
Cost that Apple paid for each component part in each month. The data covers 768 component parts across multiple years.


## Methodology
1. Remove outliers in data to discard noise. Next, simulate data for component parts with lesser cost history data using a normal distribution with the same mean and variance as the available data.
<img src="readme_images/data_simulation.png" width="1000">

2. Build one ARIMA model for each component part's cost. As such, 768 models are trained. For each model, grid search for its optimal ARIMA (p, d, q) hyperparameters, determined by lowest MAPE on left-out test set.

3. When predicting the cost of a component part for the next month, apart from simply outputting cost predictions, calculate a 95% confidence interval for the prediction. This serves as a reasonable cost range for the part. Below is a graphical illustration, where the cost range is shown as a shaded grey area
<img src="readme_images/prediction.png" width="1000">




