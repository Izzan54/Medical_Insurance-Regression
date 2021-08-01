# Medical_Insurance-Regression
* The medical insurance cost dataset had 7 variables (age, sex, BMI, children, smoker, region, and charges). We wanted to predict the cost of medical insurance using regression models.
* First, we imported the dataset and checked the shape of the data. We had 1338 rows and 7 columns. The target column was the charges.
* We checked and removed the null values.
## Explored the data

* We plotted the categorical variables using the pie charts:

![Image of cost](https://github.com/Izzan54/Medical_Insurance-Regression/blob/main/gender.png)
![Image of cost](https://github.com/Izzan54/Medical_Insurance-Regression/blob/main/smoker.png)
![Image of cost](https://github.com/Izzan54/Medical_Insurance-Regression/blob/main/region.png)

* The percentage of males and females who took medical insurance was almost the same.
* Mostly the beneficiaries came from non-smokers.
* The percentage of beneficiaries from southeast, southwest, northwest, and northeast were almost the same.
* We plotted the boxplot to observe insurance charge between males and females who were smokers.

![Image of cost](https://github.com/Izzan54/Medical_Insurance-Regression/blob/main/gender_smoker.png)

* We could see from the boxplot above, the females and males who were smokers had the higher insurance charge compared who did not smoke.
* Next, we would like to see the insurance charge of the beneficiaries from the different regions with the number of children.

![Image of cost](https://github.com/Izzan54/Medical_Insurance-Regression/blob/main/region_children.png)

* From the bar graph above, the beneficiaries from the southwest who had 2 children got higher insurance charges. Meanwhile, the beneficiaries from southeast and northwest who had 3 children got higher insurance charges. In the northeast, the beneficiaries who had only a child got high insurance charges
* We also wanted to observe the insurance charge of the smoker from the different regions.

![Image of cost](https://github.com/Izzan54/Medical_Insurance-Regression/blob/main/region_smoker.png)

* We The smokers from all regions had the higher compared to non-smokers.
* Then, we created the scatter plot to observe the relationship insurance charge with BMI. We separated them by gender and smoker.

![Image of cost](https://github.com/Izzan54/Medical_Insurance-Regression/blob/main/bmi_smoker.png)

* We could see from the scatter plot above, the BMI of smokers had a linear relationship with insurance charges regardless of their gender.
* Then, we tried to substitute BMI with age and plotted the scatter plot.

![Image of cost](https://github.com/Izzan54/Medical_Insurance-Regression/blob/main/age_smoker.png)

* We could see that the age of the smokers and non-smokers had relation to insurance charges regardless of their gender.
* Next, we wanted to class the BMI of the beneficiaries into normal, overweight, underweight and obese.

![Image of cost](https://github.com/Izzan54/Medical_Insurance-Regression/blob/main/bmi_binned.png)

* When we calculated the percentage of each group, 55.16% of the beneficiaries had normal BMI and only 2.17% had fall within the obese range.
* The distribution of the insurance charges were skewed to left. The charges fell toward the lower side of the scale and there were very few higher charges. We tried to do log-transformation of charge.

![Image of cost](https://github.com/Izzan54/Medical_Insurance-Regression/blob/main/distribution_charge.png)
![Image of cost](https://github.com/Izzan54/Medical_Insurance-Regression/blob/main/normal_charge.png)

* Lastly, we tried to look at the correlation between continuous variables.

![Image of cost](https://github.com/Izzan54/Medical_Insurance-Regression/blob/main/correlation.png)

* We could see that insurance charges correlated with BMI and age.


## Linear Regression

We would try to predict the insurance charge using the linear regression model. We changed the categorical variables to dummy variables and scaled the continuous variables using a standard scaler. Then, we visualized the model coefficients:

![Image of cost](https://github.com/Izzan54/Medical_Insurance-Regression/blob/main/model_coefficients.png)

The variables showed the positive effects on the linear regression model for predicting insurance charges:
* smoker_yes
* bmi
* age
* children_4
* children_2
* region_northeast
* region_northwest
* children_5
* sex_female

The variables showed the negative effects on the linear regression model for predicting insurance charges:
* smoker_no
* children_1
* children_0
* region_southeast
* region_southwest
* children_3
* sex_male


## Ridge Regression
we searched for the best alpha using grid search. The best alpha equaled 1. The alpha of 1, would result in a model that acts identical to Linear Regression. Thus, we tried the ridge regression model with alpha = 0.7.

## Polynomial Regression
We predict insurance charge using the selected features. We selected the features using Random Forest Regressor.

![Image of cost](https://github.com/Izzan54/Medical_Insurance-Regression/blob/main/Random_Forest.png)

Then, we only top 5 features which were 'smoker_no','smoker_yes','bmi','age' and 'children_0'. We tried created polynomial regression with degree 2, 3 and 4.

## The accuracy of the regression models

1) Linear Regression
* R squared score: 0.6496611914532804
* Mean squared error (MSE) : 0.25335813291783815

3) Ridge Regression (alpha = 0.7)
* R squared score: 0.6482708600881282
* Mean squared error (MSE) : 0.25332132906483074

5) Polynomial Regression

*degree = 2
* R squared score: 0.8559520456247791
* Mean squared error (MSE) : 0.13728797257694678

*degree = 3
* R squared score: 0.8292164810582233
* Mean squared error (MSE) : 0.17283247409806135

*degree = 4
* R squared score: 0.8641466272209819
* Mean squared error (MSE) : 0.13708950227978367

If we compared all regression models, we chose polynomial regression degree = 4 as the best model to predict medical insurance cost.
The feature 'smoker' was the most affecting the insurance cost. Thus, the smokers likely had to pay more on the medical insurance cost. This prediction task was suitable for me as a beginner of medical insurance to calculate the insurance cost.



