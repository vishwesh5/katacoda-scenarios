# Imputing missing values using SimpleImputer

In the previous step we saw how we can use kNN classifier for finding out the missing categorical values for a given feature. We also discussed how kNN is a computationally expensive algorithm and it can become troublesome when we are dealing with big data problems.

Here, we will go over the alternative solution of using Scikit-Learn's `SimpleImputer` which can find the missing categorical values following a specified `strategy`. For the ease of discussion, let's replace the missing values with the most commonly occurring values in that particular feature. This value will be referred to as the **mode** of the feature column and the `strategy` will be `most_frequent`. 

Let's see how we can use `SimpleImputer` for imputing missing values.

```
from sklearn.impute import SimpleImputer

# Join the two feature matrices
X_complete = np.vstack((X_with_nan, X))

# Define the imputer
imputer = SimpleImputer(strategy='most_frequent')

# Fit and transform the data
imputer.fit_transform(X_complete)
```{{execute}}

Do you see any differences in the results obtained using kNN and `SimpleImputer`? Think about the differences in the two algorithms. Where kNN was dependent on the **k** nearest neighbors, `SimpleImputer` is taking into account **all** the data points. So as the **k** value keeps on increasing (and eventually reaches the total number of data points), the result of kNN will start getting closer and eventually match the result obtained using `SimpleImputer`. Isn't that interesting?

In this step, we discussed about how we can use Scikit-Learn's `SimpleImputer` with `most_frequent` strategy to impute the missing categorical values.
