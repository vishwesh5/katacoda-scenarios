# Encoding Dictionaries of Features

In the previous steps, we have dealt with ordinal and nominal categorical features and encoded them into numerical values. We used the Estonia disaster dataset as an example there. This time, we will deviate to an entirely different case-study - **Natural Language Processing** which deals with textual data.

In order to understand the importance of encoding dictionaries, let's take an example. Recall the last book you read. The number of distinct words would have been extremely small as compared to their occurrence in the book. To store such word counters, we typically use sparse matrices which are used to store large matrices with mostly zeros extremely efficiently.

Let's take an example of a quote from the **Sherlock** BBC series:

> "Oh, hell! What does that matter?! So we go around the sun! If we went around the moon or round and round the garden like a teddy bear, it wouldn’t make any difference! All that matters to me is the work! Without that, my brain rots. Put that in your blog — or better still, stop inflicting your opinions on the world!"

Now let's consider the following 5 sentences.

1. What does that matter?! So we go around the sun!
2. All that matters to me is the work! Without that, my brain rots.
3. If we went around the moon or round and round the garden like a teddy bear, it wouldn’t make any difference!
4. Put that in your blog — or better still, stop inflicting your opinions on the world!
5. Oh, hell!

We will only focus on these 4 words: `blog`, `that`, `we`, `around`, `oh` and create a dictionary describing the count of these 4 words in each of the above 5 sentences.

This is what we end up with.

```
data_dict = [{"that":1,"we":1,"around":1},
	     {"that":2},
	     {"we":1,"around":1},
	     {"blog":1,"that":1},
	     {"oh":1}]
```{{execute}}

Let's now convert this data dictionary to a feature matrix using Scikit-Learn's `DictVectorizer`.

```
# Import library
from sklearn.feature_extraction import DictVectorizer

# Create dictionary vectorizer
dictvectorizer = DictVectorizer(sparse=False)

# Convert dictionary to feature matrix
features = dictvectorizer.fit_transform(data_dict)

# View feature matrix
print(features)
``` {{execute}}

By default, we get a sparse matrix, but it is a bit difficult to make sense out of it, so, we have specified `sparse=False` to create a dense matrix.

We can create a `DataFrame` out of the above feature matrix for better visualization.

```
# Get feature names
feature_names = dictvectorizer.get_feature_names()

# Create dataframe from features
print(pd.DataFrame(features, columns=feature_names))
```{{execute}}

In this set, we saw how to use `DictVectorizer` to convert a list of dictionaries to a feature matrix and how it can be used in NLP domain.
