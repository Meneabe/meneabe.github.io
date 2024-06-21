## 2Market

**Project description:** 2Market is a global supermarket which sells products online and in store. 2Market wants to understand their customer purchase behaviour. In particular, 2Market wants to understand the demographics of their customers, which advertising channels seem to be the most effective, which products seem to sell the best and if that varies based on demographic.

This insight into 2Market customer purchase behaviour will enable 2Market to target the right customer segment and market to each group effectively and appropriately. Insight into the most effective advertising channel will enable 2Market to efficiently allocate resources to advertising. The cost or impact of not knowing 2Market customer purchase behaviour is losing customers to competitors which will impact 2Market’s bottom-line.
.

### 1. Suggest hypotheses about the causes of observed phenomena

Sales of 2Market products is driven by social media advertising. 

Sales growth is explained by sales of liquor.


### 2. Assess assumptions on which statistical inference will be based

Based on the data and hypothesis that sales of 2Market products is driven by social media advertising, I made five(5) assumptions about the data and variables. The following are the assumptions:

Linearity: The relationship between the independent variable (Facebook, Instagram and Twitter) and the dependent variable (sales) is linear.

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

Homoscedasticity: The variance of the residuals is constant across all levels of the independent variable.

Residual Plot:
Use the same residual plot to check if residuals have constant variance.

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

No Multicollinearity: The independent variables are not highly correlated (if there are multiple predictors).

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

<img src="images/dummy_thumbnail.jpg?raw=true"/>

### 4. Provide a basis for further data collection through surveys or experiments

Sed ut perspiciatis unde omnis iste natus error sit voluptatem accusantium doloremque laudantium, totam rem aperiam, eaque ipsa quae ab illo inventore veritatis et quasi architecto beatae vitae dicta sunt explicabo. 

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).
