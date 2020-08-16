# Using class weights for handling imbalance

In the previous steps we have discussed about the concept of class imbalance and why it's an important thing to watch out for while building the model. In this step, we will go over how we can deal with class imbalance using the concept of class weights while training a Random Forest classifier.

If you are not familiar with Random Forest classifier, just think of it like a Machine Learning algorithm for classification. The main idea to focus on here is the `class_weight` argument.

Let's first understand what are class weights. Class weights refer to the weightage given to the samples of of a particular class in order to counter the effect of the class imbalance. Suppose that there are 10 samples of one class and 100 samples of other class, then every one sample of the first class will carry 10 times the weightage of a sample from other class.

Class weight can be calculated using different methods. Here, we will simply use the inverse of relative frequency of a class as its weight. For example, if class 0 has 10 samples out of total 110 samples, then it will have a weight of 110/10 which is equal to 11. Class 1 on the other hand has 100 samples out of total 110 samples, so it will have a weight of 110/100 or 1.1.

Using the same concept, in the case of our dataset, the class weights will be as follows:

```
weights = {0: 989/852, 1: 989/137}
```{{execute}}

Now, let's create a Random Forest classifier with the above class weights.

```
# Create random forest classifier with weights
RandomForestClassifier(class_weight=weights)
```{{execute}}

We could have skipped the calculation of class weights, by simply using the keyword `"balanced"` as shown below.

```
# Create random forest classifier
RandomForestClassifier(class_weight="balanced")
```{{execute}}

Since our focus here was only to understand how to deal with imbalance of classes, we won't go into the details of how to train the classifier but you are welcome to give it a shot. It will be a great learning experience.

In this step, we saw how to find out class weights and use them in a Machine Learning algorithm to counter the class imbalance. In next steps, we will go over different sampling techniques which increase or decrease the number of samples from the minority or the majority class, respectively, to handle class imbalance.
