# Encoding Nominal Categorical Features

**Nominal Categories** are classes without any order. Think about the `Country` column in our dataset, can we state that any of the below 3 statements are correct?

- `Sweden` > `Estonia`
- `Sweden` = `Estonia`
- `Sweden` < `Estonia`

No, right? The reason being that there is no intrinsic order in these two countries (Sweden and Estonia). In cases like these, we use **one-hot encoding** technique.

One-hot encoding technique gets its name from the fact that we set a value in a list to 1 wherever a specific class occurs. To understand it better, let's convert `Country` column to 0s and 1s, where a `1` means `Sweden` and `0` means `Estonia`. Since we are only setting one value to 1, it is referred to as "one-hot encoding". Moreover, since we have only 2 categories in this `Country` feature, we can use Scikit-Learn's `LabelBinarizer`

Let's now see how we can use the `LabelBinarizer`.

We will start off by importing the required modules.

```
import numpy as np
from sklearn.preprocessing import LabelBinarizer
``` {{execute}}

Next, we will extract the `Country` column.

```
feature = df.Country
print(feature)
``` {{execute}}

The final step is to create and fit a `LabelBinarizer` and use it to transform the `feature` data.

```
# Create one-hot encoder
one_hot = LabelBinarizer()

# One-hot encode feature
one_hot.fit_transform(feature)
```{{execute}}

We can use the `classes_` method to find the corresponsing classes.

```
print(one_hot.classes_)
```{{execute}}

If you want to obtain the original classes using the encoded features, we can use `inverse_transform` method.

```
# Reverse one-hot encoding
one_hot.inverse_transform(one_hot.transform(feature))
``` {{execute}}

Similarly, we can also use Pandas `get_dummies` function for one-hot encoding as shown below.

```
# Create dummy variables from feature
pd.get_dummies(feature)
``` {{execute}}

And that's it! Here we saw how to use one-hot encoding for binary classes using Pandas and Scikit-Learn modules. Next, we will see how we can encode multi-class features using `MultiLabelBinarizer`.
