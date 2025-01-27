# Machine Learning

- [Machine Learning](#machine-learning)
  - [Introduction](#introduction)
    - [Definition Machine Learning (ML)](#definition-machine-learning-ml)
    - [Types of Machine Learning](#types-of-machine-learning)
      - [1. Supervised ML](#1-supervised-ml)
      - [2. Unsupervised ML](#2-unsupervised-ml)
      - [3. Reinforcement ML](#3-reinforcement-ml)
    - [The Machine Learning Pipeline](#the-machine-learning-pipeline)
  - [Getting Started](#getting-started)
    - [Data preparation and preprocessing](#data-preparation-and-preprocessing)
      - [Data Collection](#data-collection)
        - [Data Sampling](#data-sampling)
        - [Labeling](#labeling)
      - [Data Preparation](#data-preparation)
      - [Data Cleaning](#data-cleaning)
        - [Missing Data](#missing-data)
        - [Inconsistency](#inconsistency)
        - [Outliers](#outliers)
      - [Data Preprocessing](#data-preprocessing)
      - [Data Visualization](#data-visualization)
    - [Choosing the ML model](#choosing-the-ml-model)
      - [Algorithms](#algorithms)
      - [Techniques](#techniques)
      - [Use cases](#use-cases)
      - [Frameworks](#frameworks)
    - [Model Training](#model-training)
      - [Formatting data](#formatting-data)
      - [Testing and validation techniques](#testing-and-validation-techniques)
        - [Splitting data](#splitting-data)
        - [Cross-validation](#cross-validation)
      - [Model training concepts](#model-training-concepts)
    - [Model Tuning](#model-tuning)
      - [Training Data Tuning](#training-data-tuning)
      - [Regularization](#regularization)
      - [Hyperparameter tuning](#hyperparameter-tuning)
        - [Grid Search](#grid-search)
        - [Randomized Search](#randomized-search)
        - [Bayesian Search](#bayesian-search)
    - [Model Evaluation](#model-evaluation)
      - [Bias Variance Tradeoff](#bias-variance-tradeoff)
      - [Model Metrics](#model-metrics)
        - [Classification Metrics](#classification-metrics)
        - [Regression Metrics](#regression-metrics)
      - [Unsupervised clustering](#unsupervised-clustering)
        - [Silhouette score](#silhouette-score)
        - [Homogeneity score](#homogeneity-score)
        - [Completeness Score](#completeness-score)
        - [V measure Score](#v-measure-score)
        - [Adjusted Random Score](#adjusted-random-score)
        - [Adjusted Mutual Information Score](#adjusted-mutual-information-score)
      - [Validation Curve](#validation-curve)
      - [Learning Curve](#learning-curve)
      - [Model Debugging](#model-debugging)
    - [Feature Engineering](#feature-engineering)
      - [Feature Extraction](#feature-extraction)
      - [Feature Selection](#feature-selection)
      - [Feature Creation and transformation](#feature-creation-and-transformation)
      - [Bagging/Boosting](#baggingboosting)
  - [ML Data Readiness](#ml-data-readiness)
  - [Productizing a ML Model](#productizing-a-ml-model)
    - [Aspects to consider](#aspects-to-consider)
    - [Types of Production environments](#types-of-production-environments)
      - [Batch predictions](#batch-predictions)
      - [Online Predictions](#online-predictions)
      - [Online training](#online-training)
    - [Business metrics vs Model Metrics](#business-metrics-vs-model-metrics)
    - [Storage](#storage)
    - [Model and Pipeline Persistence](#model-and-pipeline-persistence)
    - [Model Deployment](#model-deployment)
    - [Monitoring](#monitoring)
    - [Maintenance](#maintenance)
  - [Common Mistakes](#common-mistakes)
  - [References](#references)

## Introduction

### Definition Machine Learning (ML)

- The study of computer programs (algorithms) that can learn by example.
- ML algorithms can generalize from existing examples of a task.

### Types of Machine Learning

#### 1. Supervised ML

- Learn to predict target values from labelled data.

1. Classification: Target values with discrete classes
   1. Binary Classification: To identify targets with two classes
      - eg: Fraud detection or Spam email identification
   2. Multi-class identification: To identify targets with more than two classes.
      - eg: Differentiate between fruit types
2. Regression: Target values are continuous values.  
     - eg: Predict house price

#### 2. Unsupervised ML

Find structure in unlabeled data

1. Clustering: Find groups of similar instances in the data.
   - Finding clusters of similar users.
2. Dimensionality Reduction
   - Find latent or significant features in data
     - Find latent driers of stock movements
   - Pre-process data to build more robust machine learning models.
   - Improve performance of models in training.
3. Anomaly detection
   - Find fraudulent credit card transactions
4. Quantization
   - Compress true color (24 bit) to 8 bit

#### 3. Reinforcement ML

- Models learn by taking actions that can earn rewards.

### The Machine Learning Pipeline

1. Business Problem:
   - Identify the problem that could benefit from ML
2. Business Formulation: Preparing the problem
   - Identify ML model type (Classification, Regression)
   - Frame the simplest solution without losing important information
   - Choosing the data:
     - How much is it?
     - Where is it?
     - Do I have access to it?
   - Get a domain expert:
     - An expert for the business case.
     - Can identify the important features
     - Decide whether the data is representative for the real world
   - Evaluate the data quality
   - Identifying the features and the label
   - Does the problem needs a lot of labeled data?
   - Identify the metrics:
     - Model performance metric
       - Used during model training and evaluation
     - Business goal metric
       - Used after model deployment
       - Measures how well the model is performing
3. Data preparation and preprocessing
   - Data collection and integration
   - Determine where data comes from
   - Data Preprocessing and visualization
   - Design data for the model
4. Model Training and Tuning
5. Model Evaluation:
   - Testing the model on new data and assess the results
6. Optimization
   - Data Augmentation:
     - Modify the data
   - Feature Engineering:
     - Create or remove features
7. Model Deployment

## Getting Started

### Data preparation and preprocessing

#### Data Collection

- It is the process of acquiring training and/or test data.
- It can be structured or unstructured data.
- It is collected for:
  - Initial datasets for training models and measuring success.
  - Additional data for tuning
  - Replacements for flawed or outdated sets
  - Data and model maintenance post-production
- It can be collected from many sources like:
  - Server
  - Database
  - Disk
  - Clickstream
  - Multimedia
  - IoT and sensors
  - Social media
  - Web sites
  - Data providers
- When in the cloud, Data Lake is used. It can store and serve both structured and unstructured data.

##### Data Sampling

Selecting a subset of instances for training and testing

- Representativity:
  - Sample needs to be representative of the expected production population; i.e., unbiased
  - Especially important for testing and measurement sets
  - It's also important for training sets to get good generalization

- Random sampling:
  - Sampling so that each source data point has equal probability of being selected.
  - With random sampling, rare subpopulations can be underrepresented (or not represented at all). Stratified sampling can fix this issue.
  - Stratified sampling: Apply random sampling to each subpopulation separately.

- Other issues of sampling:
  - Seasonality: Time of day, special events, holidays
    - Stratified sampling across these can minimize bias.
    - Visualization can help
  - Trends: Patterns can shift over time, and new patterns can emerge.
    - To detect, try comparing models trained over different time periods
    - Visualization can help
  - Train/test bleed: Inadvertent overlap of training and test data when sampling to create datasets
    - Sample form fresh data
    - Filter out already selected instances
    - Partition source data along some dimension (but avoid bias)
    - Be especially careful with time-series data and data with duplicate entries.
  - Leakage: Using information during training or validation that is not available in production

##### Labeling

- Obtaining gold-standard answers for supervised learning
- Often, labels are not readily available in sampled data.
- Examples:
  - Search: The results a customer wanted to receive
  - Music categorization: The genre of a piece
  - Sentiment analysis: The overall attitude of the writer
  - Digitization: The transcription of handwriting
  - Object detection: The localization of objects in images
- Human labels can be preferable to minimize bias, capture subtleties, etc.

#### Data Preparation

- Reformat the collected data from (CSV, JSON, Pickle, ..etc) into a tabular format.
- Make sure that the data is imported properly by importing the first few rows
- Understand the data dimensions, column names
- Checking for missing data, duplicates, wrong data types

#### Data Cleaning

##### Missing Data

- Sources:
  - Undefined values, collection errors, left joins, etc..
- Issues:
  - Many learning algorithms can't handle missing values.
  - Makes it hard to interpret a target relationship
- Identifying the cause can determine whether to delete or impute them.
  - What were the mechanisms that caused the missing values?
  - Is it random and which kind of values are missing?
  - Are there rows or columns missing that not aware of?
- Techniques to solve:
  - Dropping(deletion):
    - Risk of dropping rows:
      - Not enough training samples (overfitting)
      - May bias sample
    - Risk of dropping columns:
      - May lose information in features (underfitting)
  - Imputation (adding):
    - Unit Non-Response:
      - Refers to entire rows of missing data
      - Imputation Methods include: Weight-Class Adjustments
    - Item Non-Response
      - Specific cells of a column are missing
      - Types:
        - MCAR: stands for Missing Completely at Random.
          - This happens when missing values are missing independently from all the features as well as the target.
        - MAR: stands for Missing at Random.
          - This occurs when the missing value is dependant on a variable, but independent from itself.
        - MNAR: stands for Missing Not at Random.
          - This is the case where the missingness of a value is dependent on the value itself.
      - Methods:
        - Hot-Deck Imputation: Sort records on any criteria, and for each missing value, use the prior available value.
        - Weight-Class Adjustments
        - Deductive Imputation
        - Mean/Median/Mode Imputation
        - Model-Based Imputation (Regression, Bayesian, etc)
        - Proper Multiple Stochastic Regression
        - Pattern Submodel Approach
    - Python libraries:
      - SciKit learn:
        - `sklearn.preprocessing.SimpleImputer`
      - Advanced methods for Imputation:
        - MICE (Multiple Imputation by chained Equations).
        `sklearn.impute.MICEImpute` (v0.20)
        - Python (not sklearn) `fancyimpute` package (KNN impute, SoftImpute, MICE, etc..)

##### Inconsistency

- Column values with different units
- Wrong or unrelated column values

##### Outliers

- It is the data points that differ significantly from other data points in the same dataset.
- It can:
  - Add richness to the data
  - Make accurate predictions more difficult
  - Indicate that the data point belongs to another column
- Identifying
  - Distance from mean
  - Distance from fitted line
- Techniques to solve
  - Dropping
  - Cap/Floor
  - Set to mean
- Types:
  - Artificial: when the outlier doesn't belong to the real world
    - eg: Age is 150
    - It needs to be deleted
  - Natural: when the outlier can be actually genuine
    - eg: Salary of CEO vs other employees
    - Transform the outlier
      - Ex: Use the natural log of each value in the column to reduce the extreme variation between the values.
    - Impute a new value for the outlier
      - Ex: Use the mean of that column

#### Data Preprocessing

- Descriptive Statistics:
  - Categorical vs Numerical stats
  - Understanding Mean and Median
- Encoding Labels for categorical features:
  - It is converting categorical variable into a numerical variable.
  - Ordinal:
    - SciKit Learn library, `LabelEncoder`, converts categorical variable to numerical variable that starts with 0 and increase with 1. But if this applied to non-nominal categorical type, may lead to wrong computations or wrong usages. So, it is recommended to be used with Ordinal type that has relationships with each other.

      ```py
        from sklearn.preprocessing import LabelEncoder

        loan_enc = LabelEncoder()
        y = group_enc.fit_transform(df['loan_approved'])
      ```

  - Nominal:
    - While library `OneHotEncoder` is more likely to be used for Nominal variables.

      ```py
      from sklearn.preprocessing import OneHotEncoder

      df = pd.DataFrame({"Fruits":["Apple","Banana","Banana","Mango","Banana"]})
      num_type = group_enc.fit_transform(df['Fruits'])
      type_enc = OneHotEncoder()
      type_enc.fit(num_type.reshape(-1,1))
      ```

    - Pandas library has `get_dummies`() function to do the same as OneHotEncoder

      ```py
      import pandas as pd

      df = pd.DataFrame({"Fruits":["Apple","Banana","Banana","Mango","Banana"]})

      pd.get_dummies(df)
      ```

  - Encoding with many classes:
    - Define a hierarchy structure.
    - Try to group the levels by similarity to reduce the overall number of groups.

#### Data Visualization

- Categorical data visualization:
  - Bar Charts
- Numerical data:
  - Histograms
    - How many peaks
    - Is there any skewness
    - Is the data normally distributed
  - Density plot
    - Identify skewness
    - Detect outliers
  - Box plot
    - Detect outliers
    - Visualize mean, std, IQR
- Multivariate stats
  - Benefits:
    - Identify correlation between features.
    - High correlation between features can sometimes lead to poor model performance
  - Visualization techniques:
    - Scatterplot
    - Scatterplot with labels identification
    - Scatterplot matrix
    - Correlation matrix with Heatmap

### Choosing the ML model

#### Algorithms

1. Supervised Learning
   1. Classification
      1. Binary
         1. XGBoost
         2. Linear learner
      2. Multi-class
         1. XGBoost
         2. KNN
         3. Naive Bayes
         4. SVMs
         5. Decision Trees
         6. Random Forest
   2. Regression
      1. XGBoost
      2. Linear learner
      3. Lasso
      4. Ridge
      5. SVR
      6. KNN
      7. Factorization machines
   3. Recommendation
      1. Factorization machines
2. Unsupervised Learning
   1. Clustering
      1. Hierarchical (Connectivity-based): Build a tree representation of the data. Objects close to each other are more likely to be in the same cluster.
         1. Birch, Agglomerative (Many clusters, Many records) 
      2. Centroid-based: Cluster entities based on distance from these centroids (central vector).
         1. K-means (Moderate clusters, Many records)
            - For even cluster sizes and flat surfaces
            - Mini-batch K-means tweaks algorithm to be much faster, almost as good
         2. Mean-shift (Many clusters, Small records)
            - Worsk well with uneven cluster sizes and manifold shapes
            - Uses pairwise distances between points
      3. Distribution-based: Entities that are likely from the same distribution are more likely to be in the same cluster.
         1. Gaussian Mixture
      4. Density-based: Define clusters based on regions of high density (concentration) of entities. Objects in sparse areas are often treated as noise.
         1. DBSCAN (Moderate clusters, Many records)
            - For uneven cluster sizes and manifolds
      5. Affinity Propagation (Many clusters, Small records)
            - Works well with uneven cluster sizes and manifold shapes
            - It does not need number of clusters to be specified
      6. LDA
      7. Spectral (Few clusters, Medium records)
         - Simple to implement
         - Intuitive results for data exploration
         - Even cluster sizes
         - Fine for manifolds
         - Relies on distances between points
   2. Topic modeling
      1. LDA
   3. Embeddings
      1. Object2Vec
   4. Anomaly detection
      1. Random cut forest
      2. IP insights
   5. Dimensionality reduction
      1. PCA
      2. Manifold learning
      3. Factor analysis

#### Techniques

1. Cold start
   - It is the creation of a model from scratch that requires training and tuning.
2. Warm Start
   - Use information gained from previous training runs to identify smarter starting points for the next training run.
3. Transfer Learning
   - The practice of reusing already trained neural network model that solves a similar problem.
   - The already created model is created by experts that invested time and knowledge for a similar domain.
   - It is useful when the new dataset is small and not sufficient to train a model from scratch.

#### Use cases

- Image data
  - Convolutional Neural Networks (CNN)
- Complex textual data
  - Recurrent Neural Networks (RNN)
- Sequential or time-series data
  - Recurrent Neural Networks (RNN)
- Linear x-variables
  - Linear and logistic regression
  - PCA
- Twisted data (S-curves, Swiss rolls)
  - Manifold learning
- Large number of x-variables
  - Decision trees
- Binary Classification
  - Logistic Regression
  - Support Vector Machines
- Multilabel Classification
  - Naive Bayes

#### Frameworks

1. Scikit-learn
    - Easy to use
      - Estimator API for consistent interface
      - Create a model object
      - Fit to training data
      - Predict for new data
    - Comprehensive
      - All common families of ML models
      - Cross-validation
      - Feature extraction and selection
      - Data pre-processing
      - Data generation
        - Swiss rolls, S-curves
    - Efficient
      - Highly optimized implementations
      - Built on SciPy, hence scikit prefix
      - Inter-operates with
        - NumPy
        - SciPy
        - Matplotlib
        - Pandas
2. PyTorch
   - Fast
   - Flexible experimentation
3. TensorFlow
   - End-to-end open source platform
   - Comprehensive
   - Flexible ecosystem
     - Tools
     - Libraries
     - Community resources
4. Keras
   - A high level neural network API, written in Python
   - Runs on top of TensorFlow, CNTK, or Theano
5. Apache MXNet
6. Microsoft CNTK
7. XGBoost
8. Theano

### Model Training

- The goal of training is to create an accurate model that answers the business question accurately as often as you need it or more.

#### Formatting data

- Common types for algorithms:
  - CSV: Comma separated values
    - Label on the left
  - rec: Record-IO protobuf

#### Testing and validation techniques

##### Splitting data

- We split the data to avoid overfitting and get generalized performance. The data is split into three sets:
  - Training set:
    - It is used in the model training phase to see patterns.
    - It ranges around 80% of the full data
  - Validation/Evaluation set:
    - It is used also in the training phase but used to give an estimate of model performance and/or compare performance across different models.
    - It ranges around 10% of the full data.
  - Testing set:
    - It is used to evaluate the predictive quality of the model.
    - It ranges around 10% of the full data.
- Python SciKit learn `sklearn.model_selection.train_test_split` can be used for splitting

##### Cross-validation

- It compares the performance of multiple models
- It basically gives more stable and reliable estimates of how the classifiers likely to perform on average by running multiple different training test splits and then averaging the results.
- It gives information about how sensitive the model is, to the nature of the specific training set.
- It does take more time and computation to do cross-validation.
- The records might need shuffling to avoid possible bias in the ordering by class label. For example, the first 20% of the data has the same label.

1. K-Fold Cross Validation:
   - Used when there is a small dataset
   - Most commonly used with K set to 5 or 10.
   - As K increases, TIME and VARIANCE in test data increases and BIAS decreases
   - Eg: to do five-fold cross-validation, the original dataset is partitioned into five parts of equal or close to equal sizes. Each of these parts is called a "fold". Then a series of five models is trained and validated using a different fold. In such that Model one, is trained using folds 2 through 5 as the training set and evaluated using fold 1 as the validation set. Model 2, is trained using Folds 1, 3, 4, and 5 as the training set, and evaluated using Fold 2 as the validation set, and so on. When this process is done, we have five accuracy values, one per fold.
   ![K-Fold validation](ML%20images/K-Fold_CV.png)
2. Iterated K-Fold validation with shuffling  
   - It is the same as K-Fold validation but with extra K iteration. The difference between each iteration is that the data set is shuffled differently in each iteration.
   - Eg: In K = 3, the first iteration is occurred same as 3-Fold validation which the average of the 3 models is taken, then two more iteration of this 3-Fold validation but with shuffling the data before splitting them. Then the average of the 3 iterations is taken.
   ![Iterated K-Fold validation](ML%20images/Iterated_K-Fold_CV.png)
3. Leave-one-out cross-validation:
   - It is used for very small datasets.
   - Test set is one data point.
4. Stratified K-Fold cross-validation:
   - Distributes label class across training and testing datasets.
   - For imbalanced data.

- SciKit Learn library `sklearn.model_selection.cross_val_score` can be used for cross validation:
  - In Classification problem, SciKit Learn do "Stratified K-fold Cross-validation". The Stratified Cross-validation means that when splitting the data, the proportions of classes in each fold are made as close as possible to the actual proportions of the classes in the overall data set.
  - In regression, SciKit Learn uses regular k-fold cross-validation.

#### Model training concepts

- How training the model works:
  - ![Training Concept](ML%20images/Model-Training-Concept.png)
  - The model is given a specific set of features.
  - The model predicts the classes for these features based upon the weights that was given to the features.
  - Then the predictions are compared with the actual labels to compute the loss.
  - Based on the loss computed, the model parameters (features weights) are updated to minimize the loss.
- What is loss function  
![Loss function](ML%20images/Error_Parameter_plot.png)
  - Loss function is the measure of the error in the model predictions, given a certain weights.
- Types of loss functions:
  - RMSE (Root mean square error):
    - Describes the sample standard deviation of the differences between predicted and observed values.
    - $$\sqrt{\frac{\sum_{i=1}^n(Y_{\text{target},i}-Y_{\text{pred},i})^2}{n}}$$
  - Logs Likelihood loss:
    - Considers the logarithm of probabilities of each class.
    - In Binary classification: $-(y\log{p} + (1-y) \log{(1-p)})$
- Optimization:  
![Loss function](ML%20images/Error_Parameter_plot_Global_Minima.png)
  - It is used to find the Minima.
  - Minima is the minimum point in the plot between loss and parameters or the point with the least amount of error.
  - It is often that there might more than one local Minima, in which the model might get stuck in local Minima instead of the Global Minima.
  - Ways to find the Global Minima:
    - Comparing all possible values which is inefficient way.
    - Gradient Descent  
    ![Gradient Descent](ML%20images/Gradient%20Descent.png)  
      - It is the searching for the Minima by taking a step into the direction where the point on the graph with negative gradient. Until it finds an positive gradient, then it reverses the direction to another point where has negative gradient. This process occurs until the Minima is found
      - Learning Rate:
        - It is how big is the step to be taken.
        - If it too big, the local Minima will be hard to be found.
        - If it too small, it will take too much time to be found.
      - Drawbacks:
        - Updates the parameters only after a pass through all the data (one epoch)
        - Can't be used when data is too large to fit entirely in memory.
        - Can get stuck at local Minima or fail to reach Global Minima.
    - Stochastic Gradient Descent:
      - It is the same as gradient descent except that the weights is updated at every data point.
      - It is very fast to converge.
      - The drawback is that it is very noisy, in such that the steps might be in several directions.
    - Mini-Batch Gradient Descent:
      - It uses mini batch of records, and then the parameters is updated.
      - It is slower than SGD but faster than Gradient Descent.
      - It doesn't consume much memory as SGD
    - Gradient Descent Variations:  
    ![Gradient Descent Variations](ML%20images/Gradient_Descent_Variations.png)
  - To find the Minima, an equation is calculated which is the derivative of the plot when it is equals to zero. Which is the point where the slope is neither increase nor decreases.

### Model Tuning

#### Training Data Tuning

- If training set is too small, then Sample and Label more data if possible
- If training set biased against or missing some important scenarios, then Sample and Label more data for those scenarios if possible.
- If it is not easy to sample or label more, then consider creating synthetic data by duplication or using Data Augmentation techniques like SMOTE.
- IMPORTANT: Training data doesn't need to be exactly representative, but your test set does.

#### Regularization

- Regularization is a technique used to reduce the errors by fitting the function appropriately on the given training set and avoid overfitting.
- Overfitting often caused by overly-complex models capturing idiosyncrasies in training set.
- Adding penalty score for complexity to cost function.
- $\text{cost}_{reg} = \text{cost} + \frac{\alpha}{2}\text{penalty}$
- Idea: Large weights corresponds to higher complexity.
- Regularization types:
  - Lasso(Least Absolute Shrinkage and Selection Operator):
    - A regression model which uses L1 Regularization technique
    - Lasso Regression adds “absolute value of magnitude” of coefficient as penalty term to the loss function.
    - The gradients of the loss function are INDEPENDENT of parameters, so some parameters can be set all the way to zero, hence completely ignored.
    - SciKit Learn: `sklearn.linear_model.Lasso`
  - Ridge:
    - A regression model that uses L2 regularization.
    - Ridge regression adds “squared magnitude” of coefficient as penalty term to the loss function.
    - The gradients of the loss function are DEPENDENT linearly on the parameters, so the parameters can never be zero. This means that no parameter is entirely ignored, and every parameter always has at least a very minimal effect on predictions.
    - SciKit Learn: `sklearn.linear_model.Ridge`
  - Elastic-Net:
    - Elastic-Net is a regularized regression method that linearly combines the L1 and L2 penalties of the LASSO and Ridge methods respectively
    - SciKit Learn: `sklearn.linear_model.ElasticNet`
- During Regularization the output function($\hat{y}$) does not change. The change is only in the loss function.

#### Hyperparameter tuning

It is an Estimator parameter that is NOT fitted in the data

- Hyperparameter types:
  - Model Hyperparameter:
    - It helps to define the model itself.
    - Ex: Filter size, pooling, stride, padding
  - Optimizer Hyperparameter:
    - It is how the model learns patterns on data
    - Ex: Gradient Descent, Stochastic Gradient Descent
  - Data Hyperparameter:
    - It defines attributes for the data itself
    - Useful for small/homogenous datasets
- Hyperparameters must be optimized separately
- Methods for tuning hyperparameters:
  - Manually:
    - Manually select Hyperparameters based on one's intuition and experience.
    - Often too shallow and inefficient of an approach
  - Grid Search
  - Random Search
  - Bayesian Search
- Hyperparameter tuning doesn't always improve the model.
- Best practices:
  - Don't adjust every hyperparameter
  - Limit range of values to what's most effective.
  - Run one training job at a time rather in parallel.

##### Grid Search

- It finds the optimum combination of hyperparameters by exhaustive search over specified parameter values.
- Compute intensive
- scikit-learn: `sklearn.grid_search.GridSearchCV`
  - `GridSearchCV(estimator, param_grid, scoring=None)`:
    - `estimator` is the ML model types. ex: `tree` for decision tree
    - `scoring` is your choice of model performance metric
    - `param_grid` is the hyperparameters values
      - ex: `param_grid ={ max_depth: [5, 10, 50, 100, 250], min_samples_leaf: [15, 20, 25, 30, 35]}`
    - `GridSearchCV` can be used as an estimator, with a fit and predict methods, it is also performing 5-fold Cross Validation by default for each combination of hyperparameters.
    - For the above example, 25 combinations of hyperparameters and with 5-fold CV for each combination, that would train 125 models. That will take time to complete.
    - Once all the combinations are evaluated, the model with the set of parameters which give the top metric is considered to be the best.
    - `GridSearchCV` returns the best combination of the hyperparameters, the best estimator equipped with these best hyperparameters, and will also report the performance metric of this best estimator.

##### Randomized Search

- Trained and scored on random combinations of hyperparameters
- Each setting is sampled from a distribution over possible parameter values.
- A more efficient implementation of hyperparameter tuning.
- Sci-kit Learn library: `sklearn.model_selection.RandomizedSearchCV(estimator, param_distributions, n_iter=10, scoring=None)`
  - `estimator` is the ML model types. ex: `tree` for decision tree
  - `scoring` is your choice of model performance metric
  - `param_grid` is the hyperparameters values
    - ex: `param_grid ={max_depth: [5, 10, 50, 100, 250], min_samples_leaf: uniform(15,35,5)}`
  - `n_tier` (default 10) is the number of random parameter settings that are sampled. It trades off runtime vs quality of the solution.
- In contrast to `GridSearchCV`, not all parameter values are tried out, but rather a fixed number of parameter settings is sampled from the specified distributions. The number of parameter settings that are tried is given by `n_iter`.
- `RandomizedSearchCV` also performs 5-fold CV by default for each combination of hyperparameters.
- Can sample from distributions (sampling with replacement is used), if at least one parameter is given as a distribution.
- If all parameters are presented as a list, sampling without replacement is performed.
- If at least one parameter is given as a distribution, sampling with replacement is used.
- It is highly recommended to use continuous distributions for continuous parameters.

##### Bayesian Search

- Make guesses about hyperparameter combinations, then uses regressions to refine the combinations.
- It keeps track of previous hyperparameter evaluations and builds a probabilistic model.
- It tries to balance exploration (uncertain hyperparameter set) and exploitation (hyperparameters with a good chance of being optimum)
- It prefers points near the ones that worked well.
- AWS SageMaker uses Bayesian Search for hyperparameter optimization.

### Model Evaluation

#### Bias Variance Tradeoff

![Variance vs Bias](ML%20images/Variance_vs_Bias.png)

- Machine learning models depend on input data, output data, and understanding the relationship between the two. *bias* and *variance* affect the relationship between input and output data.

- Bias:
  - It is the gap between predicted value and actual value.
  - It is an error from flawed assumptions in the algorithm.
  - High bias can cause an algorithm to miss important relationships between features and target outputs resulting in ***underfitting***.
  - Bias = $E[\hat{f}(x)] - f(x)$, Where $f(x)$ is the true model, $\hat{f}(x)$ is the estimated model.
  - Solution:
    - Increase the number of features
    - Decrease degree of regularization

- Variance:
  - How dispersed the predicted values are
  - It is an error from sensitivity to small variations in the training data. High variance can cause an algorithm to model random noise in the training set, resulting in ***overfitting***.
  - Variance = $E[(\hat{f}(x)-E[\hat{f}(x)])^2]$, Where $f(x)$ is the true model, $\hat{f}(x)$ is the estimated model.
  - Solution:
    - Increase training data
    - Reduce model complexity
      - Decrease the number of features
      - Increase the degree of regularization

- Total Error $(x) = \text{Bias}^2 + \text{Variance} + \text{Irreducible Error}$

#### Model Metrics

##### Classification Metrics

- Confusion Matrix:
  - True Positive (TP): When model predicts Positive outcome as Positive
  - True Negative (TN): When model predicts Negative Outcome as Negative
  - False Positive (FP): When model predicts Positive outcome as Negative
  - False Negative (FN): When model predicts Negative outcome as Positive

To determine how well is the Logistic Model, the are some some metrics:

- **Accuracy**:
  - Accuracy (also called Score) is the proportion of correctly labeled rows divided by the total number of rows in data set. There are some cases when Accuracy won't work well, when there are large class imbalances in the dataset.

$$\text{Accuracy} = \frac{TP+TN}{TP+TN+FP+FN}$$

- **Precision**:
  - Out of all the items labeled as positive, how many truly belong to the positive class.

$$\text{Precision} = \frac{TP}{TP+FP}$$

- **Recall**:
  - Out of all the items that are truly positive, how many were correctly classified as positive. Or simply, how many positive items were 'recalled' from the dataset.

$$\text{Recall} = \frac{TP}{TP+FN}$$

- **F1 score**:
  - It helps express precision and recall with a single value.

$$\text{F1 Score} = \frac{2 . \text{Precision} . \text{Recall}}{\text{Precision} + \text{Recall}}$$

- **AUC - ROC**:
  - AUC: Area-under-curve (degree or measure of separability).
  - ROC: Receiver-operator characteristic curve (probability curve).
  - AUC - ROC curve:
    - A performance measurement for a classification problem at various threshold settings
  - The optimum model has 1 AUC value

    ![AUC - ROC Curve](ML%20images/AUC-ROC.png)

##### Regression Metrics

- **MSE** (Mean Squared Error)
  - Average squared error over entire dataset
  - Mean squared error(MSE) = $\frac{1}{N}\sum_{i=1}^N(\widehat{y} - y_i)^2$
  - Very commonly used
  - SciKit-learn: `sklearn.metrics.mean_squared_error`
- **$R^2$ error**
  - $R^2 = 1 - \frac{\text{Sum of Squared Error (SSE)}}{\text{Var}(y)}$ which is between 0 and 1
  - Interpretation: Fraction of variance accounted for by the model
  - Basically, standardized version of MSE
  - Good $R^2$ are determined by actual problem
  - $R^2$ always increase when more variables are added to the model.
  - Highest $R^2$ may not be the best model.
- **Adjusted $R^2$**
  - Adjusted $R^2= 1-(1-R^2)\frac{\text{no. of data pts.} -1}{\text{no. of data pts. - no. of variables}-1}$
  - Takes into account of the effect of adding more variables such that it only increases when the added variables have significant effect in prediction.
  - It is a better metric for multiple variates regression.
  - SciKit-learn: `sklearn.metrics.r2_score`
- **Confidence Interval**
  - An average computed on a sample is merely an estimate of the true population mean.
  - Confidence interval: Quantifies margin-of-error between sample metric and true metric due to sampling randomness
  - Informal interpretation: with x% confidence, true metric lies within the interval.
  - Precisely: If the true distribution is as stated, then with x% probability the observed value is in the interval.
  - Z-score: Quantifies how much the value is above or below the mean in terms of its standard deviation

#### Unsupervised clustering

##### Silhouette score

- A measure of how similar a point is to other points in its own cluster and how different it is from points in other clusters.
- SciKit-learn: `sklearn.metrics.silhouette_score`

##### Homogeneity score

- Clustering satisfies homogeneity if all clusters contain only points from the same class.
- SciKit-learn: `sklearn.metrics.homogeneity_score`

##### Completeness Score

- A clustering result satisfies completeness if all the data points that are members of a given class are elements of the same cluster.
- SciKit-learn: `sklearn.metrics.completeness_score`

##### V measure Score

- Harmonic mean of the homogeneity score and the completeness score
- Harmonic mean usually used to find the average of rates.
- SciKit-learn: `sklearn.metrics.v_measure_score`

##### Adjusted Random Score

- Similarity measure between clusters which is adjusted for chance i.e. random labelling of data points.
- SciKit-learn: `sklearn.metrics.adjusted_rand_score`

##### Adjusted Mutual Information Score

- Information obtained about one random variable by observing another random variable adjusted to account for chance.
- SciKit-learn: `sklearn.metrics.adjusted_mutual_info_score`

#### Validation Curve

- A validation curve is typically drawn between some parameters of the model and the model’s score. Two curves are present in a validation curve – one for the training set score and one for the cross-validation score.
- To evaluate the effect that an important parameter of a model has on the cross-validation scores.
- Like cross-value score, validation curve will do threefold cross-validation by default but it can be adjusted with the CV parameter as well.
- Unlike `cross_val_score`, you can also specify a classifier, parameter name, and set of parameter values, you want to sweep across.
- So you first pass in the estimator object, or that is the classifier or regression object to use, followed by the data set samples X and target values Y, the name of the parameter to sweep, and the array of parameter values that that parameter should take on in doing the sweep.
- It will return two two-dimensional arrays corresponding to evaluation on the training set and the test set. Each array has one row per parameter value in the sweep, and the number of columns is the number of cross-validation folds that are used.

    ```python
    from sklearn.svm import SVC
    from sklearn.model_selection import validation_curve

    param_range = np.logspace(-3, 3, 4)
    train_scores, test_scores = validation_curve(SVC(), X, y,
                                    param_name='gamma',
                                    param_range=param_range, cv=3)
    ```

#### Learning Curve

- It used to detect if the model is underfitting or overfitting, and impact of training data size the error.
- It plots the training dataset and validation dataset error or accuracy against training set size.
- scikit-learn: `sklearn.learning_curve.learning_curve`
  - Uses stratified k-fold cross-validation by default if output is binary or multiclass (preserves percentage of samples in each class)
  - Note: `sklearn.model_selection.learning_curve` in v0.18

#### Model Debugging

- Filter on failed predictions and manually look for patterns.
  - Data problems (eg, many variants for same word)
  - Labeling errors (eg, data mislabelled)
  - Under/over-represented subclasses (eg, too many examples of one type)
  - Discriminating information is not captured in features (eg, customer location)
- This helps pivot on target, key attributes, and failure type, and build histograms of error counts.

    ```py
    pred = clf.predict(train[col])
    error_df = test[pred != test['target']]
    ```

### Feature Engineering

- It is the art of extracting more information from the existing data in order to improve the model's predictive power.
- There are two ways:
  - Reduce the dataset dimensionality using Feature Extraction and Feature Selection.
  - Increase the dataset dimensionality using Feature Creation and Transformation.
- This leads to Curse of Dimensionality where the model performance reaches its optimal state at certain number of features, however it drastically decreases by increasing the number of features any further.
- ![Curse of dimensionality graph](ML%20images/Dimensionality_Curse.png)

#### Feature Extraction

- It is a technique used to reduce the dimensionality of the dataset.
  - a.k.a data compression
- It is the extraction of new features from the existing features in the dataset.
- It is considered old school and deep learning techniques are more efficient now.
- Motivation:
  - Improves computational efficiency
  - Reduces curse of dimensionality
- It is used in:
  - Images: extracting a certain components of the image to identify the image.
  - NLP: Popular words excluding articles and prepositions.
  - Structured data: Principle component analysis (PCA) or t-distributed stochastic neighbor embedding (T-SNE)
- Techniques
  - Principle component analysis (PCA)
    - It is unsupervised linear approach to feature extraction
    - Finds pattern based on correlations between features
    - Constructs principal components: orthogonal axes in directions of maximum variance.
    - scikit-learn: `sklearn.decomposition.PCA`

        ```py
        pca = PCA(n_components=2)
        X_train_pca = pca.fit_transform(X_train_std)
        lr = LogisticRegression()
        lr.fit(X_train_pca)
        ```

  - Linear discriminant analysis (LDA)
    - A supervised linear approach to feature extraction
    - Transforms to subspace that maximizes class separability
    - Assumes data is normally distributed
    - Used for dimensionality reduction of features
    - Can reduce to at most #classes-1 components
    - scikit-learn: `sklearn.discriminant_analysis.LinearDiscriminantAnalysis`
  - Kernel versions of these for fundamentally non-linear data

#### Feature Selection

- It is a technique used to reduce the dimensionality of the dataset.
- It is by leaving only one of the highly correlated features.
- Filtering is a technique in Feature selection, which is eliminating the irrelevant data.

#### Feature Creation and transformation

- It is a technique used to increase the dimensionality of the dataset.
- It is the creation of new features using already existing data.
  - For example:
    - Creating a feature which is the multiplication of two other features.
    - Or creating new features by splitting an already existing feature.
- Techniques for Numerical Data:
  - Logarithmic transformation:
    - It is about changing the shape of the distribution plot.
    - It can be applied to right skewed plots.
    - It can not be applied to 0 or -ve values.
  - Square:
    - It can not be applied to negative values
    - It has moderate impact on distribution
    - Ex: Area of apartment
  - Cube:
    - It can be applied to negative numbers
    - It has high impact on distribution
    - Volume of rainfall in a year.
  - Binning:
    - It is the converting the values of a feature into features of ranges of the numbers.:
      - Ex: Converting Age column into columns of ranges. (0 to 7 years), (8 - 16 years) ....
  - Scaling:
    - It is the normalization of the feature values:
    - Techniques:
      - **Mean/Variance standardization**:
        - Centering the values around mean $\mu_j = 0$ with standard deviation $\sigma_j = 1$ for each column.
        - This can be achieved by removing the mean from the variable and divide it with the standard variance.
        - $$x_{i,j}^* = \frac{x_{i,j} - \mu_j}{\sigma_j}$$
        - Advantages:
          - Many algorithms behave better with smaller values
          - Keeps outlier information, but reduces impact.
        - SciKit-learn: `sklearn.preprocessing.StandardScalar`
      - **MinMax Scaling**:
        - It is the transformation of all the features, so they're all on the same scale between zero and one.
        - $$x_{i,j}^* = \frac{x_{i} - \min x_j}{\max x_j - \min x_j}$$
        - Advantages:
          - Robust to small standard deviations
        - SciKit-learn: `sklearn.preprocessing.MinMaxScaler`
      - **MaxAbs scaling**:
        - Divides each element by the maximum absolute value in the feature.
        $$x_{i,j}^* = \frac{x_{i,j}}{\max (|x_j|)}$$
        - Advantages:
          - It doesn't destroy sparsity, because there observations are not centered around any measurement
        - SciKit-learn: `sklearn.preprocessing.MaxAbsScaler`
      - **Robust scaling**
        - It is applied to particular features.
          $$x_{i}^* = \frac{x_{i} - Q_{50}(x)}{Q_{75}(x) - Q_{25}(x)}$$
        - Advantages:
          - Minimizes the impact of large marginal outliers.
          - After transformation, it will be robust outliers
        - SciKit-learn: `sklearn.preprocessing.RobustScaler`
      - **Normalizer**:
        - It is applied to rows.
        - Scaled values are scaled with standard deviation $\sigma_j = 1$
          $$x_{i,j}^* = \frac{x_{i,j}}{\sigma_j}$$
        - SciKit-learn: `sklearn.preprocessing.Normalizer`
        - Rescales $x_j$ to unit norm based on:
          - L1 norm
          - L2 norm
          - Max norm
        - It is widely used in text analysis.
    - Critical aspects to Feature Engineering:
      - The scalar is fit to the training data only, then transform both train and validation data.
        1. Apply the same scalar object to both training and testing data.
        2. Training the scalar object on the training data and not on the test data. If it trained on the test data, it will cause a phenomena called Data Leakage, where the training phase has information that is leaked from the test set.
      - The scaling should applied to the real world numbers not only to that available in the dataset. For example: If the dataset has Age column that ranges from 20 to 50, this doesn't neglect the fact that Ages in real world can range from 0 to 80 or 100. So, this should be taken in consideration while scaling in order to generalize the model to the real world.
      - Scaling is applied differently to each column
    - Polynomial Features
      ![Polynomial-Features_equation](ML%20images/Polynomial&#32;features&#32;equation.jpg)
      - Generate new features consisting of all polynomial combinations of the original two features $𝑥_0,𝑥_1$.
      - The degree of the polynomial specifies how many variables participate at a time in each new feature (above example: degree 2).
      - This is still a weighted linear combination of features, so it's still a linear model, and can use same least-squares estimation method for $w$ and $b$.
      - Adding these extra polynomial features allows us a much richer set of complex functions that we can use to fit to the data.
      - This intuitively as allowing polynomials to be fit to the training data instead of simply a straight line, but using the same least-squares criterion that minimizes mean squared error.
      - We want to transform the data this way to capture interactions between the original features by adding them as features to the linear model.
      - Polynomial feature expansion with high as this can lead to complex models that over-fit.
      - Polynomial feature expansion is often combined with a regularized learning method like ridge regression.
- Techniques for categorical data:
  - Ordinal categories:
    - Convert binary classifications to 0 and 1
    - Mapping multi categorical features to numerics with the assistance of the domain expert. For example: mapping Small, Medium, Large to 5, 10, and 20.
  - Nominal categories:
    - One Hot Encoding:
      - It is creating a binary column for each of the classes in the feature.
      - Pandas: `pandas.get_dummies()`
    - Grouping:
      - Create a binary column for a group of features together.
- Other techniques:
  - Radial Basis Function
    - Transform: $f(x) = f(||x - c||)$
    - Widely used in Support Vector Machine as a kernel and in Radial Basis Networks (RBNNs)
    - Gaussian RBF is the most common RBF used.
  - Text-based Features
    - Bag-of-words model
      - Represent document as vector of numbers, one for each word (tokenize, count, and normalize)
      - Note:
        - Sparse matrix implementation is typically used, ignores relative position of words.
        - Can be extended to bag of n-grams of words or of characters
    - Count Vectorizer
      - Per-word value is count (also called term frequency)
      - Note: Includes lowercasing and tokenization on white space and punctuation
      - scikit-learn: `sklearn.feature_extraction.text.CountVectorizer`
    - TfidfVectorizer
      - Term-Frequency times Inverse Document-Frequency
      - Per-word value is downweighted for terms common across documents (eg. "the")
      - scikit-learn: `sklearn.feature_extraction.text.TfidfVectorizer`
    - Hashing Vectorizer
      - Stateless mapper from text to term index
      - scikit-learn: `sklearn.feature_extraction.text.HashingVectorizer`

#### Bagging/Boosting

Feature extraction and selection are relatively manual processes. Bagging and boosting are automated or semi-automated approaches to determining which features to include.

- Bagging (Bootstrapping Aggregation)
  - Generate a group of weak learners that when combined together generate higher accuracy
  - Reduces variance
  - Keeps bias the same
  - sklearn:
    - `sklearn.ensemble.BaggingClassifier`
    - `sklearn.ensemble.BaggingRegressor`

- Boosting
  - Assign strengths to each weak learner
  - Iteratively train learners using misclassified examples by previous weak learners.
  - It is used for models that have a high bias and accepts weights on individual samples
  - sklearn:
    - `sklearn.ensemble.AdaBoostClassifier`
    - `sklearn.ensemble.AdaBoostRegressor`
    - `sklearn.ensemble.GradientBoostingClassifier`
  - XGBoost library

## ML Data Readiness

- ML data readiness is the capability to evaluate readiness, or worthiness, of datasets for use in an ML based predictive solution.

- ML data readiness evaluation is typically done prior to embarking on an ML project. It can help:

  - Evaluate the predictive potential of the dataset
  - Identify predictive outcomes that can be supported
  - Build initial ML models and understand relative performance

## Productizing a ML Model

### Aspects to consider

- Model Hosting
- Model deployment
- Pipeline to provide features vectors
- Code to provide low-latency and/or high-volume predictions
- Model and data updating and versioning
- Quality monitoring and alarming
- Data and model security and encryption
- Customer privacy, fairness, and trust
- Data provider contractual constraints (eg., attribution, cross-fertilization)

1. ### Overfitting

   - Failure to generalize: Model performs well on training set but poorly on test set
   - Typically indicates that model is too flexible for amount of training data
   - Flexibility allows it to "memorize" the data, including noise
   - Corresponds to high variance - small changes in the training data lead to big changes in the results

2. ### Underfitting

   - Failure to capture important patterns in the training data set
   - Typically indicates model is too simple or there are too few explanatory variables
   - Not flexible enough to model real patterns
   - Corresponds to high bias - the results show systematic lack of fit in certain regions

- To avoid these, the below points would help:
  1. First, try to draw the data with respect to the labels and try to figure out the relationship between, whether its linear, quadratic, polynomial and so on.
  2. Reduce the number of features.
     1. Manually select which features to keep.
     2. Use a model selection algorithm.
  3. Regularization
     1. Keep all the features, but reduce the magnitude of parameters.
     - It works well when there are a lot of slightly useful features.

### Types of Production environments

#### Batch predictions

- Useful if all possible inputs known a priori (eg., all product categories for which demand is to be forecast, all keywords to bid)
- Predictions can still be served real-time, simply read from pre-computed values

#### Online Predictions

- Useful if input space is large (e.g., customer's utterances or photos, detail pages to be translated)
- Low latency requirement (e., at most 100ms)

#### Online training

- Sometimes training data patterns change often, so need to train online (eh., fraud detection)

### Business metrics vs Model Metrics

- Business metrics may not be the same as the performance metrics that are optimized during training. Why?
  - click-through rate
- Ideally, performance metrics are highly correlated with business metrics.

### Storage

- Row-oriented formats:
  - comma/tab-separated values (CSV/TSV)
  - Read-only DB (RODB): Internal read-only file-based store with fast key-based access
  - Avro: allows schema evolution for Hadoop
- Column-oriented formats:
  - Parquet: Type-aware and indexed for Hadoop
  - Optimized row columnar (ORC): Type-aware, indexed, and with statistics for Hadoop
- User-defined formats:
  - JavaScript object notation (JSON): For key-value objects
  - Hierarchical data format 5 (HDF5): Flexible data model with chunks
- Compression can be applied to all formats
- Usual trad-offs: Read/write speeds, size, platform-dependency, ability for schema to evolve, schema/data separability, type richness

### Model and Pipeline Persistence

- Predictive Model Markup Language (PMML):
  - Vendor-independent XML-based language for storing ML models
  - Support varies in different libraries:
    - KNIME (analytics/ML library): Full Support
    - Scikit-learn: Extensive support
    - Spark MLlib: Limited Support

- Custom methods:
  - Scikit-learn: Uses the Python pickle method to serialize/deserialize Python objects
  - Spark MLlib: Transformers and Estimators implement ML Writable
  - TensorFlow (deep learning library): Allows saving of MetaGraph
  - MxNet (deep learning library): Saves into JSON

### Model Deployment

- It is the integration of the model and its resources into a production environment so that it can be used to create predictions.
- Technology transfer: Experimental framework may not suffice for production
  - A/B testing or shadow testing: Helps catch production issues early

### Monitoring

- It is important to monitor quality metrics and business impacts with dashboards, alarms, user feedback, etc.:
  - The real-world domain may change over time.
  - The software environment may change.
  - High profile special cases may fail.
  - There may be a change in business goals.

### Maintenance

- Performance deterioration may require acquire new tuning:
  - Changing goals may require new metrics.
  - A changing domain may require changes to validation set.
  - Your validation set may be replaced over time to avoid overfitting.

## Common Mistakes

- You solved the wrong problem
- The data was flawed
- The solution didn't scale
- Final result doesn't match with the prototype's results.
- It takes too long to fail
- The solution was too complicated
- There weren't enough allocated engineering resources to try out long-term science ideas.
- There was a lack of a true collaboration.

## References

- [A Comprehensive Guide To Data Imputation](https://towardsdatascience.com/a-comprehensive-guide-to-data-imputation-e82eadc22609)
- [Matt Brems Repo](https://github.com/matthewbrems/missing-data-workshop?fbclid=IwAR1LGjaIen-ITLndPN1ODV1lYZBvxsHDs0DgIaPkuxpXMsQRBT8eAPI-0sI)
- [Geeks for Geeks](https://www.geeksforgeeks.org/regularization-in-machine-learning/)
- [Towards Data Science](https://towardsdatascience.com/regularization-what-why-when-and-how-d4a329b6b27f)
- [Medium article](https://medium.com/analytics-vidhya/understanding-regularization-algorithms-450777fa0ed3)
- AWS Pipeline course
- [Pluralsight MOOC](https://app.pluralsight.com/library/courses/creating-machine-learning-models)
