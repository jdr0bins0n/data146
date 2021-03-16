*Download the dataset charleston_ask.csv and import it into your PyCharm project workspace. Specify and train a model the designates the asking price as your target variable and beds, baths and area (in square feet) as your features. Train and test your target and features using a linear regression model. Describe how your model performed. What were the training and testing scores you produced? How many folds did you assign when partitioning your training and testing data? Interpret and assess your output*


| average training score  | average testing score   |
| ----------------------- | ----------------------- |
| 0.019514638368913984    | -0.03750226784857269    |

As demonstrated above, my linear regression model performed very poorly. Both the training and testing scores hover around zero, indicating there is very little correlation between the features and variables. 
Futhermore the training and testing scores contradict each other. While the training score is postive, indicating that any correlation between the features and variables would be postitve, the testing score is negative, 
indicating that any correlation would be negative. 


*Now standardize your features (again beds, baths and area) prior to training and testing with a linear regression model (also again with asking price as your target). Now how did your model perform? What were the training and testing scores you produced? How many folds did you assign when partitioning your training and testing data? Interpret and assess your output.*


| average training score  | average testing score   |
| ----------------------- | ----------------------- |
| 0.019514638368913985    | -0.03750226784857236    |

Standardizing the data did not do much to improve the linear regression score. The mean training score did not change at all and the mean testing score changed by a few decimals. The mean testing and training scores still contradict one another in sign.


*Then train your dataset with the asking price as your target using a ridge regression model. Now how did your model perform? What were the training and testing scores you produced? Did you standardize the data? Interpret and assess your output.*

**Non-standardized* 

![](ridge_nonstand.png)

| Max training score      | Max testing score       |
| ----------------------- | ----------------------- |
|  0.01951463836891403    | -0.03309127535451182    |

When I ran a ridge regression model without standardizing the data both the testing and training data remained about the same, even when I attempted to narrow the range of the alpha value. The best alpha value appears to be around 250, which is when it starts to asymptote.

![](ridge_nonstand_2.png)

**Standardized**. 

![](ridge_stand.png)

| Max training score      | Max testing score       |
| ----------------------- | ----------------------- |
| 0.01758866117346013     | -0.0305934057550336     |

Standardizing the data to complete a ridge regression did not improve my training or testing scores, in fact it actually decreased both scores. The optimal alpha value hovered around 700 and asymptoted at that value. 

![](ridge_stand_2.png)

No matter how we manipulated the model the features bed, bath, and square footage did not appear to have any correlation with asking price in the Charleston area. Perhaps this is due to the asking price not being an accurate measure of how much a house may cost. I can imagine not many people are experienced in real estate and can give proper appraisals of their home value. They may ask for much higher or much lower than what their house is worth according to the number of beds, baths and square footage. With this in mind, it would make sense if the model performed rather poorly. It may benefit me to look at the actual sales price of the house and compare how well the features of the data can predict the target. 

*Next, go back, train and test each of the three previous model types/specifications, but this time use the dataset charleston_act.csv (actual sale prices). How did each of these three models perform after using the dataset that replaced asking price with the actual sale price? What were the training and testing scores you produced? Interpret and assess your output.*

**Linear regression**

*Non-Standardized* 

| Avg training score      | Avg testing score       |
| ----------------------- | ----------------------- |
|  0.019514638368913984   | -0.03750226784857269    |

*Standardized*

| Avg training score      | Avg testing score       |
| ----------------------- | ----------------------- |
| 0.01951463836891395     | -0.03750226784857236    |

The linear regression models, both standardized still did very poorly. Between the standardized and the non-standardized data, the testing and training scores improved by only a few decimals. This is an indicator that maybe the actual selling price may not be a better data set than the asking price. 

**Ridge regression**

*Non-Standardized* 

![](act_ridge.png)

| Max training score      | Max testing score       |
| ----------------------- | ----------------------- |
| 0.004454887667329488    | -0.05239617805135614    |

*Standardized*

| Max training score      | Max testing score       |
| ----------------------- | ----------------------- |
| 0.004454887667329477    | -0.04995418127915759    |

![](act_ridge_stand.png)

Similar to the linear regression model, the ridge regression model did not improve the training or testing scores and similar to the standardized ridge regression of the asking price data, the rige regression performed *more* poorly than a linear regression model.
In both cases, when I shrank the range of alpha values, centering it around the value that the range asymptoted at, the testing and training scores only improved marginally.

*Go back and also add the variables that indicate the zip code where each individual home is located within Charleston County, South Carolina. Train and test each of the three previous model types/specifications. What was the predictive power of each model? Interpret and assess your output.*

For this round of modeling I used the `charleston_act.csv` data. 

**Linear Regression**

*Non-Standardized*

| Avg training score      | Avg testing score       |
| ----------------------- | ----------------------- |
| 0.019514638368913984    | -0.03750226784857269    |

*Standardized*

| Avg training score      | Avg testing score       |
| ----------------------- | ----------------------- |
| 0.01951463836891395     | -0.03750226784857236    |

Despite adding zip code as one of our features, the model still performed poorly whether I standardized or did not standardize the data. 

**Ridge Regression**

*Non-Standardized*

| Max training score      | Max testing score       |
| ----------------------- | ----------------------- |
| 0.2182280696124602      | 0.3350645840919354      | 

*Standardized*

| Max training score      | Max testing score       |
| ----------------------- | ----------------------- |
| 0.20873750239990113     | 0.33752375664127515     | 

Adding the zip code feature and performing a ridge regression model significantly improved the testing and training scores. Not only are both scores greater than 0.0, but both test and training score are positive. This model is the first that displayed a consistency in correlation. While the correlation is still relatively weak (the model could only predict targets about a 3rd of the time, it is much better than the models generated before. I observed little difference between standardized and non-standardized data.

*Finally, consider the model that produced the best results. Would you estimate this model as being overfit or underfit? If you were working for Zillow as their chief data scientist, what action would you recommend in order to improve the predictive power of the model that produced your best results from the approximately 700 observations (716 asking / 660 actual)?*

The model that performed the best was the last model, which ran a ridge regression on the actual asking price, including zip code as a feature. I believe the model is neither underfit nor overfit, as the testing and training scores hovered between a 10% difference. The testing score was higher than the training score, which is an indicator of an underfit model, but I think the difference between the two scores is small enough to determine the model is not underfit.
If I were Zillow's chief data scientist, I would consider collecting different or more data to predict the price of a house. In addition to gathering more observations, it may be helpful to consider how other variables may affect the price of a house. As we have seen, the number of beds and baths and the square footage of a house are, alone, not good indicators of how a house may be appraised. Other indicators Zillow could consider is the age of the house. Much newer, modern houses and much older, antique-like houses may sell for much more than houses in the middle of the age range -- regardless of size, or number of bedrooms and bathrooms. Another feature Zillow could consider is location. I can imagine that houses closer to the city will sell for much more than houses located on the outskirts. 



