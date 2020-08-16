# Encoding Ordinal Categorical Features

**Ordinal Categories** are classes that have an inherent order in the values. For example, let's consider the age group group column in our dataset. Since we have distinct values possible in this column, we will call it a categorical feature, but there is a clear order in the values: age-group `11-20` is lesser than age-group `21-30` and so on.

While encoding the ordinal categories, we convert them into numerical values in a manner that retains the order as well. As an example, we can convert `11-20` to `0` and `21-30` to 1, and so on.

We can use the Pandas `replace` method to encode the ordinal categorical features as shown below.

To start off, we will define a mapper which will mention the conversion of a category to a numerical value. Since we have age-groups ranging from `11-20` to `71-80`, we can assign them numbers starting from 0.

```
# Create mapper
scale_mapper = {"11-20":0,
		"21-30":1,
		"31-40":2,
		"41-50":3,
		"51-60":4,
		"61-70":5,
		"71-80":6}
```{{execute}}

Now we can use this mapper along with Pandas `replace` function to encode the `Age-group` column.

```
# Replace feature values with scale
df["Age-group"].replace(scale_mapper)
```{{execute}}

The interesting point to note here is that it's not necessary for the numbers to be integers. Depending on the context of the problem, we can even assign floating point numbers to an ordinal category.

In this step we saw how we can use `replace` function to encode ordinal categorical features. Next, we will see how we can encode a Python dictionary to a feature matrix using `DictVectorizer`.
