# Handling Missing Values

Before we jump into the different techniques for imputing the missing values, let's quickly understand the options that we have for dealing with the missing values.

Overall, there are three ways of handling missing values-
1. Removing the columns having missing values
2. Removing the rows having missing values
3. Imputing the missing values

The choice among the above three depends on the data and the problem statement. For example, when you notice that a particular column has, say 80% missing values, then it's better to just drop the column, provided it does not have a high importance for your case study.

Similarly, when you notice that a very small percentage of rows (let's say 2% of the entire data) have missing values, you can choose to drop the rows rather than dropping the columns. Again, this is not preferred when you are dealing with small scale data (for example, around the size of a hundred rows).

Imputing the missing values, which refers to filling in the missing values, is usually the best choice but, one has to be very careful in selecting the values to impute since any incorrect choice can pollute the entire data. And at the end, remember the famous saying in Data Science and Machine Learning domain - **Garbage In, Garbage Out**. This conveys the importance of making sure that the data fed into the Machine Learning algorithm is of high quality.

Now that we have understood the options we have for handling the missing values, let's go in deep to learn how to use k-NN model for imputing the missing values.
