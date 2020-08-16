# Downsampling the majority class

In the previous step, we discussed about the concept of class weights. While they are usually very effective in dealing with class imbalance, they can cause an unstability in the model training which can cause the model loss to go haywire. The other common way of handling imbalanced dataset is by increasing the number of samples belonging to the minority class (class with lesser number of samples in the original dataset) or by decreasing the number of samples belonging to the majority class (class with larger number of samples in the original dataset). The first technique is referred to as **upsampling** since we are **increasing** the number of samples in the dataset and the second one is referred to as **downsampling** since we are **decreasing** the number of samples in the dataset.

Let's start off with how to downsample the majority class.

Since we saw earlier that we have 137 samples from class 1 (passengers who survived), we can reduce the number of samples from class 0 (those who did not survive) to 137 to get a perfectly balanced dataset. Of course, we can go for a larger number as well if we don't want to reduce the number of samples in the dataset this much.

Here's how we can downsample the class 0 samples.

First, we will find out the indices of each class' observations.

```
import numpy as np

features = df.drop("Survived",axis=1).values
target = df.Survived.values

i_class0 = np.where(target == 0)[0]
i_class1 = np.where(target == 1)[0]

# Number of observations in each class
n_class0 = len(i_class0)
n_class1 = len(i_class1)
```{{execute}}

Next, for every observation of class 1, we will randomly sample from class 0 without replacement.

```
i_class0_downsampled = np.random.choice(i_class0, size=n_class1, replace=False)
```{{execute}}

We can now merge the downsampled indices from class 0 and indices from class 1 to create a balanced dataset.

```
# Display only first 10 values
np.hstack((target[i_class0_downsampled], target[i_class1]))[:10]
```{{execute}}

We can similarly stack together the features to create a balanced feature matrix.

```
np.vstack((features[i_class0_downsampled,:], features[i_class1,:]))[:10]
```{{execute}}

One main thing to note here is that by downsampling the majority class, we ended up with only 137*2 or 274 samples in place of the original 989 samples. That's about 27.7% of the original dataset. That's a significantly small percentage and this percentage would have been even smaller if the class imbalance would have been larger. The other solution is to use upsampling which actually increases the number of samples in the dataset. We will see how to use it in the next step.
