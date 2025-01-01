# Insurance Premium Prediction with LightGBM and CatBoost


### Background

This is my submission to this [Kaggle Competition](https://www.kaggle.com/competitions/playground-series-s4e12).
The objective of this challenge is to predict insurance premiums based on various factors.

### Dataset

This repository uses a synthetic dataset consisting of multiple numerical and categorical features, with a significant portion of missing values.

You can download the dataset [here](https://drive.google.com/drive/folders/1fq4HXWJO6sg-mtbLNcrnQAXPws2KRrDn?usp=drive_link).
The dataset should be downloaded to a separate `data` folder to result in the following repo structure:

```
repository
│───README.md
│───run.ipynb   
│
|─── data
│      │───train.csv
│      │───test.csv
```

### Rundown (`run.ipynb`)

##### Missing Value Imputation
1. Impute missing value for numerical features using their median, and for categorical features an indicator class "Unknown".

2. Another experimented method is random imputation generated from the distribution of each feature (`notebook_v1.ipynb`). However, this method is not stable, and the performance is worse than 1.

##### Feature Transformation
1. Handle skewed numerical features by applying either log, sqrt, and boxcox transformation.
2. Encode date-time features by applying sinusoidal transformation
3. Encode categorical features by either ordinal encoding (for ordinal features) or one-hot encoding (for nominal features)

##### Model Training

The model is an emsemble of LightGBM and CatRegressor. 

1. Separate hyperparameter tuning for LightGBM and CatRegressor
2. Training the emsemble model