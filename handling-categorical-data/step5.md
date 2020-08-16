# Encoding Dictionaries of Features

In the previous steps, we have dealt with ordinal and nominal categorical features and encoded them into numerical values. We used the Estonia disaster dataset as an example there. This time, we will deviate to an entirely different case-study - **Natural Language Processing** which deals with textual data.

In order to understand the importance of encoding dictionaries, let's take an example. Recall the last book you read. The number of distinct words would have been extremely small as compared to their occurrence in the book. To store such word counters, we typically use sparse matrices which are used to store large matrices with mostly zeros extremely efficiently.

Let's take an example of a quote from the **Sherlock** BBC series:

> "Oh, hell! What does that matter?! So we go around the sun! If we went around the moon or round and round the garden like a teddy bear, it wouldn’t make any difference! All that matters to me is the work! Without that, my brain rots. Put that in your blog — or better still, stop inflicting your opinions on the world!"

Now if we count the occurrence of unique words (without caring about the case of the word), then we end up with the following.

| Word | Count |
| --- | --- |
| the | 5 |
| that | 4 |
| we | 2 |
|around | 2 |
| or | 2 | 
| round | 2 |
| your | 2 |
| oh | 1 |
| what | 1 |
| --- | --- |
