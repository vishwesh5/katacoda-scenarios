# Reviewing the Data

Before we get started in the details of how to encode categorical features, let's understand the data we will be dealing with throughout the scenario.

The dataset has been taken from Kaggle's [The Estonia Disaster Passenger List](https://www.kaggle.com/christianlillelund/passenger-list-for-the-estonia-ferry-disaster) which contains the details of the passengers and crew members aboard the ferry Estonia which met a tragic accident in September 1994 resulting in an unfortunate demise of more than 850 people.

We have used the data as reference and modified it in order to align it to the topics we will be covering here.

Let's get a look at the top 5 rows in the data.

```
import pandas as pd

df = pd.DataFrame({
    "PassengerId":[1,2,3,4,5,6,7,8,9,10],
    "Country":["Sweden","Estonia","Estonia","Sweden","Sweden","Sweden","Sweden","Estonia","Estonia","Sweden"],
    "Origin_Current":[("Sweden","Estonia"),("Estonia","Sweden"),("Estonia","Sweden"),("Sweden","Norway"),("Sweden","Finland"),("Sweden","Russia"),("Sweden","Estonia"),("Estonia","Latvia"),("Estonia","Sweden"),("Sweden","Estonia")],
    "Age-group":["51-60","21-30","21-30","51-60","51-60","71-80","51-60","11-20","21-30","31-40"],
    "Category":["P","C","C","C","P","P","P","P","C","P"],
    "Survived":["NO","NO","YES","NO","NO","NO","NO","YES","NO","YES"]
   })

print(df.head())
``` {{execute}}

Here's a description of the columns present in the data:
1. `PassengerId` - ID number for the passenger/crew member
2. `Country` - Country of origin of passenger/crew member
3. `Origin_Current` - Contains a combination of country of birth and country where the passenger was staying at the time
4. `Age-group` - The age group to which the passenger belongs to
5. `Category` - The type of the passenger, `C` refers to **Crew Member** and `P` refers to **Passenger**
6. `Survived` - Whether the passenger survived

Now that we have reviewed the data, let's move on to the next steps.
