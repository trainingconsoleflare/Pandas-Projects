# Aggregating Data

![](<.gitbook/assets/image (23).png>)

## Mean <a href="#mean" id="mean"></a>

**Mean** is the **average** of the given numbers and is calculated by dividing the sum of given numbers by the total number of numbers.

## Median <a href="#median" id="median"></a>

The Median is the Middle value in the list of numbers.

## Data <a href="#data" id="data"></a>

In \[30]:

```
import pandas as pd
import numpy as np
walmart = pd.read_csv('walmart.csv')
walmart['Date']  = pd.to_datetime(walmart['Date'])
walmart.head()
```

Out\[30]:

|   | Store | Type | Department | Weekly\_Sales | Is\_Holiday | Temperature | Fuel\_Price | Unemployment | Date       |
| - | ----- | ---- | ---------- | ------------- | ----------- | ----------- | ----------- | ------------ | ---------- |
| 0 | 1     | A    | 1          | 57258.43      | False       | 62.27       | 2.719       | 7.808        | 2010-04-02 |
| 1 | 1     | A    | 1          | 16333.14      | False       | 80.91       | 2.669       | 7.787        | 2010-07-02 |
| 2 | 1     | A    | 1          | 19403.54      | False       | 46.63       | 2.561       | 8.106        | 2010-02-26 |
| 3 | 1     | A    | 1          | 22517.56      | False       | 49.27       | 2.708       | 7.838        | 2010-12-03 |
| 4 | 1     | A    | 1          | 17596.96      | False       | 66.32       | 2.808       | 7.808        | 2010-04-16 |

So, this is our Data about Walmart store. In this module we are going to use Walmart DataSet.

Let's find out the the **mean** and **median** for **Weekly\_Sales** column.

In \[31]:

```
walmart['Weekly_Sales'].mean()
```

Out\[31]:

```
15983.4296920532
```

In \[32]:

```
walmart['Weekly_Sales'].median()
```

Out\[32]:

```
7616.55
```

## Summarizing dates <a href="#summarizing-dates" id="summarizing-dates"></a>

**Maximum and Minimum allow us to see what time range your data covers.**

In \[33]:

```
walmart['Date'].max()
```

Out\[33]:

```
Timestamp('2012-10-26 00:00:00')
```

In \[34]:

```
walmart['Date'].min()
```

Out\[34]:

```
Timestamp('2010-02-05 00:00:00')
```

By using .max() and .min() we get to know that our DataSet have data from January of 2010 to December of 2012.

## Efficient Summaries <a href="#efficient-summaries" id="efficient-summaries"></a>

**Agg Method:**

The .agg() method allows you to apply your own custom functions to a DataFrame, as well as apply functions to more than one column of a DataFrame at once, making your aggregations super efficient.

Have you noticed that our temperature column is in Fahrenheit and I want to convert it into Celsius. Now, we will make my custom function that will convert temperature from Fahrenheit to Celsius and we will apply it through .agg() method to a DataFrame column.

In \[35]:

```
def f_to_c(column):
    return (column-32)*5/9

walmart['Temperature'].agg(f_to_c)
```

Out\[35]:

```
0         16.816667
1         27.172222
2          8.127778
3          9.594444
4         19.066667
            ...    
282446    18.511111
282447    18.266667
282448     2.777778
282449    25.916667
282450    16.244444
Name: Temperature, Length: 282451, dtype: float64
```

Here, we are applying a custom function with the help of **.agg()** method, you can pass the list of functions to apply more than one function or you can pass the list of columns if you want to apply the function on more than one column.

## Cumulative Statistics <a href="#cumulative-statistics" id="cumulative-statistics"></a>

Cumulative statistics can also be helpful in tracking summary statistics over time. We'll calculate the cumulative sum and cumulative max of a department's weekly sales, which will allow us to identify what the total sales were so far as well as what the highest weekly sales were so far.

**Cumulative sum of weekly\_sales**

In \[36]:

```
# cum_walmart['Cum_Weekly_Sales'] = cum_walmart['Weekly_Sales'].cumsum()
```

## Dropping duplicates <a href="#dropping-duplicates" id="dropping-duplicates"></a>

Removing duplicates is very essential to get accurate counts, because we don't want to count the same thing multiple times. In this exercise, we'll create some new DataFrames using unique values from walmart.

In \[37]:

```
walmart_store_types = walmart.drop_duplicates(subset=['Store','Type'])
walmart_store_types.head()
```

Out\[37]:

|       | Store | Type | Department | Weekly\_Sales | Is\_Holiday | Temperature | Fuel\_Price | Unemployment | Date       |
| ----- | ----- | ---- | ---------- | ------------- | ----------- | ----------- | ----------- | ------------ | ---------- |
| 0     | 1     | A    | 1          | 57258.43      | False       | 62.27       | 2.719       | 7.808        | 2010-04-02 |
| 6946  | 2     | A    | 1          | 27023.35      | False       | 69.24       | 2.603       | 8.163        | 2010-10-01 |
| 13804 | 3     | B    | 1          | 4238.56       | False       | 82.20       | 2.669       | 7.346        | 2010-07-02 |
| 19897 | 4     | A    | 1          | 36486.28      | False       | 63.96       | 2.619       | 7.127        | 2010-10-01 |
| 26713 | 5     | B    | 1          | 8588.14       | False       | 71.10       | 2.603       | 6.768        | 2010-10-01 |

## Counting categorical variables <a href="#counting-categorical-variables" id="counting-categorical-variables"></a>

Counting is a great way to get an overview of your data and to spot unknown information that you might not notice. We'll count the number of each type of store and the number of each department number using the DataFrames we created in Dropping Duplicates.

**Counting the number of stores of each Type**

In \[38]:

```
walmart_store_counts = walmart_store_types['Type'].value_counts()
walmart_store_counts
```

Out\[38]:

```
A    22
B    17
C     6
Name: Type, dtype: int64
```

**Proportion of stores of each Type**

**Normalize: normalize** argument is used to turn the counts into proportion of the total.

In \[39]:

```
walmart_store_props = walmart_store_types['Type'].value_counts(normalize=True)
walmart_store_props
```

Out\[39]:

```
A    0.488889
B    0.377778
C    0.133333
Name: Type, dtype: float64
```

#### Counting the number of each department number and sorting values <a href="#counting-the-number-of-each-department-number-and-sorting-values" id="counting-the-number-of-each-department-number-and-sorting-values"></a>

In \[40]:

```
walmart_dept_counts_sorted = walmart['Department'].value_counts(sort=True)
walmart_dept_counts_sorted
```

Out\[40]:

```
90    4394
2     4379
79    4360
91    4355
14    4352
      ... 
78     147
65      96
77      93
39       9
43       8
Name: Department, Length: 81, dtype: int64
```

#### Proportion of departments of each number and sorting values <a href="#proportion-of-departments-of-each-number-and-sorting-values" id="proportion-of-departments-of-each-number-and-sorting-values"></a>

In \[41]:

```
walmart_dept_props_sorted = walmart['Department'].value_counts(sort=True, normalize=True)
walmart_dept_props_sorted
```

Out\[41]:

```
90    0.015557
2     0.015504
79    0.015436
91    0.015419
14    0.015408
        ...   
78    0.000520
65    0.000340
77    0.000329
39    0.000032
43    0.000028
Name: Department, Length: 81, dtype: float64
```

## .groupby() <a href="#.groupby" id=".groupby"></a>

Pandas groupby is used for grouping the data according to the categories and apply a function to the categories. It also helps to aggregate data efficiently.

**Group by Type to calculate total Weekly\_Sales**

In \[42]:

```
walmart_sales_by_type = walmart.groupby("Type")["Weekly_Sales"].sum()
walmart_sales_by_type
```

Out\[42]:

```
Type
A    2.902625e+09
B    1.341802e+09
C    2.701086e+08
Name: Weekly_Sales, dtype: float64
```

Here, we group by the Type and perform sum on the column Weekly\_Sales.

**Group by Type and Is\_Holiday to calculate total Weekly\_Sales**

In \[43]:

```
walmart_sales_by_type_is_holiday = walmart.groupby(["Type",'Is_Holiday'])["Weekly_Sales"].sum()
walmart_sales_by_type_is_holiday
```

Out\[43]:

```
Type  Is_Holiday
A     False         2.689482e+09
      True          2.131421e+08
B     False         1.237606e+09
      True          1.041968e+08
C     False         2.507886e+08
      True          1.931996e+07
Name: Weekly_Sales, dtype: float64
```

In this case we are grouping by two columns and summarizing one column if you want to perfrom any other summary statistics on more than one column then you have to pass the list of those column.

### Multiple grouped summaries <a href="#multiple-grouped-summaries" id="multiple-grouped-summaries"></a>

Earlier we saw that the .agg() method is useful to compute multiple statistics on multiple variables. It also works with .groupby or grouped data.

**For each store Type, aggregating Weekly\_Sales to gett min, max, mean, and median**

In \[44]:

```
walmart_sales_stats = walmart.groupby('Type')['Weekly_Sales'].agg([np.min,np.max,np.mean,np.median])
walmart_sales_stats
```

Out\[44]:

|      | amin     | amax      | mean         | median   |
| ---- | -------- | --------- | ------------ | -------- |
| Type |          |           |              |          |
| A    | -4988.94 | 381072.11 | 20079.169258 | 10096.75 |
| B    | -1750.00 | 693099.36 | 12263.647825 | 6197.43  |
| C    | -379.00  | 112152.35 | 9484.482310  | 1137.34  |

Notice that the **minimum Weekly\_Sales** is negative because some stores had more returns than sales.

**For each store Type, aggregating Unemployment and Fuel\_Price to get min, max, mean, and median**

In \[45]:

```
walmart_unemp_fuel_stats = walmart.groupby('Type')[['Unemployment','Fuel_Price']].agg([np.min,np.max,np.mean,np.median])
walmart_unemp_fuel_stats
```

Out\[45]:

|      | Unemployment | Fuel\_Price |          |        |       |       |          |        |
| ---- | ------------ | ----------- | -------- | ------ | ----- | ----- | -------- | ------ |
|      | amin         | amax        | mean     | median | amin  | amax  | mean     | median |
| Type |              |             |          |        |       |       |          |        |
| A    | 3.879        | 14.313      | 7.798863 | 7.818  | 2.472 | 4.468 | 3.343295 | 3.416  |
| B    | 4.125        | 14.313      | 7.936579 | 7.874  | 2.514 | 4.468 | 3.381915 | 3.494  |
| C    | 5.217        | 14.313      | 8.948222 | 8.300  | 2.514 | 4.468 | 3.363569 | 3.417  |

## Pivot tables <a href="#pivot-tables" id="pivot-tables"></a>

Pivot tables are another way of calculating grouped summary statistics. Basically pivot tables are used in spreadsheets, if you have ever used spreadsheets then chances are you have used pivot tables. Let's see how to create pivot tables in pandas.

**Pivoting on one variable**

We'll perform calculations using .pivot\_table() to replicate the calculations we performed in the .groupby().

_**Pivoting for mean Weekly\_Sales for each store Type**_

In \[46]:

```
mean_sales_by_type = walmart.pivot_table(values="Weekly_Sales", index="Type")
mean_sales_by_type
```

Out\[46]:

|      | Weekly\_Sales |
| ---- | ------------- |
| Type |               |
| A    | 20079.169258  |
| B    | 12263.647825  |
| C    | 9484.482310   |

_**Pivoting for mean and median Weekly\_Sales for each store Type**_

In \[47]:

```
mean_med_sales_by_type = walmart.pivot_table(values="Weekly_Sales", index="Type", aggfunc=[np.mean,np.median])
mean_med_sales_by_type
```

Out\[47]:

|      | mean          | median        |
| ---- | ------------- | ------------- |
|      | Weekly\_Sales | Weekly\_Sales |
| Type |               |               |
| A    | 20079.169258  | 10096.75      |
| B    | 12263.647825  | 6197.43       |
| C    | 9484.482310   | 1137.34       |

_**Pivoting for mean Seekly\_Sales by store Type and Holiday**_

In \[48]:

```
mean_sales_by_type_holiday = walmart.pivot_table(values="Weekly_Sales", index="Type", columns='Is_Holiday')
mean_sales_by_type_holiday
```

Out\[48]:

| Is\_Holiday | False        | True         |
| ----------- | ------------ | ------------ |
| Type        |              |              |
| A           | 20009.541574 | 21001.295283 |
| B           | 12166.429612 | 13549.646294 |
| C           | 9464.078381  | 9757.554889  |

## Fill in missing values and sum values with pivot tables <a href="#fill-in-missing-values-and-sum-values-with-pivot-tables" id="fill-in-missing-values-and-sum-values-with-pivot-tables"></a>

**.pivot\_table()** method has several useful arguments, including _**fill\_value and margins.**_

**fill\_value:** replaces missing values with real value.\
**margins:** is a shortcut for when we pivoted by two variables, but also wanted to pivot by each of those variables separately, it gives the row and column totals of the pivot table contents.

**mean of Weekly\_Sales by Department and Type, fill missing values with 0**

In \[49]:

```
walmart.pivot_table(values='Weekly_Sales', index='Department', columns='Type', fill_value=0)
```

Out\[49]:

| Type       | A            | B            | C            |
| ---------- | ------------ | ------------ | ------------ |
| Department |              |              |              |
| 1          | 23280.657103 | 17821.729825 | 8955.170884  |
| 2          | 51935.206120 | 43359.816952 | 14398.908941 |
| 3          | 14044.489715 | 12880.306941 | 803.546661   |
| 4          | 33128.245264 | 21457.823086 | 13506.047051 |
| 5          | 26589.677249 | 21109.894917 | 766.519121   |
| ...        | ...          | ...          | ...          |
| 95         | 97473.593714 | 41428.486751 | 50990.968371 |
| 96         | 19771.434235 | 4874.171608  | 15720.388253 |
| 97         | 21937.066379 | 3726.370891  | 13468.309357 |
| 98         | 10971.473930 | 317.638051   | 5406.640087  |
| 99         | 486.289516   | 21.008889    | 3.332143     |

81 rows × 3 columns

**mean Weekly\_Sales by Department and Type, fill missing values with 0s, sum all rows and cols**

In \[50]:

```
walmart.pivot_table(values="Weekly_Sales", index="Department", columns="Type", fill_value=0, margins=True)
```

Out\[50]:

| Type       | A            | B            | C            | All          |
| ---------- | ------------ | ------------ | ------------ | ------------ |
| Department |              |              |              |              |
| 1          | 23280.657103 | 17821.729825 | 8955.170884  | 19304.958040 |
| 2          | 51935.206120 | 43359.816952 | 14398.908941 | 43558.699406 |
| 3          | 14044.489715 | 12880.306941 | 803.546661   | 11880.837545 |
| 4          | 33128.245264 | 21457.823086 | 13506.047051 | 26111.912583 |
| 5          | 26589.677249 | 21109.894917 | 766.519121   | 21218.756123 |
| ...        | ...          | ...          | ...          | ...          |
| 96         | 19771.434235 | 4874.171608  | 15720.388253 | 15212.524956 |
| 97         | 21937.066379 | 3726.370891  | 13468.309357 | 14291.078869 |
| 98         | 10971.473930 | 317.638051   | 5406.640087  | 6804.735435  |
| 99         | 486.289516   | 21.008889    | 3.332143     | 468.071664   |
| All        | 20079.169258 | 12263.647825 | 9484.482310  | 15983.429692 |

82 rows × 4 columns

![](<.gitbook/assets/image (10).png>)
