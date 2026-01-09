# Stock Movement Feature Selection using filter based, wrapper based approaches and Dimensionality Reduction

## Problem Statement Overview
In financial markets, understanding directional price movements is crucial for identifying short-term trends and making informed investment decisions. Given historical stock price data of major technology companies, the objective of this study is to extract meaningful patterns from daily market features that help classify whether a stock’s price movement indicates an upward or downward trend.

To formulate this as a supervised learning problem, a new binary class label called target is created by comparing the closing prices of consecutive trading days. If the previous day’s closing price is greater than the current day’s closing price, the movement is labeled as high, otherwise it is labeled as low. The first observation is assigned a default label.

Using numerical features such as Open, High, Low, Close, Adjusted Close, and Volume, the task involves applying feature selection and dimensionality reduction techniques to identify the most relevant patterns associated with price movement direction. Classification models are then trained and evaluated to assess how effectively these extracted patterns can distinguish between the two classes.

This study emphasizes methodological correctness, including prevention of data leakage, handling multicollinearity, and interpretability of results, rather than attempting to forecast exact stock prices.

## Objectives
1. To classify daily stock price movements as high or low
2. To compare filter, wrapper, and LDA-based approaches for feature selection
3. To evaluate classification performance using appropriate statistical models

## Methodology

### I. Exploratory Data Analysis
Exploratory Data Analysis (EDA) is a mechanism of understanding data, identifying patterns, and behaviour of data either by using statistical techniques or visual methods. EDA helps us to understand the data in a better way so that we choose the best model for implementation that gives maximum performance. We have performed Histogram, boxplot, countplot and scatterplot analysis for univariate and bivariate data. We have also performed a multivariate analysis using a correlation heatmap.

### II.  Data Preprocessing
We have handled outliers using IQR capping and have also implemented StandardScaler for scaling the features so that high valued features do not overpower the low values features.

### III. Train_test_split
The dataset is first split into training and testing sets to ensure unbiased model evaluation.

Training data → Used for feature selection and model fitting  
Testing data → Used only for final evaluation

This prevents data leakage, especially important in feature selection.

### IV. Feature Selection Techniques
a) Filter Method
-> Used SelectKBest with ANOVA F-test (f_classif)
-> Evaluates each feature independently based on its relationship with the target
-> Fast and model-agnostic

 b) Wrapper Method
Used Recursive Feature Elimination (RFE) with Logistic Regression and selects features by recursively training the model.

### V. Dimensionality Reduction
We could observe immense multicollinearity in the features. Thus to remove the impact of multicollinearity and improve class separability, we have performed Dimensionality Reductio. As this is a classification task, we have implemented Linear Discriminant Analysis. A pipeline had been used to combine LDA and LogisticRegression model, in order to prevent data Leakage issues

### VI. Classification Model
Logistic Regression was used as the classifier.

## Results:
Method	Accuracy
-> Filter-based Feature Selection	76%
-> Wrapper Method (RFE)	80%
-> Linear Discriminant Analysis (LDA)	80%

## Key Observations
-> Wrapper methods outperformed filter-based selection due to model-aware feature optimization.
-> LDA achieved competitive accuracy by reducing multicollinearity and enhancing class separation.
-> More complex models (e.g., QDA) were tested but showed poor generalization, likely due to multicollinearity and limited sample size.

## Conclusion
The project demonstrates that simpler, assumption-aware models like Logistic Regression combined with LDA or RFE can perform effectively on structured numerical data.
Accuracy alone was not prioritized; instead, emphasis was placed on correct methodology, interpretability, and robustness.

## Tools & Libraries
### Python
### NumPy
### Pandas
### Scikit-learn
### Matplotlib

## Future Work
1. Cross-validation for more robust evaluation
2. Feature engineering using technical indicators
3. Comparison with tree-based models
