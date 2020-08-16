# Reviewing the Data

Before we get started in the details of how to encode categorical features, let's understand the data we will be dealing with throughout the scenario.

The dataset has been taken from Kaggle's [The Estonia Disaster Passenger List](https://www.kaggle.com/christianlillelund/passenger-list-for-the-estonia-ferry-disaster) which contains the details of the passengers and crew members aboard the ferry Estonia which met a tragic accident in September 1994 resulting in an unfortunate demise of more than 850 people.

We have used the data as reference and modified it in order to align it to the topics we will be covering here.

Let's get a look at the top 5 rows in the data.

```
import numpy as np

# Feature matrix with categorical feature
X = np.array([[0.73,0,0],[-1.08,1,0],[-1.14,1,1],
	      [0.62,1,0],[0.73,0,0],[1.62,0,0],
	      [1.01,1,0],[-1.31,0,1],[0.65,1,0],
	      [-0.53,0,1]])

print(X)
``` {{execute}}

Here's a description of the columns present in the data:
1. `Age` - The age of the passenger (the values have been normalized)
2. `Category` - The type of the passenger, `1` refers to **Crew Member** and `0` refers to **Passenger**
3. `Survived` - Whether the passenger survived, `1` refers to **YES** and `0` refers to **NO**

Let's also go over some new samples we have obtained with some missing values.

```
# Feature matrix with missing values
# in the categorical feature
X_with_nan = np.array([[-0.76,0,np.nan],[0.68,1,np.nan]])

print(X_with_nan)
```{{execute}}

Now that we have reviewed the data, let's move on to the next steps.

**Note**: This problem will look very close to a binary classification problem. This is not by chance. Here we are considering all the 3 columns to be feature columns so it's a simple missing data problem. As soon as we consider the `Survived` column (column number 3) to be a target column, the problem becomes a classification problem. It's very important to understand the difference between the two.
