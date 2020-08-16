# Imputing missing values using k-NN classifier

The first approach we will be considering for imputing missing **categorical** values is a k-Nearest Neighbor (k-NN) classifier.

If you are new to the term "k-NN", then don't panic. The idea behind k-Nearest Neighbor is very simple. First, focus on the term "nearest neighbor" which in our context means points lying close to a given point. The "closeness" refers to the distance between two points. The lesser is the distance between two points, the closer or nearer they are. Extending this idea, k-nearest neighbors are **k** points which are the closest to a given point.

The k-NN classifier says that a point behaves like its neighbors. So, if a majority of the k-nearest neighbors belong to a class 1, then the point in consideration will also belong to class 1.

We will now use the same concept to predict the missing categorical value as shown below.

First, we will train the kNN classifier on the complete data we have. For this, we will use Scikit-Learn's `KNeighborsClassifier`.

```
from sklearn.neighbors import KNeighborsClassifier

# Train KNN learner
clf = KNeighborsClassifier(3, weights='distance')
trained_model = clf.fit(X[:,:2], X[:,2])
``` {{execute}}

Next, we can simply use the trained model to predict the missing categorical values.

```
# Predict missing values' class
imputed_values = trained_model.predict(X_with_nan[:,:2])

# Join column of predicted class with their other features
X_with_imputed = np.hstack((X_with_nan[:,:2],imputed_values.reshape(-1,1)))

# Join two feature matrices
np.vstack((X_with_imputed, X))

``` {{execute}}

And there we go! We have found the missing categorical values for the `Survived` column (feature).

Now, just like the saying goes, *with great power, comes great responsibility*. kNN classifier is a very powerful Machine Learning algorithm but it can get extremely resource consuming if we are dealing with big data problems. This calls for a simpler and less computationally expensive method for imputing missing values. We will read about this alternative solution in the next step.
