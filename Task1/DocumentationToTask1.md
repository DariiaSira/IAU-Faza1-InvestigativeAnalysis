**(1b) Dokumentujte Vaše prvotné zamyslenie k riešeniu zadania projektu, napr. sú niektoré atribúty medzi sebou závislé? 
  od ktorých atribútov závisí predikovaná premenná? 
  či sa dá kombinovať záznamy z viacerých súborov? 
  či je potrebné ich kombinovať?**


When starting this project, it was important for me to do some initial data analysis and make sense of the data. To do this, I asked myself several questions:

**1) Attribute dependencies**
    I wondered if there were any dependencies between attributes. For example, I wanted to know if there was any dependency between the attributes         '_session_duration_' and '_total_load_time_'. To do this, I used correlation analysis.

**2) Predictive variable**
    I was interested in which attributes the predicted variable depends on. In this case, it is 'session_duration'. I wanted to understand which attributes could affect the session duration.

**3) Data merging**
    I was also interested in understanding if data from multiple files could be merged. In my case, I was working with 'user', 'session' and 'product' tables. I looked into the possibility of merging the data for analysis.

_For example:_

To analyze the dependencies between the '_session_duration_' and '_total_load_time_' attributes, I used:
```
print("Pearson correlation: %.3f" % session.session_duration.corr(session.total_load_time))
```
This allowed me to determine the degree of correlation between the two attributes.

To identify which attributes might be influencing '_session_duration_', I used linear regression. Sample code:
```
# Create a linear regression model
model = LinearRegression()

# Fitting the model to the data
model.fit(X, y)

# Getting coefficients and intercepts
coefficients = model.coef_
intercept = model.intercept_
```

I analyzed the possibility of merging data from the 'user' and 'session' tables using code:
```
grouped = user.join(session, how='outer', lsuffix='_', rsuffix='_')
```

This code helped me merge the data from both tables for a more complete analysis.

To sum up, I started by analyzing the structure of the data, examining the dependencies between attributes, and determining the effect of the attributes on the predicted variable.
