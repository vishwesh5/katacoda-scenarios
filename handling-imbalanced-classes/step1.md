# Reviewing the Data

Before we get started in the details of how to encode categorical features, let's understand the data we will be dealing with throughout the scenario.

The dataset has been taken from Kaggle's [The Estonia Disaster Passenger List](https://www.kaggle.com/christianlillelund/passenger-list-for-the-estonia-ferry-disaster) which contains the details of the passengers and crew members aboard the ferry Estonia which met a tragic accident in September 1994 resulting in an unfortunate demise of more than 850 people.

We have used the same dataset here in our scenario.

Let's get a look at the top 5 rows in the data.

```
import pandas as pd

df = pd.read_csv("data.csv")

print(df.head())
``` {{execute}}

Here's a description of the columns present in the data:
1. `PassengerId` - ID number for the passenger/crew member
2. `Country` - Country of origin of passenger/crew member
3. `Firstname` - First name of the passenger
4. `Lastname` - Last name of the passenger
5. `Sex` - Gender of passenger, `M` refers to Male and `F` refers to Female
6. `Age` - Age of the passenger at the time of the tragic incident
7. `Category` - The type of the passenger, `C` refers to **Crew Member** and `P` refers to **Passenger**
8. `Survived` - Whether the passenger survived

The passenger's name is not going to play an important role in the survival chances, so we can drop the 2 columns. Similarly, `PassengerId` is just a unique ID and thus can be dropped as well.

```
df.drop(["PassengerId","Firstname","Lastname"],axis=1,inplace=True)

# Display top 5 rows
print(df.head())
```{{execute}}

Finally, let's see whether there is a case of class imbalance in this dataset or not. To do this, we will count the number of passengers who survived and those who did not.

```
print(df.Survived.value_counts())
```{{execute}}

We can clearly see the imbalance here. Out of the total 989 passengers, only 137 survived.

Now that we have reviewed the data, let's move on to the next steps.
