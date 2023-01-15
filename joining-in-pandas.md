# Joining In Pandas

![](<.gitbook/assets/image (5).png>)

## Introduction To joins in pandas: <a href="#introduction-to-joins-in-pandas" id="introduction-to-joins-in-pandas"></a>

**Working on a single table is easy , but what might be challenging is to work on multiple tables. You have to think of a lot of**

**criterias , how to join these tables . Pandas offers some joining methods that makes this task easy for you. There are four**

**different types of joins in pandas. Let's go through them one by one.**

## Types of joins in Pandas : <a href="#types-of-joins-in-pandas" id="types-of-joins-in-pandas"></a>

###

**We’ll take a simple problem from a related marketing brand here. We are given two tables – one which contains data about products and the other that has customer- information.**

**We will use these tables to understand how the different types of joins work using Pandas.**

## Inner Join In Pandas <a href="#inner-join-in-pandas" id="inner-join-in-pandas"></a>

![](<.gitbook/assets/image (61).png>)

{% hint style="info" %}
**Inner join is the most common type of join you’ll be working with. It returns a dataframe with only those rows that have common characteristics.**
{% endhint %}

**This is similar to the intersection of two sets.**

**So let's start by importing our pandas library.**

In \[1]:

```
import pandas as pd
```

**To understand join better, we have two dataframes :**



In \[2]:

```
product=pd.read_csv('Products.csv')
product
```

Out\[2]:

|   | id | Product\_ID | Product\_name | Category    | Price   | Seller\_City |
| - | -- | ----------- | ------------- | ----------- | ------- | ------------ |
| 0 | 0  | 101         | Watch         | Fashion     | 299.0   | Delhi        |
| 1 | 1  | 102         | Bag           | Fashion     | 1350.5  | Mumbai       |
| 2 | 2  | 103         | Shoes         | Fashion     | 2999.0  | Chennai      |
| 3 | 3  | 104         | Smartphone    | Electronics | 14999.0 | Kolkata      |
| 4 | 4  | 105         | Books         | Study       | 145.0   | Delhi        |
| 5 | 5  | 106         | Oil           | Grocery     | 110.0   | Chennai      |
| 6 | 6  | 107         | Laptop        | Electronics | 79999.0 | Bengalore    |



```
customer=pd.read_csv('Customers.csv')
customer
```

Out\[3]:

|   | id | name    | age | Product\_ID | Purchased\_Product | City      |
| - | -- | ------- | --- | ----------- | ------------------ | --------- |
| 0 | 1  | Olivia  | 20  | 101         | Watch              | Mumbai    |
| 1 | 2  | Aditya  | 25  | 0           | NaN                | Delhi     |
| 2 | 3  | Cory    | 15  | 106         | Oil                | Bangalore |
| 3 | 4  | Isabell | 10  | 0           | NaN                | Chennai   |
| 4 | 5  | Dominic | 30  | 103         | Shoes              | Chennai   |
| 5 | 6  | Tyler   | 65  | 104         | Smartphone         | Delhi     |
| 6 | 7  | Samuel  | 35  | 0           | NaN                | Kolkata   |
| 7 | 8  | Daniel  | 18  | 0           | NaN                | Delhi     |
| 8 | 9  | Jeremy  | 23  | 107         | Laptop             | Mumbai    |

**Let's say i want to find all the products that are sold with customers details. To find this , we will perform inner join.**

## Merge Function : <a href="#merge-function" id="merge-function"></a>

**Merge function helps to join these two tables and by default it performs an inner join.**

In \[4]:

```
product.merge(customer,on='Product_ID')
```

Out\[4]:

|   | id\_x | Product\_ID | Product\_name | Category    | Price   | Seller\_City | id\_y | name    | age | Purchased\_Product | City      |
| - | ----- | ----------- | ------------- | ----------- | ------- | ------------ | ----- | ------- | --- | ------------------ | --------- |
| 0 | 0     | 101         | Watch         | Fashion     | 299.0   | Delhi        | 1     | Olivia  | 20  | Watch              | Mumbai    |
| 1 | 2     | 103         | Shoes         | Fashion     | 2999.0  | Chennai      | 5     | Dominic | 30  | Shoes              | Chennai   |
| 2 | 3     | 104         | Smartphone    | Electronics | 14999.0 | Kolkata      | 6     | Tyler   | 65  | Smartphone         | Delhi     |
| 3 | 5     | 106         | Oil           | Grocery     | 110.0   | Chennai      | 3     | Cory    | 15  | Oil                | Bangalore |
| 4 | 6     | 107         | Laptop        | Electronics | 79999.0 | Bengalore    | 9     | Jeremy  | 23  | Laptop             | Mumbai    |

**What if the column names are different in the two dataframes? Then, we have to explicitly mention both the column names.**

**left\_on and right\_on are two arguments through which we can achieve this. ‘left\_on’ is the name of the key in the left dataframe and ‘right\_on’ in the right dataframe.**

In \[5]:

```
product.merge(customer,left_on='Product_name',right_on='Purchased_Product')
```

Out\[5]:

|   | id\_x | Product\_ID\_x | Product\_name | Category    | Price   | Seller\_City | id\_y | name    | age | Product\_ID\_y | Purchased\_Product | City      |
| - | ----- | -------------- | ------------- | ----------- | ------- | ------------ | ----- | ------- | --- | -------------- | ------------------ | --------- |
| 0 | 0     | 101            | Watch         | Fashion     | 299.0   | Delhi        | 1     | Olivia  | 20  | 101            | Watch              | Mumbai    |
| 1 | 2     | 103            | Shoes         | Fashion     | 2999.0  | Chennai      | 5     | Dominic | 30  | 103            | Shoes              | Chennai   |
| 2 | 3     | 104            | Smartphone    | Electronics | 14999.0 | Kolkata      | 6     | Tyler   | 65  | 104            | Smartphone         | Delhi     |
| 3 | 5     | 106            | Oil           | Grocery     | 110.0   | Chennai      | 3     | Cory    | 15  | 106            | Oil                | Bangalore |
| 4 | 6     | 107            | Laptop        | Electronics | 79999.0 | Bengalore    | 9     | Jeremy  | 23  | 107            | Laptop             | Mumbai    |

In \[6]:

```
product.merge(customer,how='inner',left_on=['Product_ID','Seller_City'],right_on=['Product_ID','City'])
```

Out\[6]:

|   | id\_x | Product\_ID | Product\_name | Category | Price  | Seller\_City | id\_y | name    | age | Purchased\_Product | City    |
| - | ----- | ----------- | ------------- | -------- | ------ | ------------ | ----- | ------- | --- | ------------------ | ------- |
| 0 | 2     | 103         | Shoes         | Fashion  | 2999.0 | Chennai      | 5     | Dominic | 30  | Shoes              | Chennai |

## Outer Join :  <a href="#outer-join" id="outer-join"></a>

![](<.gitbook/assets/image (100).png>)

**Here’s another interesting task for you. We have to combine both dataframes so that we can find all the products that are not sold and all the customers who didn’t purchase anything from us. We can use Full Join for this purpose. Full Join, also known as Full Outer Join, returns all those records which either have a match in the left or right dataframe. When rows in both the dataframes do not match, the resulting dataframe will have NaN for every column of the dataframe that lacks a matching row. We can perform Full join by just passing the how argument as ‘outer’ to the merge() function:**

In \[7]:

```
product.merge(customer,on='Product_ID',how='outer')
```

Out\[7]:

|    | id\_x | Product\_ID | Product\_name | Category    | Price   | Seller\_City | id\_y | name    | age  | Purchased\_Product | City      |
| -- | ----- | ----------- | ------------- | ----------- | ------- | ------------ | ----- | ------- | ---- | ------------------ | --------- |
| 0  | 0.0   | 101         | Watch         | Fashion     | 299.0   | Delhi        | 1.0   | Olivia  | 20.0 | Watch              | Mumbai    |
| 1  | 1.0   | 102         | Bag           | Fashion     | 1350.5  | Mumbai       | NaN   | NaN     | NaN  | NaN                | NaN       |
| 2  | 2.0   | 103         | Shoes         | Fashion     | 2999.0  | Chennai      | 5.0   | Dominic | 30.0 | Shoes              | Chennai   |
| 3  | 3.0   | 104         | Smartphone    | Electronics | 14999.0 | Kolkata      | 6.0   | Tyler   | 65.0 | Smartphone         | Delhi     |
| 4  | 4.0   | 105         | Books         | Study       | 145.0   | Delhi        | NaN   | NaN     | NaN  | NaN                | NaN       |
| 5  | 5.0   | 106         | Oil           | Grocery     | 110.0   | Chennai      | 3.0   | Cory    | 15.0 | Oil                | Bangalore |
| 6  | 6.0   | 107         | Laptop        | Electronics | 79999.0 | Bengalore    | 9.0   | Jeremy  | 23.0 | Laptop             | Mumbai    |
| 7  | NaN   | 0           | NaN           | NaN         | NaN     | NaN          | 2.0   | Aditya  | 25.0 | NaN                | Delhi     |
| 8  | NaN   | 0           | NaN           | NaN         | NaN     | NaN          | 4.0   | Isabell | 10.0 | NaN                | Chennai   |
| 9  | NaN   | 0           | NaN           | NaN         | NaN     | NaN          | 7.0   | Samuel  | 35.0 | NaN                | Kolkata   |
| 10 | NaN   | 0           | NaN           | NaN         | NaN     | NaN          | 8.0   | Daniel  | 18.0 | NaN                | Delhi     |

## Left join <a href="#left-join" id="left-join"></a>

![](<.gitbook/assets/image (14).png>)

**Now, let’s say the leadership team wants information about only those customers who bought something from us. You guessed it – we can use the concept of Left Join here.**

**Left join, also known as Left Outer Join, returns a dataframe containing all the rows of the left dataframe.**

**All the non-matching rows of the left dataframe contain NaN for the columns in the right dataframe. It is simply an inner join plus all the non-matching rows of the left dataframe filled with NaN for columns of the right dataframe.**

**Performing a left join is actually quite similar to a full join. Just change the how argument to ‘left’:**

In \[8]:

```
product.merge(customer,on='Product_ID',how='left')
```

Out\[8]:

|   | id\_x | Product\_ID | Product\_name | Category    | Price   | Seller\_City | id\_y | name    | age  | Purchased\_Product | City      |
| - | ----- | ----------- | ------------- | ----------- | ------- | ------------ | ----- | ------- | ---- | ------------------ | --------- |
| 0 | 0     | 101         | Watch         | Fashion     | 299.0   | Delhi        | 1.0   | Olivia  | 20.0 | Watch              | Mumbai    |
| 1 | 1     | 102         | Bag           | Fashion     | 1350.5  | Mumbai       | NaN   | NaN     | NaN  | NaN                | NaN       |
| 2 | 2     | 103         | Shoes         | Fashion     | 2999.0  | Chennai      | 5.0   | Dominic | 30.0 | Shoes              | Chennai   |
| 3 | 3     | 104         | Smartphone    | Electronics | 14999.0 | Kolkata      | 6.0   | Tyler   | 65.0 | Smartphone         | Delhi     |
| 4 | 4     | 105         | Books         | Study       | 145.0   | Delhi        | NaN   | NaN     | NaN  | NaN                | NaN       |
| 5 | 5     | 106         | Oil           | Grocery     | 110.0   | Chennai      | 3.0   | Cory    | 15.0 | Oil                | Bangalore |
| 6 | 6     | 107         | Laptop        | Electronics | 79999.0 | Bengalore    | 9.0   | Jeremy  | 23.0 | Laptop             | Mumbai    |

## Right Join <a href="#right-join" id="right-join"></a>

![](<.gitbook/assets/image (75).png>)

**Similarly, if we want to create a table of customers including the information about the products they bought, we can use the right join.**

**Right join, also known as Right Outer Join, is similar to the Left Outer Join. The only difference is that all the rows of the right dataframe are taken as it is and only those of the left dataframe that are common in both.**

**Similar to other joins, we can perform a right join by changing the how argument to ‘right’:**

In \[9]:

```
product.merge(customer,on='Product_ID',how='right')
```

Out\[9]:

|   | id\_x | Product\_ID | Product\_name | Category    | Price   | Seller\_City | id\_y | name    | age | Purchased\_Product | City      |
| - | ----- | ----------- | ------------- | ----------- | ------- | ------------ | ----- | ------- | --- | ------------------ | --------- |
| 0 | 0.0   | 101         | Watch         | Fashion     | 299.0   | Delhi        | 1     | Olivia  | 20  | Watch              | Mumbai    |
| 1 | NaN   | 0           | NaN           | NaN         | NaN     | NaN          | 2     | Aditya  | 25  | NaN                | Delhi     |
| 2 | 5.0   | 106         | Oil           | Grocery     | 110.0   | Chennai      | 3     | Cory    | 15  | Oil                | Bangalore |
| 3 | NaN   | 0           | NaN           | NaN         | NaN     | NaN          | 4     | Isabell | 10  | NaN                | Chennai   |
| 4 | 2.0   | 103         | Shoes         | Fashion     | 2999.0  | Chennai      | 5     | Dominic | 30  | Shoes              | Chennai   |
| 5 | 3.0   | 104         | Smartphone    | Electronics | 14999.0 | Kolkata      | 6     | Tyler   | 65  | Smartphone         | Delhi     |
| 6 | NaN   | 0           | NaN           | NaN         | NaN     | NaN          | 7     | Samuel  | 35  | NaN                | Kolkata   |
| 7 | NaN   | 0           | NaN           | NaN         | NaN     | NaN          | 8     | Daniel  | 18  | NaN                | Delhi     |
| 8 | 6.0   | 107         | Laptop        | Electronics | 79999.0 | Bengalore    | 9     | Jeremy  | 23  | Laptop             | Mumbai    |

## Concatenate Dataframe : <a href="#concatenate-dataframe" id="concatenate-dataframe"></a>

In \[10]:

```
df1 = pd.read_csv('firsthalf.csv')
df1
```

Out\[10]:

|   | id | name   | age |
| - | -- | ------ | --- |
| 0 | 1  | abhi   | 23  |
| 1 | 2  | rajesh | 35  |
| 2 | 3  | adarsh | 56  |
| 3 | 4  | suresh | 40  |
| 4 | 5  | dev    | 27  |

In \[11]:

```
df2 = pd.read_csv('secondhalf.csv')
df2
```

Out\[11]:

|   | id | name   | age |
| - | -- | ------ | --- |
| 0 | 6  | raj    | 33  |
| 1 | 7  | himesh | 21  |
| 2 | 8  | pranav | 24  |
| 3 | 9  | pawan  | 30  |
| 4 | 10 | gaurav | 32  |

In \[13]:

```
pd.concat((df1,df2))
```

Out\[13]:

|   | id | name   | age |
| - | -- | ------ | --- |
| 0 | 1  | abhi   | 23  |
| 1 | 2  | rajesh | 35  |
| 2 | 3  | adarsh | 56  |
| 3 | 4  | suresh | 40  |
| 4 | 5  | dev    | 27  |
| 0 | 6  | raj    | 33  |
| 1 | 7  | himesh | 21  |
| 2 | 8  | pranav | 24  |
| 3 | 9  | pawan  | 30  |
| 4 | 10 | gaurav | 32  |

![](<.gitbook/assets/image (4) (1).png>)
