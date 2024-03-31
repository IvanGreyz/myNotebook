# Machine Learning Fundamental
---

## 1. What is Machine Learning?🤖

For short, **Machine learning (ML)** is a subfield of artificial intelligence that uses algorithms trained on data sets to create models that enable machines to perform tasks that would otherwise only be possible for humans, such as categorizing images, analyzing data, or predicting price fluctuations.

So, *building a ML is to train a ML model on data sets, using that data to adjust ML scalars to predict something with an input*.   


### 1.1 Machine Learning Classification📋
Base on the data sets, the ML models are classified:
* Supervised machine learning:

*In Supervised machine learning, algorithms are trained on labeled data sets that include tags describing each piece of data.
In other words, the algorithms are fed data that includes an “answer key” describing how the data should be interpreted.
For example, an algorithm may be fed images of flowers that include tags for each flower type so that it will be able to identify the flower better again when fed a new photograph.*

* Unsupervised machine learning:

*Unsupervised machine learning uses unlabeled data sets to train algorithms. 
In this process, the algorithm is fed data that doesn't include tags, which requires it to uncover patterns on its own without any outside guidance. 
For instance, an algorithm may be fed a large amount of unlabeled user data culled from a social media site in order to identify behavioral trends on the platform.*
  
* Semi-supervised machine learning:

*Semi-supervised machine learning uses both unlabeled and labeled data sets to train algorithms.
Generally, during semi-supervised machine learning, algorithms are first fed a small amount of labeled data to help direct their development and then fed much larger quantities of unlabeled data to complete the model. For example, an algorithm may be fed a smaller quantity of labeled speech data and 
then trained on a much larger set of unlabeled speech data in order to create a machine learning model capable of speech recognition.*
  
* Reinforcement learning:

*Reinforcement learning uses trial and error to train algorithms and create models.
During the training process, algorithms operate in specific environments and then are provided with feedback following each outcome.
Much like how a child learns, the algorithm slowly begins to acquire an understanding of its environment and begins to optimize actions to achieve particular outcomes. 
For instance, an algorithm may be optimized by playing successive games of chess, which allows it to learn from its past successes and failures playing each game.*

### 1.1 Machine Learning Building👣
To bulid a Machine learning model, we need to following these steps:
1. Collecting Data
2. Preparing the Data
3. Choosing a Model
4. Training the Model
5. Evaluating the Model and Retrain it
6. Parameter Tuning

Here is an example about building Machine learning:

```python
# Import library
import pandas as pd
from sklearn.metrics import mean_absolute_error          # Calculate the loss value after training loop
from sklearn.model_selection import train_test_split     # Split the data
from sklearn.tree import DecisionTreeRegressor           # The training model: Decision Tree


# Path of the file to read
iowa_file_path = '../input/home-data-for-ml-course/train.csv'

home_data = pd.read_csv(iowa_file_path)
# Create target object and call it y
y = home_data.SalePrice
# Create X
features = ['LotArea', 'YearBuilt', '1stFlrSF', '2ndFlrSF', 'FullBath', 'BedroomAbvGr', 'TotRmsAbvGrd']
X = home_data[features]

# Split into validation and training data
train_X, val_X, train_y, val_y = train_test_split(X, y, random_state=1)

# Specify Model
iowa_model = DecisionTreeRegressor(random_state=1)
# Fit Model
iowa_model.fit(train_X, train_y)

# Make validation predictions and calculate mean absolute error
val_predictions = iowa_model.predict(val_X)
val_mae = mean_absolute_error(val_predictions, val_y)
print("Validation MAE when not specifying max_leaf_nodes: {:,.0f}".format(val_mae))

# Using best value for max_leaf_nodes
iowa_model = DecisionTreeRegressor(max_leaf_nodes=100, random_state=1)
iowa_model.fit(train_X, train_y)
val_predictions = iowa_model.predict(val_X)
val_mae = mean_absolute_error(val_predictions, val_y)
print("Validation MAE for best value of max_leaf_nodes: {:,.0f}".format(val_mae))

###

# import Random Forest model
from sklearn.ensemble import RandomForestRegressor

# Define the model. Set random_state to 1
rf_model = RandomForestRegressor(random_state=1)

# fit your model
rf_model.fit(train_X, train_y)

# Calculate the mean absolute error of your Random Forest model on the validation data
rf_val_mae = mean_absolute_error(val_y, rf_model.predict(val_X))

print("Validation MAE for Random Forest Model: {}".format(rf_val_mae))

```
---
🐍Nowaday, Python is the programming language suitable for engineering, Physicist, mathematician, visualize, data processing and also training data due to the hug libraries. 
The more expert at using Python libraries, the more efficient you for your work! Here are some useful library: 
* Numpy: handle array and matrices
* Pandas: be created for data sets
* Matplotlib: visualize data
* OpenCV: image processor 
* Scipy: algebra processor
* Scikit-learn: provide machine learning tool
* PyTorch: provide deep learning tool
