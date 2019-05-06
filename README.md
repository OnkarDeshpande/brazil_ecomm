# Brazilian E-Commerce

E-commerce public dataset, contains dataset of orders from 2016-2018.

Data source: https://www.kaggle.com/olistbr/brazilian-ecommerce

Problem definition:
1. Build a machine learning model to predict the payment_value of a given order. The business can look at factors contributing to the order value, directly correlated with revenue of the organization.
2. Cluster the customers and visually check if they follow any relationship with geography.


General workflow:

[000_EDA](https://github.com/OnkarDeshpande/brazil_ecomm/blob/master/code/000_EDA.ipynb) : contains trivial findings about datasets, column types and understand the target

[100_datata_preproces](https://github.com/OnkarDeshpande/brazil_ecomm/blob/master/code/100_data_preprocess.ipynb) : File reads and transforms data cols into correct data type, converts categorical with their codes. Seller and customer information wrt to state and city are mapped using the same categorical codes. The files are stored in pickle formats for faster read operations in future.

[200_feature_creation_FT](https://github.com/OnkarDeshpande/brazil_ecomm/blob/master/code/200_features_creation_FT.ipynb) : Uses featuretools to build feature set. It requires relationship among the datasets to be specified. Using relational information, and the mentioned aggregation and transformation level primitives, feature set is created and stored in pickle files.

[201_clustering_features](https://github.com/OnkarDeshpande/brazil_ecomm/blob/master/code/201_clustering_features.ipynb) : The notebook concentrates on creating few continouos features that are then used for clustering of customers.

[300_lgb_optuna_tune_model](https://github.com/OnkarDeshpande/brazil_ecomm/blob/master/code/300_lgb_optuna_tune_model.ipynb) : LightGBM model is built to predict the order value of a given order. Model hyperparameters are tuned using optuna package. Final model is built on the training set, feature importance is noted.

[400_customer_clustering](https://github.com/OnkarDeshpande/brazil_ecomm/blob/master/code/400_customer_clustering.ipynb) : Hierarchial clustering is used here. To see if the clusters follow any pattern, PCA was done for visual aid. Due to memory error for clustering huge dataset, clusters were formed on customers who have reviewed at least once and followed by using KNN to predict on the non-reviewers. Finally, a state level comparison for which states has highest percentage of one cluster of customers was done. The top 5 states remained same in both clusters.
