# Model Building, Evaluation and Validation
## Project:  Car-price-prediction
In the jupyter file  the code explanation  written in Armenian.
### Install

This project requires **Python** and the following Python libraries installed:

- [NumPy](http://www.numpy.org/)
- [Pandas](http://pandas.pydata.org/)
- [matplotlib](http://matplotlib.org/)
- [scikit-learn](http://scikit-learn.org/stable/)

You will also need to have software installed to run and execute a [Jupyter Notebook](http://jupyter.org/install.html).

If you do not have Python installed yet, it is highly recommended that you install the [Anaconda](https://www.anaconda.com/download/) distribution of Python, which already has the above packages and more included. 

### Code

Template code is provided in the `car_price_prediction.ipynb` notebook file. You will also be required to use the included `car_price_prediction.ipynb` Jupyter Notebook  file and the `CarPrice_Assignment.csv` dataset file to complete your work.

### Run

In a terminal or command window, navigate to the top-level project directory `car_price_prediction/` (that contains this README) and run one of the following commands:
```bash
ipython notebook car_price_prediction.ipynb
```  
or
```bash
jupyter notebook car_price_prediction.ipynb
```
or open with Juoyter Lab
```bash
jupyter lab
```

This will open the Jupyter Notebook software and project file in your browser.
### Business Goal
We are required to model the price of cars with the available independent variables.
It will be used by management to understand exactly how prices vary with the independent variables. They can manipulate car design, business strategy and other features accordingly to match a certain price level. 
The model will be a good way for management to understand the pricing dynamics of a new market.

### Data
The CarPrice_Assignment.csv dataset consists of (205, 26) row & columns.

<class 'pandas.core.frame.DataFrame'>
RangeIndex: 205 entries, 0 to 204
Data columns (total 26 columns):
 #   Column            Non-Null Count  Dtype  
---  ------            --------------  -----  
 0   car_ID            205 non-null    int64  
 1   symboling         205 non-null    int64  
 2   CarName           205 non-null    object 
 3   fueltype          205 non-null    object 
 4   aspiration        205 non-null    object 
 5   doornumber        205 non-null    object 
 6   carbody           205 non-null    object 
 7   drivewheel        205 non-null    object 
 8   enginelocation    205 non-null    object 
 9   wheelbase         205 non-null    float64
 10  carlength         205 non-null    float64
 11  carwidth          205 non-null    float64
 12  carheight         205 non-null    float64
 13  curbweight        205 non-null    int64  
 14  enginetype        205 non-null    object 
 15  cylindernumber    205 non-null    object 
 16  enginesize        205 non-null    int64  
 17  fuelsystem        205 non-null    object 
 18  boreratio         205 non-null    float64
 19  stroke            205 non-null    float64
 20  compressionratio  205 non-null    float64
 21  horsepower        205 non-null    int64  
 22  peakrpm           205 non-null    int64  
 23  citympg           205 non-null    int64  
 24  highwaympg        205 non-null    int64  
 25  price             205 non-null    float64
dtypes: float64(8), int64(8), object(10)
memory usage: 41.8+ KB

From above you can see that data contains 10 class(object) and 8 numeric(float & int) attributes.I have done Data Cleaning and Preparation (see `car_price_prediction/` ).

**Features**
  ` car_ID `,`symboling`,`CarName`,`fueltype`,`aspiration`,`doornumber`,`carbody`,`drivewheel`,`enginelocation`,`cylindernumber`,`enginesize`,`cylindernumber`,`enginesize`,`fuelsystem`,`boreratio`,`stroke`,`compressionration`,`horsepower`,`peakrpm`,`citympg`,`highwaympg `.
 

**Target Variable**
4. `Price`

This type of analysis helps businesses make informed decisions about how to allocate their advertising budgets for maximum sales impact.
The detailed comments about the output examples  on each step you can find in the `FutureSalesPrediction.ipynb` notebook file.

# The results of  model: accuracy and prediction for the given project

RFE was used to build the model. RFE stands for Recursive Feature Elimination. It is a feature selection algorithm used to select a subset of features from a database. RFE works by successively removing the least important features from the dataset and retraining the model. The process is repeated until the desired number of features is reached.
(from sklearn.feature_selection import RFE)
## Summary
   OLS Regression Results                            
==============================================================================
Dep. Variable:                  price   R-squared:                       0.899
Model:                            OLS   Adj. R-squared:                  0.896
Method:                 Least Squares   F-statistic:                     308.0
Date:                Fri, 26 Apr 2019   Prob (F-statistic):           1.04e-67
Time:                        09:01:43   Log-Likelihood:                 181.06
No. Observations:                 143   AIC:                            -352.1
Df Residuals:                     138   BIC:                            -337.3
Df Model:                           4                                         
Covariance Type:            nonrobust                                         
==============================================================================
                 coef    std err          t      P>|t|      [0.025      0.975]
------------------------------------------------------------------------------
const         -0.0824      0.018     -4.480      0.000      -0.119      -0.046
horsepower     0.4402      0.052      8.390      0.000       0.336       0.544
carwidth       0.3957      0.046      8.677      0.000       0.306       0.486
hatchback     -0.0414      0.013     -3.219      0.002      -0.067      -0.016
Highend        0.2794      0.022     12.591      0.000       0.236       0.323
==============================================================================
Omnibus:                       29.385   Durbin-Watson:                   1.955
Prob(Omnibus):                  0.000   Jarque-Bera (JB):               98.010
Skew:                           0.692   Prob(JB):                     5.22e-22
Kurtosis:                       6.812   Cond. No.                         12.9
==============================================================================

1.  `R-squared and adjusted R-squared :`- 0.899 and 0.896 - at "90%" the model predicts accurately.
2. `F-stats and Prob(F-stats) (overall model fit)` - 308.0 and 1.04e-67 (approx. 0.0) - Model is significant and the explained "90%" accuracy is not random.
3. `p-values` - p-values for all coefficients are less than the 0.05 significance level, meaning that all predictors are statistically significant.
4. The relationship between the independent variables and the dependent variable is `linear`. This assumption is supported by a high R-squared value indicating that the model fits the data well. 
5. `Homoscedasticity.`The variance of the residuals is constant across all values of the independent variables. This assumption is confirmed by the Durbin-Watson statistic, which is close to 2.
6. `Normality.` the residuals are normally distributed. This assumption confirms the Jarque-Bera statistic (the Jarque-Bera test statistic is always positive, and if it is not close to zero, it indicates that the sample data does not have a normal distribution.)
7. `Independence.` the residues are independent of each other. This assumption is supported by the absence of autocorrelation in the residuals.

However, there are some potential problems with the model
Multicollinearity. Independent variables are correlated with each other. This can cause problems with the standard errors of the coefficients, making them unreliable. There may be outliers in the data. Outliers can affect model fit and standard errors of coefficients. It is important to investigate these issues before using the model to make predictions.


### Have questions, contact me.
[![LinkedIn](https://img.shields.io/static/v1.svg?label=connect&message=@monica-avagyan&color=success&logo=linkedin&style=flat&logoColor=white&colorA=blue)](https://www.linkedin.com/in/monica-avagyan/)
