# Sales Analysis Project



## <mark style="color:blue;">Project:</mark>

In this project, we are going to analyze 12 months of data of sales. We will learn how to clean, manage and analyze the dataset to find some meaningful information.

We start by cleaning our data. Tasks during this section include:

* [x] <mark style="color:purple;">**Drop NaN values from DataFrame**</mark>
* [x] <mark style="color:purple;">**Removing rows based on a condition**</mark>
* [x] <mark style="color:purple;">**Change the type of columns (to\_numeric, to\_datetime, astype)**</mark>

Once we have cleaned up our data a bit, we move the data exploration section. In this section we explore 5 high level business questions related to our data:

* [x] <mark style="color:purple;">**What was the best month for sales? How much was earned that month?**</mark>
* [x] <mark style="color:purple;">**What city sold the most product?**</mark>
* [x] <mark style="color:purple;">**What time should we display advertisemens to maximize the likelihood of customer’s buying product?**</mark>
* [x] <mark style="color:purple;">**What products are most often sold together?**</mark>
* [x] <mark style="color:purple;">**What product sold the most? Why do you think it sold the most?**</mark>

<mark style="color:purple;">****</mark>

## <mark style="color:green;">Download Dataset:</mark>

{% file src=".gitbook/assets/SalesData.zip" %}

Once you have downloaded the dataset , extract and save it somewhere.

## <mark style="color:green;">Import Necessary Libraries</mark>&#x20;

```python
import os
import pandas as pd
```

## <mark style="color:green;">Assign Path Variable to Path of Data</mark>

```python
base_path = r'C:\Users\abhis\Downloads\SalesData (1)'
```

## <mark style="color:green;">Merging 12 months of sales data in a single file:</mark> <a href="#merging-12-months-of-sales-data-in-a-single-file" id="merging-12-months-of-sales-data-in-a-single-file"></a>

To Calculate and analyze Company Sales Data, We must merge all 12 CSV files into one.

**Let us go through one-month data first , to know things better.**

```python
one_month = pd.read_csv(fr"{base_path}\Sales_April_2019.csv")
one_month.head(3)
```



| Order ID | Product                    | Quantity Ordered | Price Each | Order Date     | Purchase Address                     |
| -------- | -------------------------- | ---------------- | ---------- | -------------- | ------------------------------------ |
| 176558   | USB-C Charging Cable       | 2                | 11.95      | 04/19/19 08:46 | 917 1st St, Dallas, TX 75001         |
| 176559   | Bose SoundSport Headphones | 1                | 99.99      | 04/07/19 22:30 | 682 Chestnut St, Boston, MA 02215    |
| 176560   | Google Phone               | 1                | 600        | 04/12/19 14:38 | 669 Spruce St, Los Angeles, CA 90001 |

This is how our one month data looks like. Can we get all files from the directory ?&#x20;

## <mark style="color:green;">List all files from the directory</mark>

To get all files from a specific directory , we can use **listdir() method.**

```python
files = os.listdir(path)
files
```

Output :&#x20;

```python
['Sales_April_2019.csv',
 'Sales_August_2019.csv',
 'Sales_December_2019.csv',
 'Sales_February_2019.csv',
 'Sales_January_2019.csv',
 'Sales_July_2019.csv',
 'Sales_June_2019.csv',
 'Sales_March_2019.csv',
 'Sales_May_2019.csv',
 'Sales_November_2019.csv',
 'Sales_October_2019.csv',
 'Sales_September_2019.csv']
```

Now we need to concat all these file in a single file, for that we need to create an empty DataFrame and concat all sales file.

### Concatenate all files :&#x20;

```python
all_month_data = pd.DataFrame()  #Empty DataFrame

for file in files:    #Iteration In Sales Files
    monthly_data = pd.read_csv(fr"{path}\{file}")    #Read File
    all_month_data = pd.concat((all_month_data,monthly_data))  #Concatenate file
    
all_month_data
```

| Order ID | Product                    | Quantity Ordered | Price Each | Order Date     | Purchase Address                        |
| -------- | -------------------------- | ---------------- | ---------- | -------------- | --------------------------------------- |
| 176558   | USB-C Charging Cable       | 2                | 11.95      | 04/19/19 08:46 | 917 1st St, Dallas, TX 75001            |
| 176559   | Bose SoundSport Headphones | 1                | 99.99      | 04/07/19 22:30 | 682 Chestnut St, Boston, MA 02215       |
| 176560   | Google Phone               | 1                | 600        | 04/12/19 14:38 | 669 Spruce St, Los Angeles, CA 90001    |
| 176560   | Wired Headphones           | 1                | 11.99      | 04/12/19 14:38 | 669 Spruce St, Los Angeles, CA 90001    |
| 176561   | Wired Headphones           | 1                | 11.99      | 04/30/19 09:27 | 333 8th St, Los Angeles, CA 90001       |
| ...      | ...                        | ...              | ...        | ...            | ...                                     |
| 259353   | AAA Batteries (4-pack)     | 3                | 2.99       | 09/17/19 20:56 | 840 Highland St, Los Angeles, CA 90001  |
| 259354   | iPhone                     | 1                | 700        | 09/01/19 16:00 | 216 Dogwood St, San Francisco, CA 94016 |
| 259355   | iPhone                     | 1                | 700        | 09/23/19 07:39 | 220 12th St, San Francisco, CA 94016    |
| 259356   | 34in Ultrawide Monitor     | 1                | 379.99     | 09/19/19 17:30 | 511 Forest St, San Francisco, CA 94016  |
| 259357   | USB-C Charging Cable       | 1                | 11.95      | 09/30/19 00:18 | 250 Meadow St, San Francisco, CA 94016  |

186305 rows × 6 columns

Now that we have a DataFrame with all sales Files , let us convert it into a CSV File.

## <mark style="color:green;">Convert To CSV</mark>&#x20;

```python
all_month_data.to_csv(fr'{path}\{"Sales.csv"}',index=False)
```

Let us read out Data From Updated DataFrame.

### Read From Updated DataFrame

```python
all_data = pd.read_csv(fr'{path}\{"Sales.csv"}')
all_data.head()
```



| Order ID | Product                    | Quantity Ordered | Price Each | Order Date       | Purchase Address                     |
| -------- | -------------------------- | ---------------- | ---------- | ---------------- | ------------------------------------ |
| 176558   | USB-C Charging Cable       | 2                | 11.95      | 04/19/19 08:46   | 917 1st St, Dallas, TX 75001         |
| 176559   | Bose SoundSport Headphones | 1                | 99.99      | 04-07-2019 22:30 | 682 Chestnut St, Boston, MA 02215    |
| 176560   | Google Phone               | 1                | 600        | 04-12-2019 14:38 | 669 Spruce St, Los Angeles, CA 90001 |
| 176560   | Wired Headphones           | 1                | 11.99      | 04-12-2019 14:38 | 669 Spruce St, Los Angeles, CA 90001 |
| 176561   | Wired Headphones           | 1                | 11.99      | 04/30/19 09:27   | 333 8th St, Los Angeles, CA 90001    |

## <mark style="color:green;">Augment Data With Additional Columns</mark>

### Clean up the data :&#x20;

The first step in this is figuring out what we need to clean. I have found in practice, that you find things you need to clean as you perform operations and get errors. Based on the error, you decide how you should go about cleaning the data.

**Display All rows of NAN:**&#x20;

```python
all_data[all_data.isna().any(axis=1)]
```

###

### Convert Order Date in Datetime

To convert Order Date in Datetime, first thing that needs to be done is to bring all date in a single format.

<pre class="language-python"><code class="lang-python">all_data['Order Date'] = all_data['Order Date'].str.replace('/','-')
<strong>all_data['Order Date'] = pd.to_datetime(all_data['Order Date'])</strong></code></pre>

#### Output :&#x20;

```python
File "C:\Users\abhis\.virtualenvs\python\lib\site-packages\dateutil\parser\_parser.py", line 643, in parse
    raise ParserError("Unknown string format: %s", timestr)
dateutil.parser._parser.ParserError: Unknown string format: Order Date
```

{% hint style="danger" %}
**Reason Behind Error :**&#x20;

**---> There is some unknown string named as `'Order Date' in our Dataset.`**
{% endhint %}

Let us see where this `'Order Date'` is by using conditional formatting.

```python
temp = all_data.loc[all_data['Order Date'] == 'Order Date']
temp
```

| <p><br>Order ID</p> | Product  | Quantity Ordered | Price Each       | Order Date | Purchase Address |                  |
| ------------------- | -------- | ---------------- | ---------------- | ---------- | ---------------- | ---------------- |
| 517                 | Order ID | Product          | Quantity Ordered | Price Each | Order Date       | Purchase Address |
| 1146                | Order ID | Product          | Quantity Ordered | Price Each | Order Date       | Purchase Address |
| 1152                | Order ID | Product          | Quantity Ordered | Price Each | Order Date       | Purchase Address |
| 2869                | Order ID | Product          | Quantity Ordered | Price Each | Order Date       | Purchase Address |
| 2884                | Order ID | Product          | Quantity Ordered | Price Each | Order Date       | Purchase Address |
| ...                 | ...      | ...              | ...              | ...        | ...              | ...              |
| 2234519             | Order ID | Product          | Quantity Ordered | Price Each | Order Date       | Purchase Address |
| 2234906             | Order ID | Product          | Quantity Ordered | Price Each | Order Date       | Purchase Address |
| 2235918             | Order ID | Product          | Quantity Ordered | Price Each | Order Date       | Purchase Address |
| 2235987             | Order ID | Product          | Quantity Ordered | Price Each | Order Date       | Purchase Address |
| 2236093             | Order ID | Product          | Quantity Ordered | Price Each | Order Date       | Purchase Address |

4260 rows × 6 columns

Let us remove all these 4260 rows from our Dataframe.

```python
all_data = all_data.loc[all_data['Order Date']!='Order Date']
all_data.head()
```

Now let us try to convert Order Date again.&#x20;

```python
all_data['Order Date'] = all_data['Order Date'].str.replace('/','-')
all_data['Order Date'] = pd.to_datetime(all_data['Order Date'])
```

### **Add Month Column:**

To add month column , all we need to do is to use date time methods.

```python
all_data['Month'] = all_data['Order Date'].dt.month_name()
all_data['Month']
```

**Output:**

```python
0              April
1              April
2              April
3              April
4              April
             ...    
4285010    September
4285011    September
4285012    September
4285013    September
4285014    September
Name: Month, Length: 4276850, dtype: object
```

### <mark style="color:green;">**What was the best month for sales? How much was earned that month?**</mark>

In Our DataFrame , There are Two columns _**Price Each**_ and _**Quantity Ordered.**_ But we do not have Total Sale Value (TSV), We should also add a calculated column Total Sale Value. Let's do it first.

Now _**Price Each , Quantity Ordered**_ is object data type , so we need to convert it.

**Convert Price Each and Quantity Ordered in Float and Calculate TSV.**

```python
#Conversion To Float
all_data['Quantity Ordered'] = all_data['Quantity Ordered'].astype('float')
all_data['Price Each'] = all_data['Price Each'].astype('float')

#Calculated Column
all_data['TSV'] = all_data['Quantity Ordered'] * all_data['Price Each']
all_data.head()
```

Now we can easily use **groupby** method to find maximum sales value.

```python
all_data.groupby('month')['TSV'].sum()
```

```python
month
1     3644513.46
2     4404044.84
3     5614200.76
4     6781340.48
5     6305213.50
6     5155604.52
7     5295551.52
8     4488935.76
9     4195120.26
10    7473453.76
11    6399206.40
12    9226886.68
Name: TSV, dtype: float64
```

### <mark style="color:purple;">Best Month For Sales : December</mark>

### <mark style="color:purple;">Total Sale Value In December : 9226886.68</mark>

### Plot the Data:&#x20;

```python
months = range(1,13)
plt.bar(months,results)
plt.xticks(months)
plt.xlabel('Month')
plt.ylabel('Sales')
plt.show()
```

<figure><img src=".gitbook/assets/image (45).png" alt=""><figcaption></figcaption></figure>

December is a Festival Month , the biggest thing is December is Christmas, So people spend money and maybe that is the reason for december is best month for sales.

### <mark style="color:green;">**What city sold the most product?**</mark>

There is no City Column in our Dataset, But you can see Purchase Address ,where City is mentioned in middle, we can use Purchase address and create a City Column.

```python
all_data['City'] = all_data['Purchase Address'].str.split(',',expand=True)[1]
all_data
```

<figure><img src=".gitbook/assets/image (51).png" alt=""><figcaption></figcaption></figure>

Now we can groupby City and Calculate Total Quantity Ordered.

```python
all_data.groupby('City')['Quantity Ordered'].sum().sort_values()
```

**Output :**&#x20;

```python
City
 Austin            22306.0
 Portland          28106.0
 Seattle           33106.0
 Atlanta           33204.0
 Dallas            33460.0
 Boston            45056.0
 New York City     55864.0
 Los Angeles       66578.0
 San Francisco    100478.0
Name: Quantity Ordered, dtype: float64
```

### <mark style="color:purple;">City Sold Most Product : San Francisco</mark>

### Plot the Data:

```python
import matplotlib.pyplot as plt

keys = [city for city, df in all_data.groupby(['City'])]

plt.bar(keys,all_data.groupby(['City']).sum()['TSV'])
plt.ylabel('Sales in USD ($)')
plt.xlabel('Month number')
plt.xticks(keys, rotation='vertical', size=8)
plt.show()
```

<figure><img src=".gitbook/assets/image (72).png" alt=""><figcaption></figcaption></figure>

### <mark style="color:green;">**What time should we display advertisements to maximize the likelihood of customer’s buying product?**</mark>

Because we need to work on time, let's create **Hour** and **Minute** Column.

```python
all_data['Hour'] = all_data['Order Date'].dt.hour
all_data['Minute'] = all_data['Order Date'].dt.minute
all_data.head()
```

<figure><img src=".gitbook/assets/image (30).png" alt=""><figcaption></figcaption></figure>

Let us see what time most people bought from this Company .&#x20;

```python
all_data.groupby('Hour')['TSV'].sum().sort_values(ascending=False)
```

```python
Hour
19    4825877.08
12    4633642.68
11    4601220.48
20    4563432.48
18    4438696.60
13    4310779.60
17    4258723.22
14    4167345.46
21    4084001.72
10    3888573.54
15    3883099.20
16    3809202.62
9     3278061.16
22    3215098.42
8     2384697.94
23    2358608.88
7     1489708.24
0     1427442.54
1      921733.76
6      896226.00
2      469702.88
5      461359.64
4      325322.02
3      291515.78
Name: TSV, dtype: float64
```

### Plot the Data :&#x20;

```
keys = [pair for pair, df in all_data.groupby(['Hour'])]

plt.plot(keys, all_data.groupby(['Hour']).count())
plt.xticks(keys)
plt.grid()
plt.show()
```

<figure><img src=".gitbook/assets/image (115).png" alt=""><figcaption></figcaption></figure>

### <mark style="color:green;">What Products are most often sold together ?</mark>&#x20;

This is going to be a tricky business. Before diving into the problem, let us understand the problem.&#x20;

What Products are most often sold together gives a very important insight that helps company lure customers into spending more and generate more profit.

You must have seen Amazon's **Customer Who Bought this item also bought this Item.** We are going to do something like this.

Let's try to solve this problem Step by step :&#x20;

#### Duplicate Order ID :&#x20;

Same Order ID for different products suggests customer bought different products Together in Our Data. Let us look for Duplicate OrderId Products: ****&#x20;

```python
# All Duplicate Order ID 
df = all_data[all_data['Order ID'].duplicated(keep=False)]
df
```

<figure><img src=".gitbook/assets/image (36).png" alt=""><figcaption></figcaption></figure>

#### Group Different Products With Same Order ID :&#x20;

Let's create a new column that contains different Products with the same Order ID. We can do this with the help of transform method.

```python
df['Grouped'] = df.groupby('Order ID')['Product'].transform(lambda x : ','.join(x))
df.head(10)
```

<figure><img src=".gitbook/assets/image (97).png" alt=""><figcaption></figcaption></figure>

{% embed url="https://stackoverflow.com/questions/52195887/counting-unique-pairs-of-numbers-into-a-python-dictionary" %}

```
from itertools import combinations
from collections import Counter

count = Counter()
row_list = []
for row in df['Grouped']:
    row_list = row.split(',')
    count.update(Counter(combinations(row_list, 3)))

count.most_common(10)
```

Output :&#x20;

```
[(('Google Phone', 'USB-C Charging Cable', 'Wired Headphones'), 86),
 (('iPhone', 'Lightning Charging Cable', 'Wired Headphones'), 62),
 (('iPhone', 'Lightning Charging Cable', 'Apple Airpods Headphones'), 47),
 (('Google Phone', 'USB-C Charging Cable', 'Bose SoundSport Headphones'), 35),
 (('Vareebadd Phone', 'USB-C Charging Cable', 'Wired Headphones'), 33),
 (('iPhone', 'Apple Airpods Headphones', 'Wired Headphones'), 27),
 (('Google Phone', 'Bose SoundSport Headphones', 'Wired Headphones'), 24),
 (('Vareebadd Phone', 'USB-C Charging Cable', 'Bose SoundSport Headphones'),
  16),
 (('USB-C Charging Cable', 'Bose SoundSport Headphones', 'Wired Headphones'),
  5),
 (('Vareebadd Phone', 'Bose SoundSport Headphones', 'Wired Headphones'), 5)]
```

### <mark style="color:green;">**What product sold the most? Why do you think it sold the most?**</mark>

This is pretty simple , we will group all product and calculate quantity ordered.

```python
all_data.groupby('Product')['Quantity Ordered'].sum().sort_values().plot(kind='bar')
```

<figure><img src=".gitbook/assets/image (71).png" alt=""><figcaption></figcaption></figure>
