# DateTime In Pandas

![](<.gitbook/assets/image (33).png>)

## Datetime In Pandas <a href="#datetime-in-pandas" id="datetime-in-pandas"></a>

While working on Datasets, you may come across datetimes columns many times. Dealing with dates is a little different than other types of data. But Pandas is a really intelligent library that offers many features to deal with datetime . We will use Walmart Dataset to deal with date time.

## Loading the Datasets <a href="#loading-the-datasets" id="loading-the-datasets"></a>

In \[1]:

```
import pandas as pd
df = pd.read_csv('walmart.csv')
df
```

Out\[1]:

|        | Store | Type | Department | Weekly\_Sales | Is\_Holiday | Temperature | Fuel\_Price | Unemployment | Date1      | Date2      |
| ------ | ----- | ---- | ---------- | ------------- | ----------- | ----------- | ----------- | ------------ | ---------- | ---------- |
| 0      | 1     | A    | 1          | 57258.43      | False       | 62.27       | 2.719       | 7.808        | 01-01-2010 | 16-06-2022 |
| 1      | 1     | A    | 1          | 16333.14      | False       | 80.91       | 2.669       | 7.787        | 07-03-2010 | 07-04-2010 |
| 2      | 1     | A    | 1          | 19403.54      | False       | 46.63       | 2.561       | 8.106        | 26-02-2012 | 27-02-2012 |
| 3      | 1     | A    | 1          | 22517.56      | False       | 49.27       | 2.708       | 7.838        | 12-03-2011 | 12-03-2012 |
| 4      | 1     | A    | 1          | 17596.96      | False       | 66.32       | 2.808       | 7.808        | 16-04-2010 | 16-04-2010 |
| ...    | ...   | ...  | ...        | ...           | ...         | ...         | ...         | ...          | ...        | ...        |
| 282446 | 45    | B    | 98         | 467.30        | False       | 65.32       | 4.038       | 8.684        | 21-09-2012 | 21-09-2012 |
| 282447 | 45    | B    | 98         | 508.37        | False       | 64.88       | 3.997       | 8.684        | 28-09-2012 | 28-09-2012 |
| 282448 | 45    | B    | 98         | 770.86        | True        | 37.00       | 3.640       | 8.424        | 02-10-2012 | 02-10-2012 |
| 282449 | 45    | B    | 98         | 727.49        | False       | 78.65       | 3.722       | 8.684        | 08-10-2012 | 08-10-2012 |
| 282450 | 45    | B    | 98         | 893.60        | False       | 61.24       | 3.889       | 8.567        | 05-11-2012 | 05-11-2012 |

282451 rows × 10 columns

**Let's Check Data Types of Column Date1 and Date2 with info()**

In \[2]:

```
df.info()
```

```
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 282451 entries, 0 to 282450
Data columns (total 10 columns):
 #   Column        Non-Null Count   Dtype  
---  ------        --------------   -----  
 0   Store         282451 non-null  int64  
 1   Type          282451 non-null  object 
 2   Department    282451 non-null  int64  
 3   Weekly_Sales  282451 non-null  float64
 4   Is_Holiday    282451 non-null  bool   
 5   Temperature   282451 non-null  float64
 6   Fuel_Price    282451 non-null  float64
 7   Unemployment  282451 non-null  float64
 8   Date1         282451 non-null  object 
 9   Date2         282451 non-null  object 
dtypes: bool(1), float64(4), int64(2), object(3)
memory usage: 19.7+ MB
```

As you can see , Date1 and Date2 are treated as **Object** here. Firstly we need to convert them in Datetime.

## Convert Columns In Datetime Datatype: <a href="#convert-columns-in-datetime-datatype" id="convert-columns-in-datetime-datatype"></a>

To convert a column in Datetime , We need to use _**to\_datetime**_ method and also specify the format of datetime.

while converting column in Datetime , We must specify the format of Datetime with format specifier. You can find all the directives that we use here : [Datetime format](https://docs.python.org/3/library/datetime.html#strftime-and-strptime-format-codes)

In \[3]:

```
df['Date1'] = pd.to_datetime(df['Date1'],format = '%d-%m-%Y')
df['Date2'] = pd.to_datetime(df['Date2'],format = '%d-%m-%Y')
df
```

Out\[3]:

|        | Store | Type | Department | Weekly\_Sales | Is\_Holiday | Temperature | Fuel\_Price | Unemployment | Date1      | Date2      |
| ------ | ----- | ---- | ---------- | ------------- | ----------- | ----------- | ----------- | ------------ | ---------- | ---------- |
| 0      | 1     | A    | 1          | 57258.43      | False       | 62.27       | 2.719       | 7.808        | 2010-01-01 | 2022-06-16 |
| 1      | 1     | A    | 1          | 16333.14      | False       | 80.91       | 2.669       | 7.787        | 2010-03-07 | 2010-04-07 |
| 2      | 1     | A    | 1          | 19403.54      | False       | 46.63       | 2.561       | 8.106        | 2012-02-26 | 2012-02-27 |
| 3      | 1     | A    | 1          | 22517.56      | False       | 49.27       | 2.708       | 7.838        | 2011-03-12 | 2012-03-12 |
| 4      | 1     | A    | 1          | 17596.96      | False       | 66.32       | 2.808       | 7.808        | 2010-04-16 | 2010-04-16 |
| ...    | ...   | ...  | ...        | ...           | ...         | ...         | ...         | ...          | ...        | ...        |
| 282446 | 45    | B    | 98         | 467.30        | False       | 65.32       | 4.038       | 8.684        | 2012-09-21 | 2012-09-21 |
| 282447 | 45    | B    | 98         | 508.37        | False       | 64.88       | 3.997       | 8.684        | 2012-09-28 | 2012-09-28 |
| 282448 | 45    | B    | 98         | 770.86        | True        | 37.00       | 3.640       | 8.424        | 2012-10-02 | 2012-10-02 |
| 282449 | 45    | B    | 98         | 727.49        | False       | 78.65       | 3.722       | 8.684        | 2012-10-08 | 2012-10-08 |
| 282450 | 45    | B    | 98         | 893.60        | False       | 61.24       | 3.889       | 8.567        | 2012-11-05 | 2012-11-05 |

282451 rows × 10 columns

**Let's Check Data Types of Column Date1 and Date2 with info() again.**

In \[4]:

```
df.info()
```

```
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 282451 entries, 0 to 282450
Data columns (total 10 columns):
 #   Column        Non-Null Count   Dtype         
---  ------        --------------   -----         
 0   Store         282451 non-null  int64         
 1   Type          282451 non-null  object        
 2   Department    282451 non-null  int64         
 3   Weekly_Sales  282451 non-null  float64       
 4   Is_Holiday    282451 non-null  bool          
 5   Temperature   282451 non-null  float64       
 6   Fuel_Price    282451 non-null  float64       
 7   Unemployment  282451 non-null  float64       
 8   Date1         282451 non-null  datetime64[ns]
 9   Date2         282451 non-null  datetime64[ns]
dtypes: bool(1), datetime64[ns](2), float64(4), int64(2), object(1)
memory usage: 19.7+ MB
```

As you can see , Date1 and Date2 are treated as **Datetime** here.

Now that we have covered these columns in Datetime , let us perform some basic operations of Datetime.

## Filtering In Datetime: <a href="#filtering-in-datetime" id="filtering-in-datetime"></a>

You can perform filters with **.loc** on datetime. Suppose i want all the data dated after 2010.

In \[5]:

```
df.loc[df['Date1']>'2010']
```

Out\[5]:

|        | Store | Type | Department | Weekly\_Sales | Is\_Holiday | Temperature | Fuel\_Price | Unemployment | Date1      | Date2      |
| ------ | ----- | ---- | ---------- | ------------- | ----------- | ----------- | ----------- | ------------ | ---------- | ---------- |
| 1      | 1     | A    | 1          | 16333.14      | False       | 80.91       | 2.669       | 7.787        | 2010-03-07 | 2010-04-07 |
| 2      | 1     | A    | 1          | 19403.54      | False       | 46.63       | 2.561       | 8.106        | 2012-02-26 | 2012-02-27 |
| 3      | 1     | A    | 1          | 22517.56      | False       | 49.27       | 2.708       | 7.838        | 2011-03-12 | 2012-03-12 |
| 4      | 1     | A    | 1          | 17596.96      | False       | 66.32       | 2.808       | 7.808        | 2010-04-16 | 2010-04-16 |
| 5      | 1     | A    | 1          | 16555.11      | False       | 67.41       | 2.780       | 7.808        | 2010-04-30 | 2010-04-30 |
| ...    | ...   | ...  | ...        | ...           | ...         | ...         | ...         | ...          | ...        | ...        |
| 282446 | 45    | B    | 98         | 467.30        | False       | 65.32       | 4.038       | 8.684        | 2012-09-21 | 2012-09-21 |
| 282447 | 45    | B    | 98         | 508.37        | False       | 64.88       | 3.997       | 8.684        | 2012-09-28 | 2012-09-28 |
| 282448 | 45    | B    | 98         | 770.86        | True        | 37.00       | 3.640       | 8.424        | 2012-10-02 | 2012-10-02 |
| 282449 | 45    | B    | 98         | 727.49        | False       | 78.65       | 3.722       | 8.684        | 2012-10-08 | 2012-10-08 |
| 282450 | 45    | B    | 98         | 893.60        | False       | 61.24       | 3.889       | 8.567        | 2012-11-05 | 2012-11-05 |

282450 rows × 10 columns

As you can see here **.loc** works differently. when you say i want data where Date is greater than 2010. Pandas filters the data after **1st January 2010**. So If you filter Data after **1st January 2010**, It will give the same result.

In \[6]:

```
df.loc[df['Date1']>'2010-01-01']
```

Out\[6]:

|        | Store | Type | Department | Weekly\_Sales | Is\_Holiday | Temperature | Fuel\_Price | Unemployment | Date1      | Date2      |
| ------ | ----- | ---- | ---------- | ------------- | ----------- | ----------- | ----------- | ------------ | ---------- | ---------- |
| 1      | 1     | A    | 1          | 16333.14      | False       | 80.91       | 2.669       | 7.787        | 2010-03-07 | 2010-04-07 |
| 2      | 1     | A    | 1          | 19403.54      | False       | 46.63       | 2.561       | 8.106        | 2012-02-26 | 2012-02-27 |
| 3      | 1     | A    | 1          | 22517.56      | False       | 49.27       | 2.708       | 7.838        | 2011-03-12 | 2012-03-12 |
| 4      | 1     | A    | 1          | 17596.96      | False       | 66.32       | 2.808       | 7.808        | 2010-04-16 | 2010-04-16 |
| 5      | 1     | A    | 1          | 16555.11      | False       | 67.41       | 2.780       | 7.808        | 2010-04-30 | 2010-04-30 |
| ...    | ...   | ...  | ...        | ...           | ...         | ...         | ...         | ...          | ...        | ...        |
| 282446 | 45    | B    | 98         | 467.30        | False       | 65.32       | 4.038       | 8.684        | 2012-09-21 | 2012-09-21 |
| 282447 | 45    | B    | 98         | 508.37        | False       | 64.88       | 3.997       | 8.684        | 2012-09-28 | 2012-09-28 |
| 282448 | 45    | B    | 98         | 770.86        | True        | 37.00       | 3.640       | 8.424        | 2012-10-02 | 2012-10-02 |
| 282449 | 45    | B    | 98         | 727.49        | False       | 78.65       | 3.722       | 8.684        | 2012-10-08 | 2012-10-08 |
| 282450 | 45    | B    | 98         | 893.60        | False       | 61.24       | 3.889       | 8.567        | 2012-11-05 | 2012-11-05 |

282450 rows × 10 columns

If you want to include data of 1st January 2010 , You will also include 2010 in your condition, something like this:

In \[7]:

```
df.loc[df['Date1']>='2010']
```

Out\[7]:

|        | Store | Type | Department | Weekly\_Sales | Is\_Holiday | Temperature | Fuel\_Price | Unemployment | Date1      | Date2      |
| ------ | ----- | ---- | ---------- | ------------- | ----------- | ----------- | ----------- | ------------ | ---------- | ---------- |
| 0      | 1     | A    | 1          | 57258.43      | False       | 62.27       | 2.719       | 7.808        | 2010-01-01 | 2022-06-16 |
| 1      | 1     | A    | 1          | 16333.14      | False       | 80.91       | 2.669       | 7.787        | 2010-03-07 | 2010-04-07 |
| 2      | 1     | A    | 1          | 19403.54      | False       | 46.63       | 2.561       | 8.106        | 2012-02-26 | 2012-02-27 |
| 3      | 1     | A    | 1          | 22517.56      | False       | 49.27       | 2.708       | 7.838        | 2011-03-12 | 2012-03-12 |
| 4      | 1     | A    | 1          | 17596.96      | False       | 66.32       | 2.808       | 7.808        | 2010-04-16 | 2010-04-16 |
| ...    | ...   | ...  | ...        | ...           | ...         | ...         | ...         | ...          | ...        | ...        |
| 282446 | 45    | B    | 98         | 467.30        | False       | 65.32       | 4.038       | 8.684        | 2012-09-21 | 2012-09-21 |
| 282447 | 45    | B    | 98         | 508.37        | False       | 64.88       | 3.997       | 8.684        | 2012-09-28 | 2012-09-28 |
| 282448 | 45    | B    | 98         | 770.86        | True        | 37.00       | 3.640       | 8.424        | 2012-10-02 | 2012-10-02 |
| 282449 | 45    | B    | 98         | 727.49        | False       | 78.65       | 3.722       | 8.684        | 2012-10-08 | 2012-10-08 |
| 282450 | 45    | B    | 98         | 893.60        | False       | 61.24       | 3.889       | 8.567        | 2012-11-05 | 2012-11-05 |

282451 rows × 10 columns

In \[8]:

```
df.loc[df['Date1']>='2010-01-01']
```

Out\[8]:

|        | Store | Type | Department | Weekly\_Sales | Is\_Holiday | Temperature | Fuel\_Price | Unemployment | Date1      | Date2      |
| ------ | ----- | ---- | ---------- | ------------- | ----------- | ----------- | ----------- | ------------ | ---------- | ---------- |
| 0      | 1     | A    | 1          | 57258.43      | False       | 62.27       | 2.719       | 7.808        | 2010-01-01 | 2022-06-16 |
| 1      | 1     | A    | 1          | 16333.14      | False       | 80.91       | 2.669       | 7.787        | 2010-03-07 | 2010-04-07 |
| 2      | 1     | A    | 1          | 19403.54      | False       | 46.63       | 2.561       | 8.106        | 2012-02-26 | 2012-02-27 |
| 3      | 1     | A    | 1          | 22517.56      | False       | 49.27       | 2.708       | 7.838        | 2011-03-12 | 2012-03-12 |
| 4      | 1     | A    | 1          | 17596.96      | False       | 66.32       | 2.808       | 7.808        | 2010-04-16 | 2010-04-16 |
| ...    | ...   | ...  | ...        | ...           | ...         | ...         | ...         | ...          | ...        | ...        |
| 282446 | 45    | B    | 98         | 467.30        | False       | 65.32       | 4.038       | 8.684        | 2012-09-21 | 2012-09-21 |
| 282447 | 45    | B    | 98         | 508.37        | False       | 64.88       | 3.997       | 8.684        | 2012-09-28 | 2012-09-28 |
| 282448 | 45    | B    | 98         | 770.86        | True        | 37.00       | 3.640       | 8.424        | 2012-10-02 | 2012-10-02 |
| 282449 | 45    | B    | 98         | 727.49        | False       | 78.65       | 3.722       | 8.684        | 2012-10-08 | 2012-10-08 |
| 282450 | 45    | B    | 98         | 893.60        | False       | 61.24       | 3.889       | 8.567        | 2012-11-05 | 2012-11-05 |

282451 rows × 10 columns

If you want data from **1st May of 2010** , You can write something like this:



```
df.loc[df['Date1']>='2010-05']
```

Out\[9]:

|        | Store | Type | Department | Weekly\_Sales | Is\_Holiday | Temperature | Fuel\_Price | Unemployment | Date1      | Date2      |
| ------ | ----- | ---- | ---------- | ------------- | ----------- | ----------- | ----------- | ------------ | ---------- | ---------- |
| 2      | 1     | A    | 1          | 19403.54      | False       | 46.63       | 2.561       | 8.106        | 2012-02-26 | 2012-02-27 |
| 3      | 1     | A    | 1          | 22517.56      | False       | 49.27       | 2.708       | 7.838        | 2011-03-12 | 2012-03-12 |
| 7      | 1     | A    | 1          | 34238.88      | False       | 58.74       | 2.689       | 7.838        | 2010-05-11 | 2010-05-11 |
| 8      | 1     | A    | 1          | 18926.74      | False       | 74.78       | 2.854       | 7.808        | 2010-05-14 | 2010-05-14 |
| 9      | 1     | A    | 1          | 14773.04      | False       | 76.44       | 2.826       | 7.808        | 2010-05-21 | 2010-05-21 |
| ...    | ...   | ...  | ...        | ...           | ...         | ...         | ...         | ...          | ...        | ...        |
| 282446 | 45    | B    | 98         | 467.30        | False       | 65.32       | 4.038       | 8.684        | 2012-09-21 | 2012-09-21 |
| 282447 | 45    | B    | 98         | 508.37        | False       | 64.88       | 3.997       | 8.684        | 2012-09-28 | 2012-09-28 |
| 282448 | 45    | B    | 98         | 770.86        | True        | 37.00       | 3.640       | 8.424        | 2012-10-02 | 2012-10-02 |
| 282449 | 45    | B    | 98         | 727.49        | False       | 78.65       | 3.722       | 8.684        | 2012-10-08 | 2012-10-08 |
| 282450 | 45    | B    | 98         | 893.60        | False       | 61.24       | 3.889       | 8.567        | 2012-11-05 | 2012-11-05 |

256854 rows × 10 columns

You can also give specific dates including year , month and day.

In \[10]:

```
df.loc[df['Date1']>='2010-05-27']
```

Out\[10]:

|        | Store | Type | Department | Weekly\_Sales | Is\_Holiday | Temperature | Fuel\_Price | Unemployment | Date1      | Date2      |
| ------ | ----- | ---- | ---------- | ------------- | ----------- | ----------- | ----------- | ------------ | ---------- | ---------- |
| 2      | 1     | A    | 1          | 19403.54      | False       | 46.63       | 2.561       | 8.106        | 2012-02-26 | 2012-02-27 |
| 3      | 1     | A    | 1          | 22517.56      | False       | 49.27       | 2.708       | 7.838        | 2011-03-12 | 2012-03-12 |
| 10     | 1     | A    | 1          | 16216.27      | False       | 84.11       | 2.637       | 7.808        | 2010-06-18 | 2010-06-18 |
| 11     | 1     | A    | 1          | 16328.72      | False       | 84.34       | 2.653       | 7.808        | 2010-06-25 | 2010-06-25 |
| 12     | 1     | A    | 1          | 17413.94      | False       | 72.55       | 2.835       | 7.808        | 2010-07-05 | 2010-07-05 |
| ...    | ...   | ...  | ...        | ...           | ...         | ...         | ...         | ...          | ...        | ...        |
| 282446 | 45    | B    | 98         | 467.30        | False       | 65.32       | 4.038       | 8.684        | 2012-09-21 | 2012-09-21 |
| 282447 | 45    | B    | 98         | 508.37        | False       | 64.88       | 3.997       | 8.684        | 2012-09-28 | 2012-09-28 |
| 282448 | 45    | B    | 98         | 770.86        | True        | 37.00       | 3.640       | 8.424        | 2012-10-02 | 2012-10-02 |
| 282449 | 45    | B    | 98         | 727.49        | False       | 78.65       | 3.722       | 8.684        | 2012-10-08 | 2012-10-08 |
| 282450 | 45    | B    | 98         | 893.60        | False       | 61.24       | 3.889       | 8.567        | 2012-11-05 | 2012-11-05 |

246996 rows × 10 columns

You can also find data for a Specific Date, Say i want to Know Walmart sales on 8th october of 2012.

In \[11]:

```
df.loc[df['Date1']=='2012-10-08']
```

Out\[11]:

|        | Store | Type | Department | Weekly\_Sales | Is\_Holiday | Temperature | Fuel\_Price | Unemployment | Date1      | Date2      |
| ------ | ----- | ---- | ---------- | ------------- | ----------- | ----------- | ----------- | ------------ | ---------- | ---------- |
| 90     | 1     | A    | 1          | 16119.92      | False       | 85.05       | 3.494       | 6.908        | 2012-10-08 | 2012-10-08 |
| 186    | 1     | A    | 2          | 46729.91      | False       | 85.05       | 3.494       | 6.908        | 2012-10-08 | 2012-10-08 |
| 375    | 1     | A    | 4          | 40343.83      | False       | 85.05       | 3.494       | 6.908        | 2012-10-08 | 2012-10-08 |
| 580    | 1     | A    | 6          | -139.65       | False       | 85.05       | 3.494       | 6.908        | 2012-10-08 | 2012-10-08 |
| 670    | 1     | A    | 7          | 16552.49      | False       | 85.05       | 3.494       | 6.908        | 2012-10-08 | 2012-10-08 |
| ...    | ...   | ...  | ...        | ...           | ...         | ...         | ...         | ...          | ...        | ...        |
| 281792 | 45    | B    | 90         | 22399.66      | False       | 78.65       | 3.722       | 8.684        | 2012-10-08 | 2012-10-08 |
| 282067 | 45    | B    | 93         | 3171.56       | False       | 78.65       | 3.722       | 8.684        | 2012-10-08 | 2012-10-08 |
| 282253 | 45    | B    | 95         | 54892.83      | False       | 78.65       | 3.722       | 8.684        | 2012-10-08 | 2012-10-08 |
| 282353 | 45    | B    | 97         | 6361.79       | False       | 78.65       | 3.722       | 8.684        | 2012-10-08 | 2012-10-08 |
| 282449 | 45    | B    | 98         | 727.49        | False       | 78.65       | 3.722       | 8.684        | 2012-10-08 | 2012-10-08 |

1964 rows × 10 columns

## Multiple Conditions In Datetime: <a href="#multiple-conditions-in-datetime" id="multiple-conditions-in-datetime"></a>

There may occur a situation when you need only one year date or between a range of Date. For example, i want data ranged between 2010 to 2011.

In \[12]:

```
edf = df.loc[(df['Date1']>='2010') & (df['Date1']<'2011-01-01')]
edf
```

Out\[12]:

|        | Store | Type | Department | Weekly\_Sales | Is\_Holiday | Temperature | Fuel\_Price | Unemployment | Date1      | Date2      |
| ------ | ----- | ---- | ---------- | ------------- | ----------- | ----------- | ----------- | ------------ | ---------- | ---------- |
| 0      | 1     | A    | 1          | 57258.43      | False       | 62.27       | 2.719       | 7.808        | 2010-01-01 | 2022-06-16 |
| 1      | 1     | A    | 1          | 16333.14      | False       | 80.91       | 2.669       | 7.787        | 2010-03-07 | 2010-04-07 |
| 4      | 1     | A    | 1          | 17596.96      | False       | 66.32       | 2.808       | 7.808        | 2010-04-16 | 2010-04-16 |
| 5      | 1     | A    | 1          | 16555.11      | False       | 67.41       | 2.780       | 7.808        | 2010-04-30 | 2010-04-30 |
| 6      | 1     | A    | 1          | 21827.90      | False       | 46.50       | 2.625       | 8.106        | 2010-04-03 | 2010-04-03 |
| ...    | ...   | ...  | ...        | ...           | ...         | ...         | ...         | ...          | ...        | ...        |
| 282379 | 45    | B    | 98         | 553.25        | True        | 27.73       | 2.773       | 8.992        | 2010-12-02 | 2010-12-02 |
| 282380 | 45    | B    | 98         | 18.50         | False       | 45.80       | 2.818       | 8.992        | 2010-12-03 | 2010-12-03 |
| 282381 | 45    | B    | 98         | 59.46         | False       | 46.14       | 2.931       | 8.724        | 2010-12-11 | 2010-12-11 |
| 282382 | 45    | B    | 98         | 222.48        | False       | 30.51       | 3.140       | 8.724        | 2010-12-17 | 2010-12-17 |
| 282383 | 45    | B    | 98         | 74.55         | True        | 29.67       | 3.179       | 8.724        | 2010-12-31 | 2010-12-31 |

94467 rows × 10 columns

## sort date : <a href="#sort-date" id="sort-date"></a>

You can also sort date with sort\_values() function.

In \[13]:

```
edf.sort_values('Date1')
```

Out\[13]:

|        | Store | Type | Department | Weekly\_Sales | Is\_Holiday | Temperature | Fuel\_Price | Unemployment | Date1      | Date2      |
| ------ | ----- | ---- | ---------- | ------------- | ----------- | ----------- | ----------- | ------------ | ---------- | ---------- |
| 0      | 1     | A    | 1          | 57258.43      | False       | 62.27       | 2.719       | 7.808        | 2010-01-01 | 2022-06-16 |
| 23653  | 4     | A    | 44         | 5534.06       | False       | 63.96       | 2.619       | 7.127        | 2010-01-10 | 2010-01-10 |
| 104676 | 16    | B    | 85         | 3560.28       | False       | 59.39       | 2.759       | 6.986        | 2010-01-10 | 2010-01-10 |
| 180948 | 28    | A    | 25         | 14757.48      | False       | 85.20       | 3.001       | 14.313       | 2010-01-10 | 2010-01-10 |
| 238501 | 38    | C    | 16         | 715.83        | False       | 85.20       | 3.001       | 14.313       | 2010-01-10 | 2010-01-10 |
| ...    | ...   | ...  | ...        | ...           | ...         | ...         | ...         | ...          | ...        | ...        |
| 50724  | 8     | A    | 58         | 458.00        | True        | 41.47       | 2.943       | 6.433        | 2010-12-31 | 2010-12-31 |
| 233132 | 37    | C    | 9          | 66.37         | True        | 52.88       | 2.943       | 8.476        | 2010-12-31 | 2010-12-31 |
| 50437  | 8     | A    | 54         | -7.08         | True        | 41.47       | 2.943       | 6.433        | 2010-12-31 | 2010-12-31 |
| 232180 | 36    | A    | 97         | 6204.11       | True        | 52.88       | 2.949       | 8.476        | 2010-12-31 | 2010-12-31 |
| 282383 | 45    | B    | 98         | 74.55         | True        | 29.67       | 3.179       | 8.724        | 2010-12-31 | 2010-12-31 |

94467 rows × 10 columns

## Set Datetime as Index: <a href="#set-datetime-as-index" id="set-datetime-as-index"></a>

In \[14]:

```
edf = df.set_index('Date1')
edf
```

Out\[14]:

|            | Store | Type | Department | Weekly\_Sales | Is\_Holiday | Temperature | Fuel\_Price | Unemployment | Date2      |
| ---------- | ----- | ---- | ---------- | ------------- | ----------- | ----------- | ----------- | ------------ | ---------- |
| Date1      |       |      |            |               |             |             |             |              |            |
| 2010-01-01 | 1     | A    | 1          | 57258.43      | False       | 62.27       | 2.719       | 7.808        | 2022-06-16 |
| 2010-03-07 | 1     | A    | 1          | 16333.14      | False       | 80.91       | 2.669       | 7.787        | 2010-04-07 |
| 2012-02-26 | 1     | A    | 1          | 19403.54      | False       | 46.63       | 2.561       | 8.106        | 2012-02-27 |
| 2011-03-12 | 1     | A    | 1          | 22517.56      | False       | 49.27       | 2.708       | 7.838        | 2012-03-12 |
| 2010-04-16 | 1     | A    | 1          | 17596.96      | False       | 66.32       | 2.808       | 7.808        | 2010-04-16 |
| ...        | ...   | ...  | ...        | ...           | ...         | ...         | ...         | ...          | ...        |
| 2012-09-21 | 45    | B    | 98         | 467.30        | False       | 65.32       | 4.038       | 8.684        | 2012-09-21 |
| 2012-09-28 | 45    | B    | 98         | 508.37        | False       | 64.88       | 3.997       | 8.684        | 2012-09-28 |
| 2012-10-02 | 45    | B    | 98         | 770.86        | True        | 37.00       | 3.640       | 8.424        | 2012-10-02 |
| 2012-10-08 | 45    | B    | 98         | 727.49        | False       | 78.65       | 3.722       | 8.684        | 2012-10-08 |
| 2012-11-05 | 45    | B    | 98         | 893.60        | False       | 61.24       | 3.889       | 8.567        | 2012-11-05 |

282451 rows × 9 columns

If you have set date as index , you can perform filtering very easily. Say if i want data range from 2010 to 2011 , we will slice it something like this :

In \[15]:

```
edf['2010':'2011']
```

Out\[15]:

|            | Store | Type | Department | Weekly\_Sales | Is\_Holiday | Temperature | Fuel\_Price | Unemployment | Date2      |
| ---------- | ----- | ---- | ---------- | ------------- | ----------- | ----------- | ----------- | ------------ | ---------- |
| Date1      |       |      |            |               |             |             |             |              |            |
| 2010-01-01 | 1     | A    | 1          | 57258.43      | False       | 62.27       | 2.719       | 7.808        | 2022-06-16 |
| 2010-03-07 | 1     | A    | 1          | 16333.14      | False       | 80.91       | 2.669       | 7.787        | 2010-04-07 |
| 2011-03-12 | 1     | A    | 1          | 22517.56      | False       | 49.27       | 2.708       | 7.838        | 2012-03-12 |
| 2010-04-16 | 1     | A    | 1          | 17596.96      | False       | 66.32       | 2.808       | 7.808        | 2010-04-16 |
| 2010-04-30 | 1     | A    | 1          | 16555.11      | False       | 67.41       | 2.780       | 7.808        | 2010-04-30 |
| ...        | ...   | ...  | ...        | ...           | ...         | ...         | ...         | ...          | ...        |
| 2011-11-11 | 45    | B    | 98         | 897.22        | False       | 47.65       | 3.530       | 8.523        | 2011-11-11 |
| 2011-11-18 | 45    | B    | 98         | 503.20        | False       | 51.34       | 3.530       | 8.523        | 2011-11-18 |
| 2011-12-08 | 45    | B    | 98         | 827.40        | False       | 77.00       | 3.812       | 8.625        | 2011-12-08 |
| 2011-12-23 | 45    | B    | 98         | 1084.78       | False       | 42.27       | 3.389       | 8.523        | 2011-12-23 |
| 2011-12-30 | 45    | B    | 98         | 553.21        | True        | 37.79       | 3.389       | 8.523        | 2011-12-30 |

197447 rows × 9 columns



```
edf['2010-03':'2011-02']
```

```
C:\Users\abhis\AppData\Local\Temp/ipykernel_1984/2244430576.py:1: FutureWarning: Value based partial slicing on non-monotonic DatetimeIndexes with non-existing keys is deprecated and will raise a KeyError in a future Version.
  edf['2010-03':'2011-02']
```

Out\[16]:

|            | Store | Type | Department | Weekly\_Sales | Is\_Holiday | Temperature | Fuel\_Price | Unemployment | Date2      |
| ---------- | ----- | ---- | ---------- | ------------- | ----------- | ----------- | ----------- | ------------ | ---------- |
| Date1      |       |      |            |               |             |             |             |              |            |
| 2010-03-07 | 1     | A    | 1          | 16333.14      | False       | 80.91       | 2.669       | 7.787        | 2010-04-07 |
| 2010-04-16 | 1     | A    | 1          | 17596.96      | False       | 66.32       | 2.808       | 7.808        | 2010-04-16 |
| 2010-04-30 | 1     | A    | 1          | 16555.11      | False       | 67.41       | 2.780       | 7.808        | 2010-04-30 |
| 2010-04-03 | 1     | A    | 1          | 21827.90      | False       | 46.50       | 2.625       | 8.106        | 2010-04-03 |
| 2010-05-11 | 1     | A    | 1          | 34238.88      | False       | 58.74       | 2.689       | 7.838        | 2010-05-11 |
| ...        | ...   | ...  | ...        | ...           | ...         | ...         | ...         | ...          | ...        |
| 2011-01-21 | 45    | B    | 98         | 2.00          | False       | 30.55       | 3.229       | 8.549        | 2011-01-21 |
| 2011-01-28 | 45    | B    | 98         | 77.00         | False       | 24.05       | 3.237       | 8.549        | 2011-01-28 |
| 2011-02-09 | 45    | B    | 98         | 601.42        | False       | 70.63       | 3.703       | 8.625        | 2011-02-09 |
| 2011-02-12 | 45    | B    | 98         | 538.51        | False       | 50.19       | 3.452       | 8.523        | 2011-02-12 |
| 2011-02-25 | 45    | B    | 98         | 675.26        | False       | 35.78       | 3.274       | 8.549        | 2011-02-25 |

102427 rows × 9 columns

## Get Difference of Days between Dates: <a href="#get-difference-of-days-between-dates" id="get-difference-of-days-between-dates"></a>

As we know we have two dates in our Dataset, we can perform easy subtraction among dates. So we are going to create a new Column containing number of days between two dates.

In \[17]:

```
df['number of days'] = df['Date2'] - df['Date1']
df
```

Out\[17]:

|        | Store | Type | Department | Weekly\_Sales | Is\_Holiday | Temperature | Fuel\_Price | Unemployment | Date1      | Date2      | number of days |
| ------ | ----- | ---- | ---------- | ------------- | ----------- | ----------- | ----------- | ------------ | ---------- | ---------- | -------------- |
| 0      | 1     | A    | 1          | 57258.43      | False       | 62.27       | 2.719       | 7.808        | 2010-01-01 | 2022-06-16 | 4549 days      |
| 1      | 1     | A    | 1          | 16333.14      | False       | 80.91       | 2.669       | 7.787        | 2010-03-07 | 2010-04-07 | 31 days        |
| 2      | 1     | A    | 1          | 19403.54      | False       | 46.63       | 2.561       | 8.106        | 2012-02-26 | 2012-02-27 | 1 days         |
| 3      | 1     | A    | 1          | 22517.56      | False       | 49.27       | 2.708       | 7.838        | 2011-03-12 | 2012-03-12 | 366 days       |
| 4      | 1     | A    | 1          | 17596.96      | False       | 66.32       | 2.808       | 7.808        | 2010-04-16 | 2010-04-16 | 0 days         |
| ...    | ...   | ...  | ...        | ...           | ...         | ...         | ...         | ...          | ...        | ...        | ...            |
| 282446 | 45    | B    | 98         | 467.30        | False       | 65.32       | 4.038       | 8.684        | 2012-09-21 | 2012-09-21 | 0 days         |
| 282447 | 45    | B    | 98         | 508.37        | False       | 64.88       | 3.997       | 8.684        | 2012-09-28 | 2012-09-28 | 0 days         |
| 282448 | 45    | B    | 98         | 770.86        | True        | 37.00       | 3.640       | 8.424        | 2012-10-02 | 2012-10-02 | 0 days         |
| 282449 | 45    | B    | 98         | 727.49        | False       | 78.65       | 3.722       | 8.684        | 2012-10-08 | 2012-10-08 | 0 days         |
| 282450 | 45    | B    | 98         | 893.60        | False       | 61.24       | 3.889       | 8.567        | 2012-11-05 | 2012-11-05 | 0 days         |

282451 rows × 11 columns

**Data Type of number of days is timedelta64.**

In \[18]:

```
print(df['number of days'].dtype)
```

```
timedelta64[ns]
```

## Let's Explore timedelta64ns : <a href="#lets-explore-timedelta64ns" id="lets-explore-timedelta64ns"></a>

What if i want number of _**Days**_ or _**Months**_ or _**Years**_ or _**Weeks**_ or in _**Minutes**_ between two dates. We will be using timedelta64. We will be using numpy to calculate these. Let us see how:

**Find Number of Months :**

In \[19]:

```
import numpy as np
df['number of months'] = df['number of days']/np.timedelta64(1,'M')
df[['Date1','Date2','number of days','number of months']]  #checking data related to dates only
```

Out\[19]:

|        | Date1      | Date2      | number of days | number of months |
| ------ | ---------- | ---------- | -------------- | ---------------- |
| 0      | 2010-01-01 | 2022-06-16 | 4549 days      | 149.456868       |
| 1      | 2010-03-07 | 2010-04-07 | 31 days        | 1.018501         |
| 2      | 2012-02-26 | 2012-02-27 | 1 days         | 0.032855         |
| 3      | 2011-03-12 | 2012-03-12 | 366 days       | 12.024888        |
| 4      | 2010-04-16 | 2010-04-16 | 0 days         | 0.000000         |
| ...    | ...        | ...        | ...            | ...              |
| 282446 | 2012-09-21 | 2012-09-21 | 0 days         | 0.000000         |
| 282447 | 2012-09-28 | 2012-09-28 | 0 days         | 0.000000         |
| 282448 | 2012-10-02 | 2012-10-02 | 0 days         | 0.000000         |
| 282449 | 2012-10-08 | 2012-10-08 | 0 days         | 0.000000         |
| 282450 | 2012-11-05 | 2012-11-05 | 0 days         | 0.000000         |

282451 rows × 4 columns

**Find number of years:**

In \[20]:

```
import numpy as np
df['number of years'] = df['number of days']/np.timedelta64(1,'Y')
df[['Date1','Date2','number of days','number of years']]  #checking data related to dates only
```

Out\[20]:

|        | Date1      | Date2      | number of days | number of years |
| ------ | ---------- | ---------- | -------------- | --------------- |
| 0      | 2010-01-01 | 2022-06-16 | 4549 days      | 12.454739       |
| 1      | 2010-03-07 | 2010-04-07 | 31 days        | 0.084875        |
| 2      | 2012-02-26 | 2012-02-27 | 1 days         | 0.002738        |
| 3      | 2011-03-12 | 2012-03-12 | 366 days       | 1.002074        |
| 4      | 2010-04-16 | 2010-04-16 | 0 days         | 0.000000        |
| ...    | ...        | ...        | ...            | ...             |
| 282446 | 2012-09-21 | 2012-09-21 | 0 days         | 0.000000        |
| 282447 | 2012-09-28 | 2012-09-28 | 0 days         | 0.000000        |
| 282448 | 2012-10-02 | 2012-10-02 | 0 days         | 0.000000        |
| 282449 | 2012-10-08 | 2012-10-08 | 0 days         | 0.000000        |
| 282450 | 2012-11-05 | 2012-11-05 | 0 days         | 0.000000        |

282451 rows × 4 columns

**Find number of weeks:**

In \[21]:

```
import numpy as np
df['number of weeks'] = df['number of days']/np.timedelta64(1,'W')
df[['Date1','Date2','number of days','number of weeks']]  #checking data related to dates only
```

Out\[21]:

|        | Date1      | Date2      | number of days | number of weeks |
| ------ | ---------- | ---------- | -------------- | --------------- |
| 0      | 2010-01-01 | 2022-06-16 | 4549 days      | 649.857143      |
| 1      | 2010-03-07 | 2010-04-07 | 31 days        | 4.428571        |
| 2      | 2012-02-26 | 2012-02-27 | 1 days         | 0.142857        |
| 3      | 2011-03-12 | 2012-03-12 | 366 days       | 52.285714       |
| 4      | 2010-04-16 | 2010-04-16 | 0 days         | 0.000000        |
| ...    | ...        | ...        | ...            | ...             |
| 282446 | 2012-09-21 | 2012-09-21 | 0 days         | 0.000000        |
| 282447 | 2012-09-28 | 2012-09-28 | 0 days         | 0.000000        |
| 282448 | 2012-10-02 | 2012-10-02 | 0 days         | 0.000000        |
| 282449 | 2012-10-08 | 2012-10-08 | 0 days         | 0.000000        |
| 282450 | 2012-11-05 | 2012-11-05 | 0 days         | 0.000000        |

282451 rows × 4 columns

**Find number of hours:**

In \[22]:

```
import numpy as np
df['number of hours'] = df['number of days']/np.timedelta64(1,'h')
df[['Date1','Date2','number of days','number of hours']]  #checking data related to dates only
```

Out\[22]:

|        | Date1      | Date2      | number of days | number of hours |
| ------ | ---------- | ---------- | -------------- | --------------- |
| 0      | 2010-01-01 | 2022-06-16 | 4549 days      | 109176.0        |
| 1      | 2010-03-07 | 2010-04-07 | 31 days        | 744.0           |
| 2      | 2012-02-26 | 2012-02-27 | 1 days         | 24.0            |
| 3      | 2011-03-12 | 2012-03-12 | 366 days       | 8784.0          |
| 4      | 2010-04-16 | 2010-04-16 | 0 days         | 0.0             |
| ...    | ...        | ...        | ...            | ...             |
| 282446 | 2012-09-21 | 2012-09-21 | 0 days         | 0.0             |
| 282447 | 2012-09-28 | 2012-09-28 | 0 days         | 0.0             |
| 282448 | 2012-10-02 | 2012-10-02 | 0 days         | 0.0             |
| 282449 | 2012-10-08 | 2012-10-08 | 0 days         | 0.0             |
| 282450 | 2012-11-05 | 2012-11-05 | 0 days         | 0.0             |

282451 rows × 4 columns

**Find number of minutes:**

In \[23]:

```
import numpy as np
df['number of minutes'] = df['number of days']/np.timedelta64(1,'m')
df[['Date1','Date2','number of days','number of minutes']]  #checking data related to dates only
```

Out\[23]:

|        | Date1      | Date2      | number of days | number of minutes |
| ------ | ---------- | ---------- | -------------- | ----------------- |
| 0      | 2010-01-01 | 2022-06-16 | 4549 days      | 6550560.0         |
| 1      | 2010-03-07 | 2010-04-07 | 31 days        | 44640.0           |
| 2      | 2012-02-26 | 2012-02-27 | 1 days         | 1440.0            |
| 3      | 2011-03-12 | 2012-03-12 | 366 days       | 527040.0          |
| 4      | 2010-04-16 | 2010-04-16 | 0 days         | 0.0               |
| ...    | ...        | ...        | ...            | ...               |
| 282446 | 2012-09-21 | 2012-09-21 | 0 days         | 0.0               |
| 282447 | 2012-09-28 | 2012-09-28 | 0 days         | 0.0               |
| 282448 | 2012-10-02 | 2012-10-02 | 0 days         | 0.0               |
| 282449 | 2012-10-08 | 2012-10-08 | 0 days         | 0.0               |
| 282450 | 2012-11-05 | 2012-11-05 | 0 days         | 0.0               |

282451 rows × 4 columns

**Find number of seconds:**

In \[24]:

```
import numpy as np
df['number of seconds'] = df['number of days']/np.timedelta64(1,'s')
df[['Date1','Date2','number of days','number of seconds']]  #checking data related to dates only
```

Out\[24]:

|        | Date1      | Date2      | number of days | number of seconds |
| ------ | ---------- | ---------- | -------------- | ----------------- |
| 0      | 2010-01-01 | 2022-06-16 | 4549 days      | 393033600.0       |
| 1      | 2010-03-07 | 2010-04-07 | 31 days        | 2678400.0         |
| 2      | 2012-02-26 | 2012-02-27 | 1 days         | 86400.0           |
| 3      | 2011-03-12 | 2012-03-12 | 366 days       | 31622400.0        |
| 4      | 2010-04-16 | 2010-04-16 | 0 days         | 0.0               |
| ...    | ...        | ...        | ...            | ...               |
| 282446 | 2012-09-21 | 2012-09-21 | 0 days         | 0.0               |
| 282447 | 2012-09-28 | 2012-09-28 | 0 days         | 0.0               |
| 282448 | 2012-10-02 | 2012-10-02 | 0 days         | 0.0               |
| 282449 | 2012-10-08 | 2012-10-08 | 0 days         | 0.0               |
| 282450 | 2012-11-05 | 2012-11-05 | 0 days         | 0.0               |

282451 rows × 4 columns

You can convert it in many different datetime units , to refer you can go [Datetime format.](https://docs.python.org/3/library/datetime.html#strftime-and-strptime-format-codes)

## How to convert multiple columns to Datetime: <a href="#how-to-convert-multiple-columns-to-datetime" id="how-to-convert-multiple-columns-to-datetime"></a>

In \[25]:

```
import pandas as pd
sdf = pd.read_csv('walmart.csv')
sdf
```

Out\[25]:

|        | Store | Type | Department | Weekly\_Sales | Is\_Holiday | Temperature | Fuel\_Price | Unemployment | Date1      | Date2      |
| ------ | ----- | ---- | ---------- | ------------- | ----------- | ----------- | ----------- | ------------ | ---------- | ---------- |
| 0      | 1     | A    | 1          | 57258.43      | False       | 62.27       | 2.719       | 7.808        | 01-01-2010 | 16-06-2022 |
| 1      | 1     | A    | 1          | 16333.14      | False       | 80.91       | 2.669       | 7.787        | 07-03-2010 | 07-04-2010 |
| 2      | 1     | A    | 1          | 19403.54      | False       | 46.63       | 2.561       | 8.106        | 26-02-2012 | 27-02-2012 |
| 3      | 1     | A    | 1          | 22517.56      | False       | 49.27       | 2.708       | 7.838        | 12-03-2011 | 12-03-2012 |
| 4      | 1     | A    | 1          | 17596.96      | False       | 66.32       | 2.808       | 7.808        | 16-04-2010 | 16-04-2010 |
| ...    | ...   | ...  | ...        | ...           | ...         | ...         | ...         | ...          | ...        | ...        |
| 282446 | 45    | B    | 98         | 467.30        | False       | 65.32       | 4.038       | 8.684        | 21-09-2012 | 21-09-2012 |
| 282447 | 45    | B    | 98         | 508.37        | False       | 64.88       | 3.997       | 8.684        | 28-09-2012 | 28-09-2012 |
| 282448 | 45    | B    | 98         | 770.86        | True        | 37.00       | 3.640       | 8.424        | 02-10-2012 | 02-10-2012 |
| 282449 | 45    | B    | 98         | 727.49        | False       | 78.65       | 3.722       | 8.684        | 08-10-2012 | 08-10-2012 |
| 282450 | 45    | B    | 98         | 893.60        | False       | 61.24       | 3.889       | 8.567        | 05-11-2012 | 05-11-2012 |

282451 rows × 10 columns

Here Date1 and Date2 are again objects , let us try to convert both of them in Datetime in a go. We need to use .apply() and apply datetime function to convert more than one column to Datetime.

In \[26]:

```
sdf[['Date1','Date2']] = sdf[['Date1','Date2']].apply(pd.to_datetime)
sdf
```

Out\[26]:

|        | Store | Type | Department | Weekly\_Sales | Is\_Holiday | Temperature | Fuel\_Price | Unemployment | Date1      | Date2      |
| ------ | ----- | ---- | ---------- | ------------- | ----------- | ----------- | ----------- | ------------ | ---------- | ---------- |
| 0      | 1     | A    | 1          | 57258.43      | False       | 62.27       | 2.719       | 7.808        | 2010-01-01 | 2022-06-16 |
| 1      | 1     | A    | 1          | 16333.14      | False       | 80.91       | 2.669       | 7.787        | 2010-07-03 | 2010-07-04 |
| 2      | 1     | A    | 1          | 19403.54      | False       | 46.63       | 2.561       | 8.106        | 2012-02-26 | 2012-02-27 |
| 3      | 1     | A    | 1          | 22517.56      | False       | 49.27       | 2.708       | 7.838        | 2011-12-03 | 2012-12-03 |
| 4      | 1     | A    | 1          | 17596.96      | False       | 66.32       | 2.808       | 7.808        | 2010-04-16 | 2010-04-16 |
| ...    | ...   | ...  | ...        | ...           | ...         | ...         | ...         | ...          | ...        | ...        |
| 282446 | 45    | B    | 98         | 467.30        | False       | 65.32       | 4.038       | 8.684        | 2012-09-21 | 2012-09-21 |
| 282447 | 45    | B    | 98         | 508.37        | False       | 64.88       | 3.997       | 8.684        | 2012-09-28 | 2012-09-28 |
| 282448 | 45    | B    | 98         | 770.86        | True        | 37.00       | 3.640       | 8.424        | 2012-02-10 | 2012-02-10 |
| 282449 | 45    | B    | 98         | 727.49        | False       | 78.65       | 3.722       | 8.684        | 2012-08-10 | 2012-08-10 |
| 282450 | 45    | B    | 98         | 893.60        | False       | 61.24       | 3.889       | 8.567        | 2012-05-11 | 2012-05-11 |

282451 rows × 10 columns

Let us check with dtypes :

In \[27]:

```
df[['Date1','Date2']].dtypes
```

Out\[27]:

```
Date1    datetime64[ns]
Date2    datetime64[ns]
dtype: object
```

## Date series: <a href="#date-series" id="date-series"></a>

There are numerous methods for date series that performs useful operations on a date. Let's go through them one by one.

You can always refer to this : [pandas date series documentation](https://pandas.pydata.org/docs/reference/api/pandas.Series.dt.html) for Datetime operations.

**How to get Day from a Date**

Suppose if i want a column of days from Date1 , we will apply a series method on Date1.

**Syntax : series.dt.day**

In \[28]:

```
df['day'] = df['Date1'].dt.day
df[['Date1','day']]
```

Out\[28]:

|        | Date1      | day |
| ------ | ---------- | --- |
| 0      | 2010-01-01 | 1   |
| 1      | 2010-03-07 | 7   |
| 2      | 2012-02-26 | 26  |
| 3      | 2011-03-12 | 12  |
| 4      | 2010-04-16 | 16  |
| ...    | ...        | ... |
| 282446 | 2012-09-21 | 21  |
| 282447 | 2012-09-28 | 28  |
| 282448 | 2012-10-02 | 2   |
| 282449 | 2012-10-08 | 8   |
| 282450 | 2012-11-05 | 5   |

282451 rows × 2 columns

Similary you can get month or year from date.

**How to get Month from a Date**

****

```
df['month'] = df['Date1'].dt.month
df[['Date1','month']]
```

Out\[29]:

|        | Date1      | month |
| ------ | ---------- | ----- |
| 0      | 2010-01-01 | 1     |
| 1      | 2010-03-07 | 3     |
| 2      | 2012-02-26 | 2     |
| 3      | 2011-03-12 | 3     |
| 4      | 2010-04-16 | 4     |
| ...    | ...        | ...   |
| 282446 | 2012-09-21 | 9     |
| 282447 | 2012-09-28 | 9     |
| 282448 | 2012-10-02 | 10    |
| 282449 | 2012-10-08 | 10    |
| 282450 | 2012-11-05 | 11    |

282451 rows × 2 columns

**How to get Year from a Date**

In \[30]:

```
df['year'] = df['Date1'].dt.year
df[['Date1','year']]
```

Out\[30]:

|        | Date1      | year |
| ------ | ---------- | ---- |
| 0      | 2010-01-01 | 2010 |
| 1      | 2010-03-07 | 2010 |
| 2      | 2012-02-26 | 2012 |
| 3      | 2011-03-12 | 2011 |
| 4      | 2010-04-16 | 2010 |
| ...    | ...        | ...  |
| 282446 | 2012-09-21 | 2012 |
| 282447 | 2012-09-28 | 2012 |
| 282448 | 2012-10-02 | 2012 |
| 282449 | 2012-10-08 | 2012 |
| 282450 | 2012-11-05 | 2012 |

282451 rows × 2 columns

**How to get Quarter from a Date**

Quarter is a 3 month period as first three months is consideres as first quarter while last three months is considered as fourth quarter, There are 4 quarters in a year.

In \[31]:

```
df['quarter'] = df['Date1'].dt.quarter
df[['Date1','quarter']]
```

Out\[31]:

|        | Date1      | quarter |
| ------ | ---------- | ------- |
| 0      | 2010-01-01 | 1       |
| 1      | 2010-03-07 | 1       |
| 2      | 2012-02-26 | 1       |
| 3      | 2011-03-12 | 1       |
| 4      | 2010-04-16 | 2       |
| ...    | ...        | ...     |
| 282446 | 2012-09-21 | 3       |
| 282447 | 2012-09-28 | 3       |
| 282448 | 2012-10-02 | 4       |
| 282449 | 2012-10-08 | 4       |
| 282450 | 2012-11-05 | 4       |

282451 rows × 2 columns

## A useful Example: <a href="#a-useful-example" id="a-useful-example"></a>

Quarters are a tricky thing to handle, as we all know that quarters can change country wise , like in India, First three months are 4th quarter while last three months are first quarter. So we need to apply a function when we are dealing with these kind of situations.

Now that we have got quarter columns , we can apply a function on it.

In \[32]:

```
def qc(q):
    if(q==1):
        return 4
    elif(q==2):
        return 1
    elif(q==3):
        return 2
    else:
        return 3
```

In \[33]:

```
df['india_quarter'] = df['quarter'].apply(qc)
df[['Date1','quarter','india_quarter']]
```

Out\[33]:

|        | Date1      | quarter | india\_quarter |
| ------ | ---------- | ------- | -------------- |
| 0      | 2010-01-01 | 1       | 4              |
| 1      | 2010-03-07 | 1       | 4              |
| 2      | 2012-02-26 | 1       | 4              |
| 3      | 2011-03-12 | 1       | 4              |
| 4      | 2010-04-16 | 2       | 1              |
| ...    | ...        | ...     | ...            |
| 282446 | 2012-09-21 | 3       | 2              |
| 282447 | 2012-09-28 | 3       | 2              |
| 282448 | 2012-10-02 | 4       | 3              |
| 282449 | 2012-10-08 | 4       | 3              |
| 282450 | 2012-11-05 | 4       | 3              |

282451 rows × 3 columns

**How to find month start from date**

_**Series.dt.is\_month\_start**_

It Indicates whether the date is the first day of the month. It returns boolean values.

In \[34]:

```
df['month start'] = df['Date1'].dt.is_month_start
df[['Date1','month start']]
```

Out\[34]:

|        | Date1      | month start |
| ------ | ---------- | ----------- |
| 0      | 2010-01-01 | True        |
| 1      | 2010-03-07 | False       |
| 2      | 2012-02-26 | False       |
| 3      | 2011-03-12 | False       |
| 4      | 2010-04-16 | False       |
| ...    | ...        | ...         |
| 282446 | 2012-09-21 | False       |
| 282447 | 2012-09-28 | False       |
| 282448 | 2012-10-02 | False       |
| 282449 | 2012-10-08 | False       |
| 282450 | 2012-11-05 | False       |

282451 rows × 2 columns

**How to find month end from date**

_**Series.dt.is\_month\_end**_

It Indicates whether the date is the last day of the month. It returns boolean values.

In \[35]:

```
df['month end'] = df['Date1'].dt.is_month_end
df[['Date1','month end']]
```

Out\[35]:

|        | Date1      | month end |
| ------ | ---------- | --------- |
| 0      | 2010-01-01 | False     |
| 1      | 2010-03-07 | False     |
| 2      | 2012-02-26 | False     |
| 3      | 2011-03-12 | False     |
| 4      | 2010-04-16 | False     |
| ...    | ...        | ...       |
| 282446 | 2012-09-21 | False     |
| 282447 | 2012-09-28 | False     |
| 282448 | 2012-10-02 | False     |
| 282449 | 2012-10-08 | False     |
| 282450 | 2012-11-05 | False     |

282451 rows × 2 columns

**How to find number of days in a month**

In \[41]:

```
df['daysinmonth'] = df['Date1'].dt.daysinmonth
df[['Date1','daysinmonth']]
```

Out\[41]:

|        | Date1      | daysinmonth |
| ------ | ---------- | ----------- |
| 0      | 2010-01-01 | 31          |
| 1      | 2010-03-07 | 31          |
| 2      | 2012-02-26 | 29          |
| 3      | 2011-03-12 | 31          |
| 4      | 2010-04-16 | 30          |
| ...    | ...        | ...         |
| 282446 | 2012-09-21 | 30          |
| 282447 | 2012-09-28 | 30          |
| 282448 | 2012-10-02 | 31          |
| 282449 | 2012-10-08 | 31          |
| 282450 | 2012-11-05 | 30          |

282451 rows × 2 columns

**How to find day name in a month**

In \[39]:

```
df['dayname'] = df['Date1'].dt.day_name()
df[['Date1','dayname']]
```

Out\[39]:

|        | Date1      | dayname  |
| ------ | ---------- | -------- |
| 0      | 2010-01-01 | Friday   |
| 1      | 2010-03-07 | Sunday   |
| 2      | 2012-02-26 | Sunday   |
| 3      | 2011-03-12 | Saturday |
| 4      | 2010-04-16 | Friday   |
| ...    | ...        | ...      |
| 282446 | 2012-09-21 | Friday   |
| 282447 | 2012-09-28 | Friday   |
| 282448 | 2012-10-02 | Tuesday  |
| 282449 | 2012-10-08 | Monday   |
| 282450 | 2012-11-05 | Monday   |

282451 rows × 2 columns

You can explore all kind of Series methods from [here](https://pandas.pydata.org/docs/reference/api/pandas.Series.dt.date.html)**.**

![](<.gitbook/assets/image (47).png>)

****
