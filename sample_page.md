## Cisco

**Project description:** This is a predictive analytics using the capital asset pricing model (CAPM) which is a simple asset pricing model in finance. CAPM is a linear regression model.

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    CAPM Explanation
</head>
<body>
    <h1>Capital Asset Pricing Model (CAPM)</h1>
    <p>The capital asset pricing model (CAPM) is a simple asset pricing model in finance given by:</p>
    <p><strong>y<sub>i</sub> = β<sub>0</sub> + β<sub>1</sub>x<sub>i</sub> + e<sub>i</sub></strong></p>
    <p>where y<sub>i</sub> is a stock return and x<sub>i</sub> is a market return at time i.</p>
    <p>Some remarks are the following:</p>
    <ul>
        <li>β<sub>1</sub> measures the market-related (or systematic) risk of the stock.</li>
        <li>Market-related risk is unavoidable, while firm-specific risk may be 'diversified away' through hedging.</li>
        <li>Variance is a simple measure (and one of the most frequently-used) of risk in finance.</li>
    </ul>
</body>
</html>

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    
</head>
<body>
    <h1>Capital Asset Pricing Model, CAPM</h1>
    <p>I apply the simple linear regression model to study the relationship between two series of financial returns – a regression of Cisco Systems stock returns, y, on S&P500 index returns, x (CAPM).</p>
    <p>Stock returns are defined as:</p>
    <p><strong>return = (current price - previous price) / previous price ≈ log(current price / previous price)</strong></p>
    <p>when the difference between the two prices is small.</p>
    <p>The data file ‘Returns.csv’ contains daily observations over a January - 29 December 2000 (i.e., n=252 returns). The dataset has 5 columns: Day, S&P500 return, Cisco return, Intel return and Sprint return.</p>
</body>
</html>

<img src="images/IMG_8459.jpeg"/>

### 1. Suggest hypotheses about the causes of observed phenomena

Sales of 2Market products is driven by social media advertising. 

Sales growth is explained by sales of liquor.


### 2. Assess assumptions on which statistical inference will be based

Based on the data and hypothesis that sales of 2Market products is driven by social media advertising, I made five(5) assumptions about the data and variables. The following are the assumptions:

Linearity: The relationship between the predictor variable (Facebook, Instagram and Twitter) and the dependent variable (sales) is linear.

Scatter plot:

```
import matplotlib.pyplot as plt
plt.scatter(advertising_spend, sales)
plt.xlabel('Social Media Advertising Spend')
plt.ylabel('Sales')
plt.show()
```
Residual plot:
After fitting the regression model, plot residuals versus the fitted values.

```
plt.scatter(model.fittedvalues, model.residuals)
plt.xlabel('Fitted values')
plt.ylabel('Residuals')
plt.axhline(0, color='red', linestyle='--')
plt.show()
```
Independence: Observations are independent of each other.

Durbin-Watson Test

```
from statsmodels.stats.stattools import durbin_watson
dw = durbin_watson(model.residuals)
print(f'Durbin-Watson: {dw}')
```

Homoscedasticity: The variance of the residuals is constant across all levels of the predictor variable. This means there is no heteroscedasticity.

Residual Plot:
I used the same residual plot to check if residuals have constant variance.

```
plt.scatter(model.fittedvalues, model.residuals)
plt.xlabel('Fitted values')
plt.ylabel('Residuals')
plt.axhline(0, color='red', linestyle='--')
plt.show()
```
Breusch-Pagan Test:

```
from statsmodels.compat import lzip
from statsmodels.stats.diagnostic import het_breuschpagan
test_stat, p_value, _, _ = het_breuschpagan(model.residuals, model.model.exog)
print(f'Breusch-Pagan test stat: {test_stat}, p-value: {p_value}')
```

Normality: The residuals are normally distributed.

Histogram of Residuals:

```
plt.hist(model.residuals, bins=30)
plt.show()
```

Q-Q Plot:

```
import statsmodels.api as sm
sm.qqplot(model.residuals, line='45')
plt.show()
```

Shapiro-Wilk Test:

```
from scipy.stats import shapiro
stat, p = shapiro(model.residuals)
print(f'Statistic={stat}, p-value={p}')
```

No Multicollinearity: The predictor variables are not highly correlated (if there are multiple predictors). But correlation between each predictor variable and the dependent variable should be high. That is correlation between Facebook, Instagram and Twitter should be low but correlation between Facebook and sales, Instagram and sales, Twitter and sales should be high.

Variance Inflation Factor (VIF):

```
from statsmodels.stats.outliers_influence import variance_inflation_factor
vif = [variance_inflation_factor(X.values, i) for i in range(X.shape[1])]
print(f'VIF: {vif}')
```

Correlation Matrix:

```
import seaborn as sns
corr_matrix = X.corr()
sns.heatmap(corr_matrix, annot=True)
plt.show()
```

### 3. Support the selection of appropriate statistical tools and techniques
Based on the hypothesis and assumptions, I selected linear regression as the statistical tool and technique which will be used to assess whether sales of 2Market products is driven by social media advertising. The dependent variable is sales and the predictor variable is social media i.e. Facebook, Instagram and Twitter.

A simple linear regression model is given as below:

<img src="images/IMG_8459.jpeg"/>

Y is the dependent variable. For this analyses Y is sales.

X is predictor variable. For this analyses X is Facebook, Instagram and Twitter.

Bo is the intercept or the predicted value of sales (Y) when all of the predictor variable i.e. Facebook, Instagram and Twitter is equal to zero.

B1 is the slope coefficient or the amount of increase or decrease in sales when there is a unit (1) increase in either Facebook, Instagram or Twiitter advertising.

e is the error term (residuals).

### 4. Provide a basis for further data collection through surveys or experiments

Since the conclusion is that social media is the most effective form of advertising more than brochure (print) or e-mail channels, it will be of great benefit if data on which product type were bought through a particular social media channel is collected. Analysing this data will provide meaningful and actionable insight into which social media channel drives the sales of which product type so that targeted advertising can be deployed to drive sales and revenue even further. This approach will further aid the delivery of impactful analytics that provides real business value.

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).
