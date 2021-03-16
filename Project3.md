**Download the dataset charleston_ask.csv and import it into your PyCharm project workspace. Specify and train a model the designates the asking price as your target variable and beds, baths and area (in square feet) as your features. Train and test your target and features using a linear regression model. Describe how your model performed. What were the training and testing scores you produced? How many folds did you assign when partitioning your training and testing data? Interpret and assess your output.**

I produced a training score of 0.019, and a testing score of -0.014. To get this, I assigned 10 folds. Overall, the results were very poor. This is because the r-squared value is far from 1. It leads me to believe that the connection between these variables and the house asking price is somewhat limited.
 
**Now standardize your features (again beds, baths and area) prior to training and testing with a linear regression model (also again with asking price as your target). Now how did your model perform? What were the training and testing scores you produced? How many folds did you assign when partitioning your training and testing data? Interpret and assess your output.**

After standardization, my training score was 0.019, and my testing score was -0.026. This model still performed quite poorly. I assigned 10 folds. 
Then train your dataset with the asking price as your target using a ridge regression model. Now how did your model perform? What were the training and testing scores you produced? Did you standardize the data? Interpret and assess your output.
After doing so, the training score I got was 0.019, and the testing score was 0.011. The model still performed quite poorly. I used 10 folds, and I standardized the data.
 
**Next, go back, train and test each of the three previous model types/specifications, but this time use the dataset charleston_act.csv (actual sale prices). How did each of these three models perform after using the dataset that replaced asking price with the actual sale price? What were the training and testing scores you produced? Interpret and assess your output.**

Linear Regression Model:
The training score was 0.005 and the testing score was -0.015, with 10 folds. 
 
Linear Regression Model after standardization:
The training score was 0.004 and the testing score was -0.022, with 10 folds. 
 
Standardized data in the ridge regression model:
The training score was 0.004 and the testing score was -0.006, with 10 folds.
 
Looking at this output, it appears that the models were not really any better with the Charleston_act.csv data as opposed to the Charleston_ask.csv data. They remain very far away from 1. This is likely because the variables we have used for this model are not very good indicators of price on their own.
 
**Go back and also add the variables that indicate the zip code where each individual home is located within Charleston County, South Carolina. Train and test each of the three previous model types/specifications. What was the predictive power of each model? Interpret and assess your output.**

Charleston_ask:
 
Linear Regression Model:
The training score was 0.281 and the testing score was  0.113, with 10 folds. 
 
Linear Regression Model after standardization:
The training score was 0.282 and the testing score was 0.180, with 10 folds. 
 
Standardized data in the ridge regression model:
The training score was 0.281 and the testing score was 0.269, with 10 folds.
 
 
Charleston_act:
 
Linear Regression Model:
The training score was 0.339 and the testing score was 0.273, with 10 folds. 
 
Linear Regression Model after standardization:
The training score was 0.339 and the testing score was 0.231, with 10 folds. 
 
Standardized data in the ridge regression model:
The training score was 0.335 and the testing score was 0.286, with 10 folds.
 
Looking at this output, it appears as though the training and testing scores had improved quite a bit after adding the zip codes, and were much closer to 1. I suspect this is because zipcodes are a very good indicator of house price, as houses of the close together tend to have similar values.
 
 
 
**Finally, consider the model that produced the best results. Would you estimate this model as being overfit or underfit? If you were working for Zillow as their chief data scientist, what action would you recommend in order to improve the predictive power of the model that produced your best results from the approximately 700 observations (716 asking / 660 actual)?**

I would estimate this model as being overfit, as it has a training score that is higher than its testing score. I would recommend they use the standardized data in the ridge regression model, after having included zip codes. To improve the predictive power of the model, I would suggest using more variables for these homes. This is because, while I think zipcodes are a powerful predictor, having many more predictors could be quite valuable, and there might be other predictors whose weight in determining house value that might come as a surprise.
