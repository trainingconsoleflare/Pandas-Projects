# Missing Values In Pandas

![](<.gitbook/assets/image (35) (1).png>)

## How To Handle Missing Values In Pandas ? <a href="#how-to-handle-missing-values-in-pandas" id="how-to-handle-missing-values-in-pandas"></a>

Missing Data values can occur when no information is provided and it also can be referred as NA. These values can interfere in processing the data.

Imagine a survey where few people did not share their income , It is known as missing values. We need to handle missing values with the help of pandas so there is no obstacle.

Let us start with our dataset named **miss.csv** file.

In \[1]:

```
import pandas as pd

df = pd.read_csv('miss.csv')
df
```

Out\[1]:

|    | id   | fname    | lname     | city      | state | age  |
| -- | ---- | -------- | --------- | --------- | ----- | ---- |
| 0  | 1.0  | nihal    | jaiswal   | noida     | up    | 26.0 |
| 1  | NaN  | rahul    | raj       | pune      | mh    | NaN  |
| 2  | 3.0  | NaN      | kumar     | NaN       | up    | NaN  |
| 3  | 4.0  | dipanshu | gupta     | mumbai    | mh    | 34.0 |
| 4  | 5.0  | NaN      | NaN       | gurugram  | hr    | 29.0 |
| 5  | 6.0  | alok     | agnihotri | amritsar  | pb    | 40.0 |
| 6  | 7.0  | priya    | verma     | NaN       | NaN   | NaN  |
| 7  | NaN  | NaN      | NaN       | NaN       | jk    | NaN  |
| 8  | 9.0  | ravi     | ranjan    | kochi     | kr    | 43.0 |
| 9  | NaN  | NaN      | NaN       | NaN       | NaN   | NaN  |
| 10 | 11.0 | atul     | verma     | rishikesh | uk    | 29.0 |

As you can see , there are lots of missing values NAN , Before dealing with these null values , Let's count them all in a go.

## Count Null and Non-Null Values: <a href="#count-null-and-non-null-values" id="count-null-and-non-null-values"></a>

In \[2]:

```
df.info()
```



```
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 11 entries, 0 to 10
Data columns (total 6 columns):
 #   Column  Non-Null Count  Dtype  
---  ------  --------------  -----  
 0   id      8 non-null      float64
 1   fname   7 non-null      object 
 2   lname   8 non-null      object 
 3   city    7 non-null      object 
 4   state   9 non-null      object 
 5   age     6 non-null      float64
dtypes: float64(2), object(4)
memory usage: 656.0+ bytes
```



### isnull <a href="#isnull" id="isnull"></a>

isnull() function returns all the null values as **True** and notnull values as **False**.

In \[3]:

```
df.isnull()
```

Out\[3]:

|    | id    | fname | lname | city  | state | age   |
| -- | ----- | ----- | ----- | ----- | ----- | ----- |
| 0  | False | False | False | False | False | False |
| 1  | True  | False | False | False | False | True  |
| 2  | False | True  | False | True  | False | True  |
| 3  | False | False | False | False | False | False |
| 4  | False | True  | True  | False | False | False |
| 5  | False | False | False | False | False | False |
| 6  | False | False | False | True  | True  | True  |
| 7  | True  | True  | True  | True  | False | True  |
| 8  | False | False | False | False | False | False |
| 9  | True  | True  | True  | True  | True  | True  |
| 10 | False | False | False | False | False | False |

You can also apply sum() function to count all the null values for a particular column.

In \[4]:

```
df.isnull().sum()
```

Out\[4]:

```
id       3
fname    4
lname    3
city     4
state    2
age      5
dtype: int64
```

### notnull <a href="#notnull" id="notnull"></a>

notnull() function returns all the null values as **False** and notnull values as **True**.

In \[5]:

```
df.notnull()
```

Out\[5]:

|    | id    | fname | lname | city  | state | age   |
| -- | ----- | ----- | ----- | ----- | ----- | ----- |
| 0  | True  | True  | True  | True  | True  | True  |
| 1  | False | True  | True  | True  | True  | False |
| 2  | True  | False | True  | False | True  | False |
| 3  | True  | True  | True  | True  | True  | True  |
| 4  | True  | False | False | True  | True  | True  |
| 5  | True  | True  | True  | True  | True  | True  |
| 6  | True  | True  | True  | False | False | False |
| 7  | False | False | False | False | True  | False |
| 8  | True  | True  | True  | True  | True  | True  |
| 9  | False | False | False | False | False | False |
| 10 | True  | True  | True  | True  | True  | True  |

You can also apply sum() function to count all the not null values for a particular column.

In \[6]:

```
df.notnull().sum()
```



```
id       8
fname    7
lname    8
city     7
state    9
age      6
dtype: int64
```

## Delete All rows with Any missing value: <a href="#delete-all-rows-with-any-missing-value" id="delete-all-rows-with-any-missing-value"></a>

**dropna:**

dropna() function deletes all the rows with any missing values.

**how:** how is a parameter that tells how do you want to delete data. There are two values that we pass in how.

**how='any':** This is default. It deletes all the rows with any null values in it.

**how='all':** It deletes rows where all the values are null values.

In \[7]:

```
df.dropna()
```

Out\[7]:

|    | id   | fname    | lname     | city      | state | age  |
| -- | ---- | -------- | --------- | --------- | ----- | ---- |
| 0  | 1.0  | nihal    | jaiswal   | noida     | up    | 26.0 |
| 3  | 4.0  | dipanshu | gupta     | mumbai    | mh    | 34.0 |
| 5  | 6.0  | alok     | agnihotri | amritsar  | pb    | 40.0 |
| 8  | 9.0  | ravi     | ranjan    | kochi     | kr    | 43.0 |
| 10 | 11.0 | atul     | verma     | rishikesh | uk    | 29.0 |

&#x20;                                                                                                       **OR**

```
df.dropna(how='any')
```

Out\[8]:

|    | id   | fname    | lname     | city      | state | age  |
| -- | ---- | -------- | --------- | --------- | ----- | ---- |
| 0  | 1.0  | nihal    | jaiswal   | noida     | up    | 26.0 |
| 3  | 4.0  | dipanshu | gupta     | mumbai    | mh    | 34.0 |
| 5  | 6.0  | alok     | agnihotri | amritsar  | pb    | 40.0 |
| 8  | 9.0  | ravi     | ranjan    | kochi     | kr    | 43.0 |
| 10 | 11.0 | atul     | verma     | rishikesh | uk    | 29.0 |

In \[9]:

```
df.dropna(how='all')
```

Out\[9]:

|    | id   | fname    | lname     | city      | state | age  |
| -- | ---- | -------- | --------- | --------- | ----- | ---- |
| 0  | 1.0  | nihal    | jaiswal   | noida     | up    | 26.0 |
| 1  | NaN  | rahul    | raj       | pune      | mh    | NaN  |
| 2  | 3.0  | NaN      | kumar     | NaN       | up    | NaN  |
| 3  | 4.0  | dipanshu | gupta     | mumbai    | mh    | 34.0 |
| 4  | 5.0  | NaN      | NaN       | gurugram  | hr    | 29.0 |
| 5  | 6.0  | alok     | agnihotri | amritsar  | pb    | 40.0 |
| 6  | 7.0  | priya    | verma     | NaN       | NaN   | NaN  |
| 7  | NaN  | NaN      | NaN       | NaN       | jk    | NaN  |
| 8  | 9.0  | ravi     | ranjan    | kochi     | kr    | 43.0 |
| 10 | 11.0 | atul     | verma     | rishikesh | uk    | 29.0 |

**thresh:**

thresh is known as threshold and it takes integer value,it will drop any row with less than 4 values in it.

In \[10]:

```
df.dropna(how='any',thresh=4)
```

Out\[10]:

|    | id   | fname    | lname     | city      | state | age  |
| -- | ---- | -------- | --------- | --------- | ----- | ---- |
| 0  | 1.0  | nihal    | jaiswal   | noida     | up    | 26.0 |
| 1  | NaN  | rahul    | raj       | pune      | mh    | NaN  |
| 3  | 4.0  | dipanshu | gupta     | mumbai    | mh    | 34.0 |
| 4  | 5.0  | NaN      | NaN       | gurugram  | hr    | 29.0 |
| 5  | 6.0  | alok     | agnihotri | amritsar  | pb    | 40.0 |
| 8  | 9.0  | ravi     | ranjan    | kochi     | kr    | 43.0 |
| 10 | 11.0 | atul     | verma     | rishikesh | uk    | 29.0 |

**subset**

subset stores columns in which you want to look for missing values. Like in this example if there is any city and state is NA, it will remove that row only.

In \[11]:

```
df.dropna(how='any',subset=['city','state'])
```

Out\[11]:

|    | id   | fname    | lname     | city      | state | age  |
| -- | ---- | -------- | --------- | --------- | ----- | ---- |
| 0  | 1.0  | nihal    | jaiswal   | noida     | up    | 26.0 |
| 1  | NaN  | rahul    | raj       | pune      | mh    | NaN  |
| 3  | 4.0  | dipanshu | gupta     | mumbai    | mh    | 34.0 |
| 4  | 5.0  | NaN      | NaN       | gurugram  | hr    | 29.0 |
| 5  | 6.0  | alok     | agnihotri | amritsar  | pb    | 40.0 |
| 8  | 9.0  | ravi     | ranjan    | kochi     | kr    | 43.0 |
| 10 | 11.0 | atul     | verma     | rishikesh | uk    | 29.0 |

In \[12]:

```
df.dropna(how='all',subset=['city','state'])
```

Out\[12]:

|    | id   | fname    | lname     | city      | state | age  |
| -- | ---- | -------- | --------- | --------- | ----- | ---- |
| 0  | 1.0  | nihal    | jaiswal   | noida     | up    | 26.0 |
| 1  | NaN  | rahul    | raj       | pune      | mh    | NaN  |
| 2  | 3.0  | NaN      | kumar     | NaN       | up    | NaN  |
| 3  | 4.0  | dipanshu | gupta     | mumbai    | mh    | 34.0 |
| 4  | 5.0  | NaN      | NaN       | gurugram  | hr    | 29.0 |
| 5  | 6.0  | alok     | agnihotri | amritsar  | pb    | 40.0 |
| 7  | NaN  | NaN      | NaN       | NaN       | jk    | NaN  |
| 8  | 9.0  | ravi     | ranjan    | kochi     | kr    | 43.0 |
| 10 | 11.0 | atul     | verma     | rishikesh | uk    | 29.0 |

Say if you want to look for atleast two values in city state and age.

In \[13]:

```
df.dropna(how='all',subset=['city','state','age'],thresh=2)
```

Out\[13]:

|    | id   | fname    | lname     | city      | state | age  |
| -- | ---- | -------- | --------- | --------- | ----- | ---- |
| 0  | 1.0  | nihal    | jaiswal   | noida     | up    | 26.0 |
| 1  | NaN  | rahul    | raj       | pune      | mh    | NaN  |
| 3  | 4.0  | dipanshu | gupta     | mumbai    | mh    | 34.0 |
| 4  | 5.0  | NaN      | NaN       | gurugram  | hr    | 29.0 |
| 5  | 6.0  | alok     | agnihotri | amritsar  | pb    | 40.0 |
| 8  | 9.0  | ravi     | ranjan    | kochi     | kr    | 43.0 |
| 10 | 11.0 | atul     | verma     | rishikesh | uk    | 29.0 |

**What if there is no NaN values but - and spaces or some other values.**

In \[14]:

```
ef = pd.read_csv('miss2.csv')
ef
```

Out\[14]:

|    | id   | fname    | lname     | city      | state | age |
| -- | ---- | -------- | --------- | --------- | ----- | --- |
| 0  | 1.0  | nihal    | jaiswal   | noida     | up    | -   |
| 1  | NaN  | rahul    | raj       | pune      | mh    | NaN |
| 2  | 3.0  | NaN      | kumar     | NaN       | up    | NaN |
| 3  | 4.0  | dipanshu | gupta     | mumbai    | mh    | -   |
| 4  | 5.0  | NaN      | NaN       | gurugram  | hr    | 29  |
| 5  | 6.0  | -        | agnihotri | amritsar  | pb    | 40  |
| 6  | 7.0  | priya    | verma     | NaN       |       | NaN |
| 7  | NaN  | NaN      | NaN       | NaN       | jk    | NaN |
| 8  | 9.0  | ravi     | ranjan    |           | kr    | 43  |
| 9  | NaN  | NaN      | NaN       | NaN       | NaN   | NaN |
| 10 | 11.0 | atul     | verma     | rishikesh | uk    | 29  |

We can use numpy functions to replace all useless values from NaN.

In \[15]:

```
import pandas as pd
import numpy as np

ef = pd.read_csv('miss2.csv')
ef = ef.replace('-',np.NAN).replace(' ',np.NAN)
ef
```

Out\[15]:

|    | id   | fname    | lname     | city      | state | age |
| -- | ---- | -------- | --------- | --------- | ----- | --- |
| 0  | 1.0  | nihal    | jaiswal   | noida     | up    | NaN |
| 1  | NaN  | rahul    | raj       | pune      | mh    | NaN |
| 2  | 3.0  | NaN      | kumar     | NaN       | up    | NaN |
| 3  | 4.0  | dipanshu | gupta     | mumbai    | mh    | NaN |
| 4  | 5.0  | NaN      | NaN       | gurugram  | hr    | 29  |
| 5  | 6.0  | NaN      | agnihotri | amritsar  | pb    | 40  |
| 6  | 7.0  | priya    | verma     | NaN       | NaN   | NaN |
| 7  | NaN  | NaN      | NaN       | NaN       | jk    | NaN |
| 8  | 9.0  | ravi     | ranjan    | NaN       | kr    | 43  |
| 9  | NaN  | NaN      | NaN       | NaN       | NaN   | NaN |
| 10 | 11.0 | atul     | verma     | rishikesh | uk    | 29  |

In \[16]:

```
ef.dropna()
```

Out\[16]:

|    | id   | fname | lname | city      | state | age |
| -- | ---- | ----- | ----- | --------- | ----- | --- |
| 10 | 11.0 | atul  | verma | rishikesh | uk    | 29  |

**fillna():**

fillna() method is used to replace all NaN values with something else. For example:

In \[17]:

```
df
```

Out\[17]:

|    | id   | fname    | lname     | city      | state | age  |
| -- | ---- | -------- | --------- | --------- | ----- | ---- |
| 0  | 1.0  | nihal    | jaiswal   | noida     | up    | 26.0 |
| 1  | NaN  | rahul    | raj       | pune      | mh    | NaN  |
| 2  | 3.0  | NaN      | kumar     | NaN       | up    | NaN  |
| 3  | 4.0  | dipanshu | gupta     | mumbai    | mh    | 34.0 |
| 4  | 5.0  | NaN      | NaN       | gurugram  | hr    | 29.0 |
| 5  | 6.0  | alok     | agnihotri | amritsar  | pb    | 40.0 |
| 6  | 7.0  | priya    | verma     | NaN       | NaN   | NaN  |
| 7  | NaN  | NaN      | NaN       | NaN       | jk    | NaN  |
| 8  | 9.0  | ravi     | ranjan    | kochi     | kr    | 43.0 |
| 9  | NaN  | NaN      | NaN       | NaN       | NaN   | NaN  |
| 10 | 11.0 | atul     | verma     | rishikesh | uk    | 29.0 |

If i want to fill all NaN values with Zero:

In \[20]:

```
df.fillna(0)
```

Out\[20]:

|    | id   | fname    | lname     | city      | state | age  |
| -- | ---- | -------- | --------- | --------- | ----- | ---- |
| 0  | 1.0  | nihal    | jaiswal   | noida     | up    | 26.0 |
| 1  | 0.0  | rahul    | raj       | pune      | mh    | 0.0  |
| 2  | 3.0  | 0        | kumar     | 0         | up    | 0.0  |
| 3  | 4.0  | dipanshu | gupta     | mumbai    | mh    | 34.0 |
| 4  | 5.0  | 0        | 0         | gurugram  | hr    | 29.0 |
| 5  | 6.0  | alok     | agnihotri | amritsar  | pb    | 40.0 |
| 6  | 7.0  | priya    | verma     | 0         | 0     | 0.0  |
| 7  | 0.0  | 0        | 0         | 0         | jk    | 0.0  |
| 8  | 9.0  | ravi     | ranjan    | kochi     | kr    | 43.0 |
| 9  | 0.0  | 0        | 0         | 0         | 0     | 0.0  |
| 10 | 11.0 | atul     | verma     | rishikesh | uk    | 29.0 |

But 0 as a value is not right for columns like city or state, so you can fill values according to column data type by using dictionary.



```
df.fillna(
    {
        'id':0,
        'age':0,
        'fname':"no name",
        'lname':"no name",
        'city':"no city",
        'state':"no state"
    }
)
```

Out\[24]:

|    | id   | fname    | lname     | city      | state    | age  |
| -- | ---- | -------- | --------- | --------- | -------- | ---- |
| 0  | 1.0  | nihal    | jaiswal   | noida     | up       | 26.0 |
| 1  | 0.0  | rahul    | raj       | pune      | mh       | 0.0  |
| 2  | 3.0  | no name  | kumar     | no city   | up       | 0.0  |
| 3  | 4.0  | dipanshu | gupta     | mumbai    | mh       | 34.0 |
| 4  | 5.0  | no name  | no name   | gurugram  | hr       | 29.0 |
| 5  | 6.0  | alok     | agnihotri | amritsar  | pb       | 40.0 |
| 6  | 7.0  | priya    | verma     | no city   | no state | 0.0  |
| 7  | 0.0  | no name  | no name   | no city   | jk       | 0.0  |
| 8  | 9.0  | ravi     | ranjan    | kochi     | kr       | 43.0 |
| 9  | 0.0  | no name  | no name   | no city   | no state | 0.0  |
| 10 | 11.0 | atul     | verma     | rishikesh | uk       | 29.0 |

**ffill and bfill**

you can use ffill and bfill property to carry next or previous value to NaN Values.

In \[25]:

```
df.fillna(method='ffill')
```

Out\[25]:

|    | id   | fname    | lname     | city      | state | age  |
| -- | ---- | -------- | --------- | --------- | ----- | ---- |
| 0  | 1.0  | nihal    | jaiswal   | noida     | up    | 26.0 |
| 1  | 1.0  | rahul    | raj       | pune      | mh    | 26.0 |
| 2  | 3.0  | rahul    | kumar     | pune      | up    | 26.0 |
| 3  | 4.0  | dipanshu | gupta     | mumbai    | mh    | 34.0 |
| 4  | 5.0  | dipanshu | gupta     | gurugram  | hr    | 29.0 |
| 5  | 6.0  | alok     | agnihotri | amritsar  | pb    | 40.0 |
| 6  | 7.0  | priya    | verma     | amritsar  | pb    | 40.0 |
| 7  | 7.0  | priya    | verma     | amritsar  | jk    | 40.0 |
| 8  | 9.0  | ravi     | ranjan    | kochi     | kr    | 43.0 |
| 9  | 9.0  | ravi     | ranjan    | kochi     | kr    | 43.0 |
| 10 | 11.0 | atul     | verma     | rishikesh | uk    | 29.0 |

![](<.gitbook/assets/image (8).png>)



```
df.fillna(method='bfill')
```

Out\[26]:

|    | id   | fname    | lname     | city      | state | age  |
| -- | ---- | -------- | --------- | --------- | ----- | ---- |
| 0  | 1.0  | nihal    | jaiswal   | noida     | up    | 26.0 |
| 1  | 3.0  | rahul    | raj       | pune      | mh    | 34.0 |
| 2  | 3.0  | dipanshu | kumar     | mumbai    | up    | 34.0 |
| 3  | 4.0  | dipanshu | gupta     | mumbai    | mh    | 34.0 |
| 4  | 5.0  | alok     | agnihotri | gurugram  | hr    | 29.0 |
| 5  | 6.0  | alok     | agnihotri | amritsar  | pb    | 40.0 |
| 6  | 7.0  | priya    | verma     | kochi     | jk    | 43.0 |
| 7  | 9.0  | ravi     | ranjan    | kochi     | jk    | 43.0 |
| 8  | 9.0  | ravi     | ranjan    | kochi     | kr    | 43.0 |
| 9  | 11.0 | atul     | verma     | rishikesh | uk    | 29.0 |
| 10 | 11.0 | atul     | verma     | rishikesh | uk    | 29.0 |

![](<.gitbook/assets/image (68).png>)

You can also fill values horizontally with the help of axis.

In \[31]:

```
df.fillna(method='ffill',axis='columns')
```

Out\[31]:

|    | id   | fname    | lname     | city      | state | age   |
| -- | ---- | -------- | --------- | --------- | ----- | ----- |
| 0  | 1.0  | nihal    | jaiswal   | noida     | up    | 26.0  |
| 1  | NaN  | rahul    | raj       | pune      | mh    | mh    |
| 2  | 3.0  | 3.0      | kumar     | kumar     | up    | up    |
| 3  | 4.0  | dipanshu | gupta     | mumbai    | mh    | 34.0  |
| 4  | 5.0  | 5.0      | 5.0       | gurugram  | hr    | 29.0  |
| 5  | 6.0  | alok     | agnihotri | amritsar  | pb    | 40.0  |
| 6  | 7.0  | priya    | verma     | verma     | verma | verma |
| 7  | NaN  | NaN      | NaN       | NaN       | jk    | jk    |
| 8  | 9.0  | ravi     | ranjan    | kochi     | kr    | 43.0  |
| 9  | NaN  | NaN      | NaN       | NaN       | NaN   | NaN   |
| 10 | 11.0 | atul     | verma     | rishikesh | uk    | 29.0  |

You can also limit filling values by using **limit** property.

In \[32]:

```
df.fillna(method='ffill',limit=1)
```

Out\[32]:

|    | id   | fname    | lname     | city      | state | age  |
| -- | ---- | -------- | --------- | --------- | ----- | ---- |
| 0  | 1.0  | nihal    | jaiswal   | noida     | up    | 26.0 |
| 1  | 1.0  | rahul    | raj       | pune      | mh    | 26.0 |
| 2  | 3.0  | rahul    | kumar     | pune      | up    | NaN  |
| 3  | 4.0  | dipanshu | gupta     | mumbai    | mh    | 34.0 |
| 4  | 5.0  | dipanshu | gupta     | gurugram  | hr    | 29.0 |
| 5  | 6.0  | alok     | agnihotri | amritsar  | pb    | 40.0 |
| 6  | 7.0  | priya    | verma     | amritsar  | pb    | 40.0 |
| 7  | 7.0  | priya    | verma     | NaN       | jk    | NaN  |
| 8  | 9.0  | ravi     | ranjan    | kochi     | kr    | 43.0 |
| 9  | 9.0  | ravi     | ranjan    | kochi     | kr    | 43.0 |
| 10 | 11.0 | atul     | verma     | rishikesh | uk    | 29.0 |

## Interpolation - Linear Interpolation <a href="#interpolation-linear-interpolation" id="interpolation-linear-interpolation"></a>

Interpolation is a technique in Python used to estimate unknown data points between two known data points. Interpolation is mostly used to impute missing values in the dataframe or series while preprocessing data.

In \[35]:

```
df.interpolate()
```

Out\[35]:

|    | id   | fname    | lname     | city      | state | age       |
| -- | ---- | -------- | --------- | --------- | ----- | --------- |
| 0  | 1.0  | nihal    | jaiswal   | noida     | up    | 26.000000 |
| 1  | 2.0  | rahul    | raj       | pune      | mh    | 28.666667 |
| 2  | 3.0  | NaN      | kumar     | NaN       | up    | 31.333333 |
| 3  | 4.0  | dipanshu | gupta     | mumbai    | mh    | 34.000000 |
| 4  | 5.0  | NaN      | NaN       | gurugram  | hr    | 29.000000 |
| 5  | 6.0  | alok     | agnihotri | amritsar  | pb    | 40.000000 |
| 6  | 7.0  | priya    | verma     | NaN       | NaN   | 41.000000 |
| 7  | 8.0  | NaN      | NaN       | NaN       | jk    | 42.000000 |
| 8  | 9.0  | ravi     | ranjan    | kochi     | kr    | 43.000000 |
| 9  | 10.0 | NaN      | NaN       | NaN       | NaN   | 36.000000 |
| 10 | 11.0 | atul     | verma     | rishikesh | uk    | 29.000000 |

![](<.gitbook/assets/image (83).png>)
