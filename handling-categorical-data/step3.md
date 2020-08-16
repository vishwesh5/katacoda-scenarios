# Encoding Nominal Multiclass Features

In the previous step, we saw how we can use `LabelBinarizer` and `get_dummies` methods for encoding nominal binary class features. But, imagine the scenario where you have multi-class features (for example, country of origin and country where the passenger was staying currently). In such cases, you can simply use `MultiLabelBinarizer` from Scikit-Learn package to encode the feature.

Let's see how we can do the same. First, we will extract the feature column - `Origin_Current`.

```
# Extract the multiclass feature column
multiclass_feature = df.Origin_Current
```{{execute}}

Next, just like we did in the case of `LabelBinarizer`, we will first create and fit the multi-class encoder and then use it to transform our multi-class feature column.

```
from sklearn.preprocessing import MultiLabelBinarizer
# Create multiclass one-hot encoder
one_hot_multiclass = MultiLabelBinarizer()

# One-hot encode multiclass feature
one_hot_multiclass.fit_transform(multiclass_feature)
``` {{execute}}

Similarly, we can find out the corresponding classes using the `classes_` method.

```
# View classes
print(one_hot_multiclass.classes)
``` {{execute}}

In this step, we saw how we can encode multi-class nominal features using Scikit-Learn's `MultiLabelBinarizer`. In the next step, we will shift our focus to **ordinal categorical features**.
