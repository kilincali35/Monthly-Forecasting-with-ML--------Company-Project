# Monthly-Forecasting-with-ML--------Company-Project

This forecast model uses the input table created with the "input transformer code" applied in another Jupyter notebook. This notebook is about monthly forecasting of sales data. For training and model creation; I used most of the historical data as training data and selected the last N months as test set; N is specified at the beginning of code as a parameter.

Test set is consisting of 0 values for test months at beginning. Think about N rows to be predicted. When 1st month of the test set is predicted, it is also written on another rows in a shifting pattern, according to "Last M months" parameter set at the beginning.

After I get the predictions of model, I compared them to the real life predictions made by sales department for these last N months.

Model structure is based on a classification stage at first. Dataset is a "0 dense dataset" where about 50% of the data contains 0 as a sales output. This creates some issues for a regression problem. 0 values leverages the predictions towards 0.

When I divided the problem into 2 stages; I also could neglect 0 values from regression problem. In first stage, classification algorithm decides if a values is 0 or "not 0". If it predicts the value as 0, then a regression algorithm will not be applied for that row and prediction is written a 0. But if it is labeled as "not 0", second stage regression algorithm will be applied for that row and regression result will be written as a prediction.

Classification dataset consists of all the input data (if it is balanced - daily prediction dataset was imbalanced and I applied (80% 0 20% else) an undersampling algorithm to 0 values to make it balanced, I am adding it into this code also as a comment-) whereas regression data neglects 0 values from the input to eliminate their leverage effect.

Inside this development code there are several parameters for experimental trials like nestedcv parameter, or neural network parameter etc. They are set at the beginning according to the experimental design and model is run according to these settings. Mostly, I am using hyperparameter search on several algorithms to get a better performance from this dataset. And also I use cross validation to get a better estimate of errors from different runs.

After getting best of the best model among all experiments, a shortened version of this code can be used for further production stages with the best hyperparameters for the selected model, making predictions on newcoming data.

This project is simply for ad-hoc usage. It will be used at a monthly frequency to update monthly forecasts for future sales.

Segmented Model ---- is the model version with companies divided into 3 different segments and for each segment a different regression algorithm is trained. 

Input data preparation files ------ are 2 different versions of input preparation models. Input data supplied from sales department had to be turned into into an applicable format by ML algorithms (Daily version for daily forecasting; monthly version for monthly forecasting). Also further parameters are combined together and joined inside this model. Finally, an input dataset is formed, ready to be used by models. 
