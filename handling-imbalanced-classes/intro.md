# Python ML Cookbook: Handling Imbalanced Classes

Imagine a database of COVID-19 tests conducted in India on 15th August, 2020. A total of around 747 thousand people were tested, out of which around 64 thousand people were found COVID-19 positive. This number is just about 8.5% of the total people tested. If one were to use a Machine Learning model to predict if a particular patient is COVID-19 positive or not using the data for 15th August, there is one major hurdle that the model would have to overcome.

If the model assumed all the people to be COVID-19 negative, it would still be able to achieve around 91.5% results correctly. That's a great accuracy! But, is it actually correct? NO!

In short, this is what class imbalance is all about. When a particular category has a very low frequency as compared to another category for a feature, we call the dataset imbalanced and the occurrence as "class imbalance". As we saw in the example above, it's very important to handle imbalanced classes correctly to come up with Machine Learning models which can generalize well in the real world. And this is exactly what we are going to cover in this scenario.

Let's get started!
