# Upsampling the minority class

In the previous step we discussed about downsampling the majority class and how it results in losing a high percentage of the original data. Considering that data acquisition is an expensive step (both in terms of time and money spent), losing data is not usually preferred. That's where upsampling comes into the picture.

This time, we will sample the data points belonging to minority class in order to bring the sample count same as the majority class. Since we are not creating any new unique samples for the minority class, the sampling has to be done **with replacement**. Recall that in downsampling, the sampling was done **without replacement**.

We will start off by randomly sampling from class 1 for every observation in class 0, with replacement.

```
i_class1_upsampled = np.random.choice(i_class1, size=n_class0, replace=True)
```{{execute}}

Next, we will merge the two indices - class 0 indices and class 1 (upsampled) indices.

```
# Join together class 1's upsampled target vector with class 0's target vector
# Display only the first 10 values
np.concatenate((target[i_class0], target[i_class1_upsampled]))[:10]
```{{execute}}

Similarly, we can stack together the feature matrices to create a combined feature matrix.

```
# Join together class 1's upsampled feature matrix with class 0's feature matrix
np.vstack((features[i_class0,:], features[i_class1_upsampled,:]))[0:10]
```{{execute}}

At this point, you are aware of the advantage of using upsampling over downsampling, but can you think of a disadvantage? The major disadvantage lies in the fact that we are not creating any new samples for the minority class. We are just blatantly copying and pasting the existing samples. This can easily result in the concept called **overfitting** where model even learns the noise present in the dataset and ends up with high losses on unseen data points.

So what's the solution? We know that both upsampling and downsampling have their own cons. The other solution is to use more advanced techniques like **Synthetic Minority Over-sampling Technique** (SMOTE) which is able to generate new synthetic samples which upsampling the minority class. I encourage you to read up more on SMOTE and how to use it in Python.
