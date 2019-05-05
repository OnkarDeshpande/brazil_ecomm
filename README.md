# Brazilian E-Commerce

E-commerce public dataset, contains dataset of orders from 2016-2018.

Data source: https://www.kaggle.com/olistbr/brazilian-ecommerce

Problem definition: Build a machine learning model to predict the payment_value of a given order. The business can look at factors contributing to the order value, directly correlated with revenue of the organization.

General workflow:

000_EDA : contains trivial findings about datasets, column types and understand the target

100_datata_preproces : File reads and transforms data cols into correct data type, converts categorical with their codes. Seller and customer information wrt to state and city are mapped using the same categorical codes. The files are stored in pickle formats for faster read operations in future.

200_feature_creation_FT : Uses featuretools to build feature set. It requires relationship among the datasets to be specified. Using relational information, and the mentioned aggregation and transformation level primitives, feature set is created and stored in pickle files.

300_lgb_optuna_tune_model : LightGBM model is built to predict the order value of a given order. Model hyperparameters are tuned using optuna package. Final model is built on the training set, feature importance is noted.
