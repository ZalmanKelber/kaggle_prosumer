These notebooks explore feature engineering, feature selection and model selection for the [Estonian prosumer energy competition on Kaggle](https://www.kaggle.com/competitions/predict-energy-behavior-of-prosumers).  In it, a series of time-stamped data containing weather events, energy prices, and information about various businesses is used to predict energy output among Estonian "prosumers" (organizations that both provide and consume energy)

A key aspect of feature engineering involves mapping weather events to specific organizations that only have the Estonian county they're located in as part of the input data.  While [public notebooks](https://www.kaggle.com/code/nischaymahamana/enefit-pebop-submission-change-hps) in this competition have used topo-geographic data to map weather stations onto counties and take the average of them, I chose a different approach, instead chosing the weather station for each county closest to that county's main population center, reasoning that prosumers are likely to be concentrated in those places in an industralized and urbanized society like Estonia

Other than that, the mapping of weather, client and price data onto the input data is fairly straightforward.  Using the `statsmodel` API, features are evaluated by Fscore and VIF to determine the most useful features for the model.  An `LGBMRegressor` model is chosen, with a grid search used to tune the hyper-perameters