<h2 class="text-uppercase">Forecasting<br>supply chain costs</h2>
<h3 class="text-warning">Time-series modelling using ARIMA</h3>
<p class="item-intro text-muted">Designed desktop application that uses ARIMA models to detect cost errors.<br>Created interactive Tableau dashboards depicting costs across components and time.</p>
<br>

<h3 style="text-align:left;">Motivation</h3>
    <p style="text-align:justify;">Apple purchases components parts for its products from third party suppliers. The prices of these parts can be volatile at times due to trends and seasonalities, which snowballs into significant supply chain cost impacts.<br><br>This project uses time-series modelling to predict a reasonable cost range for hundreds of parts in each month, and is used to flag warnings when the true cost of a part is outside of this range. This information can then be used for price negotiations with part suppliers.</p>
<br>

<h3 style="text-align:left;">Results: <0.1% Mean Absolute Percentage Error</h3>
<p style="text-align:left;">These models work in the back-end of the desktop application: </p>>
<img class="img-fluid" src="assets/images/portfolio/apple/desktop_application.png">
<br>

<h3 style="text-align:left;">Data</h3>
    <p style="text-align:justify;">Cost that Apple paid for each component part in each month. The data covers 768 component parts across multiple years.
<br>
<br>

<h3 style="text-align:left;">Methodology</h3>
    <p style="text-align:justify;">1. Remove outliers in data to discard noise. Next, simulate data for component parts with lesser cost history data using a normal distribution with the same mean and variance as the available data.</p>
    <img class="img-fluid" src="assets/images/portfolio/apple/data_simulation.png">

    <p style="text-align:justify;">2. Build one ARIMA model for each component part's cost. As such, 768 models are trained. For each model, grid search for its optimal ARIMA (p, d, q) hyperparameters, determined by lowest MAPE on left-out test set.</p>

    <p style="text-align:justify;">3. When predicting the cost of a component part for the next month, apart from simply outputting cost predictions, calculate a 95% confidence interval for the prediction. This serves as a reasonable cost range for the part. Below is a graphical illustration, where the cost range is shown as a shaded grey area.</p>
    <img class="img-fluid" src="assets/images/portfolio/apple/prediction.png">
