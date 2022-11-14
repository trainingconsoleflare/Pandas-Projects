---
description: >-
  pandas is a fast, powerful, flexible and easy-to-use open source data analysis
  and manipulation tool, built on top of the Python programming language.
---

# Introduction To Pandas

![](<.gitbook/assets/image (60).png>)

## What is Pandas ? <a href="#what-is-pandas" id="what-is-pandas"></a>

pandas is a **fast, powerful, flexible and easy to use** open source **data analysis and manipulation tool**, built on top of the Python programming language.

In more simpler terms , pandas is a software library written for the Python programming language for data manipulation and analysis. In particular, it offers data structures and operations for manipulating numerical tables and time series.

### Installing Pandas <a href="#installing-pandas" id="installing-pandas"></a>

Let's Install Pandas by using pip package manager :&#x20;

{% hint style="success" %}
1. **Open your terminal in Pycharm**

&#x20; **2.  Write : `pip install pandas`**
{% endhint %}

## Read CSV and Text files Through Pandas <a href="#read-csv-and-text-files-through-pandas" id="read-csv-and-text-files-through-pandas"></a>

In \[ ]:

```
import pandas as pd
df = pd.read_csv('Pokemon.csv')
print(df)
```

### Result: <a href="#result" id="result"></a>

![](<.gitbook/assets/image (27).png>)



## Read Top few rows or Bottom few: <a href="#read-top-few-rows-or-bottom-few" id="read-top-few-rows-or-bottom-few"></a>

### head() Function : <a href="#head-function" id="head-function"></a>

The head() function is used to get the first or last n rows.This function returns the first n rows for the object based on position. It is useful for quickly testing if your object has the right type of data in it.

In \[ ]:

```
print(df.head(5))    #Top 5 Rows
```

![](<.gitbook/assets/image (6).png>)



```
print(df.head(-5))    #Last 5 Rows
```

![](<.gitbook/assets/image (15).png>)



## Load Data Without Header <a href="#load-data-without-header" id="load-data-without-header"></a>

In \[ ]:

```
head=["#","Name","Type 1","Type 2","HP","Attack","Defense","Sp. Atk","Sp. Def","Speed","Generation","Legendary"]

df = pd.read_csv(r"Pokemon.csv",names=head)

print(df)
```

![](<.gitbook/assets/image (99).png>)



## To Read Data Separated by any delimiter : <a href="#to-read-data-separated-by-any-delimiter" id="to-read-data-separated-by-any-delimiter"></a>

In \[ ]:

```
df = pd.read_csv('Pokemon.csv', delimiter=',')

print(df.head(5))
```



## To work on Specific Column: <a href="#to-work-on-specific-column" id="to-work-on-specific-column"></a>

Say , We want to work on HP Column.

In \[ ]:

```
col = df['HP']
print(col)
```

![](<.gitbook/assets/image (94).png>)



## To work on more than one columns: <a href="#to-work-on-more-than-one-columns" id="to-work-on-more-than-one-columns"></a>

In \[ ]:

```
cols = df[['Name', 'Type 1', 'HP']]
print(cols)
```

![](<.gitbook/assets/image (54).png>)



## To Read Headers: <a href="#to-read-headers" id="to-read-headers"></a>

In \[ ]:

```
df.columns
```

![](<.gitbook/assets/image (43).png>)



## To get the Data Types Of Columns: <a href="#to-get-the-data-types-of-columns" id="to-get-the-data-types-of-columns"></a>

To get the data types of columns , you need to use dtype attribute.

In \[ ]:

```
df.dtypes
```

![](<.gitbook/assets/image (107).png>)



## Statistical Describing Data <a href="#statistical-describing-data" id="statistical-describing-data"></a>

The Describe function returns the **statistical summary of the dataframe or series**. This includes **Count, Mean, Median (or 50th percentile) standard variation, min-max, and percentile values of columns**.

In \[19]:

```
df.describe()
```





| #     | Total      | HP        | Attack     | Defense    | Sp. Atk    | Sp. Def    | Speed      | Generation |           |
| ----- | ---------- | --------- | ---------- | ---------- | ---------- | ---------- | ---------- | ---------- | --------- |
| count | 800.000000 | 800.00000 | 800.000000 | 800.000000 | 800.000000 | 800.000000 | 800.000000 | 800.000000 | 800.00000 |
| mean  | 362.813750 | 435.10250 | 69.258750  | 79.001250  | 73.842500  | 72.820000  | 71.902500  | 68.277500  | 3.32375   |
| std   | 208.343798 | 119.96304 | 25.534669  | 32.457366  | 31.183501  | 32.722294  | 27.828916  | 29.060474  | 1.66129   |
| min   | 1.000000   | 180.00000 | 1.000000   | 5.000000   | 5.000000   | 10.000000  | 20.000000  | 5.000000   | 1.00000   |
| 25%   | 184.750000 | 330.00000 | 50.000000  | 55.000000  | 50.000000  | 49.750000  | 50.000000  | 45.000000  | 2.00000   |
| 50%   | 364.500000 | 450.00000 | 65.000000  | 75.000000  | 70.000000  | 65.000000  | 70.000000  | 65.000000  | 3.00000   |
| 75%   | 539.250000 | 515.00000 | 80.000000  | 100.000000 | 90.000000  | 95.000000  | 90.000000  | 90.000000  | 5.00000   |
| max   | 721.000000 | 780.00000 | 255.000000 | 190.000000 | 230.000000 | 194.000000 | 230.000000 | 180.000000 | 6.00000   |

## Slicing Pandas Data frame using DataFrame.iloc\[] <a href="#slicing-pandas-data-frame-using-dataframe.iloc-5b-5d" id="slicing-pandas-data-frame-using-dataframe.iloc-5b-5d"></a>

We can perform slicing on columns as well as rows on pandas Dataframe.

#### Syntax For Slicing: <a href="#syntax-for-slicing" id="syntax-for-slicing"></a>

**`df.iloc[rows,columns]`**

### Slicing For Rows : <a href="#slicing-for-rows" id="slicing-for-rows"></a>

Say We want to slice Top 4 rows with all columns , We will slice it in the same way as we learned it in Numpy.



```
df.iloc[0:4,:]
```



| # | Name | Type 1                | Type 2 | Total  | HP  | Attack | Defense | Sp. Atk | Sp. Def | Speed | Generation | Legendary |       |
| - | ---- | --------------------- | ------ | ------ | --- | ------ | ------- | ------- | ------- | ----- | ---------- | --------- | ----- |
| 0 | 1    | Bulbasaur             | Grass  | Poison | 318 | 45     | 49      | 49      | 65      | 65    | 45         | 1         | False |
| 1 | 2    | Ivysaur               | Grass  | Poison | 405 | 60     | 62      | 63      | 80      | 80    | 60         | 1         | False |
| 2 | 3    | Venusaur              | Grass  | Poison | 525 | 80     | 82      | 83      | 100     | 100   | 80         | 1         | False |
| 3 | 3    | VenusaurMega Venusaur | Grass  | Poison | 625 | 80     | 100     | 123     | 122     | 120   | 80         | 1         | False |



### Slicing For Columns : <a href="#slicing-for-columns" id="slicing-for-columns"></a>

Say We want to slice 4 Columns from start with all rows , We will do it something like this.

In \[21]:

```
df.iloc[:,0:4]
```

| #   | Name | Type 1                | Type 2  |        |
| --- | ---- | --------------------- | ------- | ------ |
| 0   | 1    | Bulbasaur             | Grass   | Poison |
| 1   | 2    | Ivysaur               | Grass   | Poison |
| 2   | 3    | Venusaur              | Grass   | Poison |
| 3   | 3    | VenusaurMega Venusaur | Grass   | Poison |
| 4   | 4    | Charmander            | Fire    | NaN    |
| ... | ...  | ...                   | ...     | ...    |
| 795 | 719  | Diancie               | Rock    | Fairy  |
| 796 | 719  | DiancieMega Diancie   | Rock    | Fairy  |
| 797 | 720  | HoopaHoopa Confined   | Psychic | Ghost  |
| 798 | 720  | HoopaHoopa Unbound    | Psychic | Dark   |
| 799 | 721  | Volcanion             | Fire    | Water  |

800 rows × 4 columns



## Performing **Iteration** In DataFrame : <a href="#performing-iteration-in-dataframe" id="performing-iteration-in-dataframe"></a>

In this topic, we will learn to iterate over :

1.Rows\
2.Columns\


### Iteration Over Rows Using **iterrows()** Function :   <a href="#iteration-over-rows-using-iterrows-function" id="iteration-over-rows-using-iterrows-function"></a>

You can iterate over rows with the help of `iterrows().`It gives you a tuple of index and whole row. Say i want index and only name from the row, We will write it something like this:

In \[ ]:

```
for index, row in df.iterrows():
    print(index, row['Name'])
```

![](<.gitbook/assets/image (58).png>)



### Iteration Over Columns Using **iteritems()** Function : <a href="#iteration-over-columns-using-iteritems-function" id="iteration-over-columns-using-iteritems-function"></a>

In \[25]:

```
for (colname,colval) in df.iteritems():
    print(colname)
```



```
#
Name
Type 1
Type 2
Total
HP
Attack
Defense
Sp. Atk
Sp. Def
Speed
Generation
Legendary
```



## Filtering Data in Pandas DataFrame Using loc\[] : <a href="#filtering-data-in-pandas-dataframe-using-loc-5b-5d" id="filtering-data-in-pandas-dataframe-using-loc-5b-5d"></a>

Selecting all the rows from the given Dataframe in which **Type1** is **Grass** using loc\[ ].

In \[26]:

```
df.loc[df['Type 1'] == "Grass"]
```

| <p><br>#</p> | Name | Type 1                | Type 2 | Total    | HP  | Attack | Defense | Sp. Atk | Sp. Def | Speed | Generation | Legendary |       |
| ------------ | ---- | --------------------- | ------ | -------- | --- | ------ | ------- | ------- | ------- | ----- | ---------- | --------- | ----- |
| 0            | 1    | Bulbasaur             | Grass  | Poison   | 318 | 45     | 49      | 49      | 65      | 65    | 45         | 1         | False |
| 1            | 2    | Ivysaur               | Grass  | Poison   | 405 | 60     | 62      | 63      | 80      | 80    | 60         | 1         | False |
| 2            | 3    | Venusaur              | Grass  | Poison   | 525 | 80     | 82      | 83      | 100     | 100   | 80         | 1         | False |
| 3            | 3    | VenusaurMega Venusaur | Grass  | Poison   | 625 | 80     | 100     | 123     | 122     | 120   | 80         | 1         | False |
| 48           | 43   | Oddish                | Grass  | Poison   | 320 | 45     | 50      | 55      | 75      | 65    | 30         | 1         | False |
| ...          | ...  | ...                   | ...    | ...      | ... | ...    | ...     | ...     | ...     | ...   | ...        | ...       | ...   |
| 718          | 650  | Chespin               | Grass  | NaN      | 313 | 56     | 61      | 65      | 48      | 45    | 38         | 6         | False |
| 719          | 651  | Quilladin             | Grass  | NaN      | 405 | 61     | 78      | 95      | 56      | 58    | 57         | 6         | False |
| 720          | 652  | Chesnaught            | Grass  | Fighting | 530 | 88     | 107     | 122     | 74      | 75    | 64         | 6         | False |
| 740          | 672  | Skiddo                | Grass  | NaN      | 350 | 66     | 65      | 48      | 62      | 57    | 52         | 6         | False |
| 741          | 673  | Gogoat                | Grass  | NaN      | 531 | 123    | 100     | 62      | 97      | 81    | 68         | 6         | False |

70 rows × 13 columns

## Sorting of Data in DataFrame Using sort.values() Function : <a href="#sorting-of-data-in-dataframe-using-sort.values-function" id="sorting-of-data-in-dataframe-using-sort.values-function"></a>

### Sort in Ascending Order <a href="#sort-in-ascending-order" id="sort-in-ascending-order"></a>

You can use sort.values() function to sort data in ascending or descending order.For Example, We want to sort **Type1** in Ascending Order.

In \[35]:

```
df.sort_values(['Type 1'])
```

Out\[35]:

|     | #   | Name     | Type 1 | Type 2   | Total | HP  | Attack | Defense | Sp. Atk | Sp. Def | Speed | Generation | Legendary |
| --- | --- | -------- | ------ | -------- | ----- | --- | ------ | ------- | ------- | ------- | ----- | ---------- | --------- |
| 600 | 540 | Sewaddle | Bug    | Grass    | 310   | 45  | 53     | 70      | 40      | 60      | 42    | 5          | False     |
| 136 | 127 | Pinsir   | Bug    | NaN      | 500   | 65  | 125    | 100     | 55      | 70      | 85    | 1          | False     |
| 457 | 412 | Burmy    | Bug    | NaN      | 224   | 40  | 29     | 45      | 29      | 45      | 36    | 4          | False     |
| 132 | 123 | Scyther  | Bug    | Flying   | 500   | 70  | 110    | 80      | 55      | 80      | 105   | 1          | False     |
| 656 | 595 | Joltik   | Bug    | Electric | 319   | 50  | 47     | 50      | 57      | 50      | 65    | 5          | False     |
| ... | ... | ...      | ...    | ...      | ...   | ... | ...    | ...     | ...     | ...     | ...   | ...        | ...       |
| 172 | 158 | Totodile | Water  | NaN      | 314   | 50  | 65     | 64      | 44      | 48      | 43    | 2          | False     |
| 610 | 550 | Basculin | Water  | NaN      | 460   | 70  | 92     | 65      | 80      | 55      | 98    | 5          | False     |
| 145 | 134 | Vaporeon | Water  | NaN      | 525   | 130 | 65     | 60      | 110     | 95      | 65    | 1          | False     |
| 574 | 515 | Panpour  | Water  | NaN      | 316   | 50  | 53     | 48      | 53      | 48      | 64    | 5          | False     |
| 184 | 170 | Chinchou | Water  | Electric | 330   | 75  | 38     | 38      | 56      | 56      | 67    | 2          | False     |

800 rows × 13 columns

### Sort in Descending Order <a href="#sort-in-descending-order" id="sort-in-descending-order"></a>

By using **ascending=False** parameter, You can Sort Data in Descending Order.

In \[36]:

```
df.sort_values(['Type 1'],ascending=False)
```

Out\[36]:

|     | #   | Name     | Type 1 | Type 2 | Total | HP  | Attack | Defense | Sp. Atk | Sp. Def | Speed | Generation | Legendary |
| --- | --- | -------- | ------ | ------ | ----- | --- | ------ | ------- | ------- | ------- | ----- | ---------- | --------- |
| 371 | 339 | Barboach | Water  | Ground | 288   | 50  | 48     | 43      | 46      | 41      | 60    | 3          | False     |
| 97  | 90  | Shellder | Water  | NaN    | 305   | 30  | 65     | 100     | 45      | 25      | 40    | 1          | False     |
| 240 | 222 | Corsola  | Water  | Rock   | 380   | 55  | 55     | 85      | 65      | 85      | 35    | 2          | False     |
| 403 | 368 | Gorebyss | Water  | NaN    | 485   | 55  | 84     | 105     | 114     | 75      | 52    | 3          | False     |
| 93  | 86  | Seel     | Water  | NaN    | 325   | 65  | 45     | 55      | 45      | 70      | 45    | 1          | False     |
| ... | ... | ...      | ...    | ...    | ...   | ... | ...    | ...     | ...     | ...     | ...   | ...        | ...       |
| 54  | 49  | Venomoth | Bug    | Poison | 450   | 70  | 65     | 60      | 90      | 75      | 90    | 1          | False     |
| 208 | 193 | Yanma    | Bug    | Flying | 390   | 65  | 65     | 45      | 75      | 45      | 95    | 2          | False     |
| 182 | 168 | Ariados  | Bug    | Poison | 390   | 70  | 90     | 70      | 60      | 60      | 40    | 2          | False     |
| 734 | 666 | Vivillon | Bug    | Flying | 411   | 80  | 52     | 50      | 90      | 50      | 89    | 6          | False     |
| 179 | 165 | Ledyba   | Bug    | Flying | 265   | 40  | 20     | 30      | 40      | 80      | 55    | 2          | False     |

800 rows × 13 columns

## Sorting of Multiple Columns in different order using sort.values(): <a href="#sorting-of-multiple-columns-in-different-order-using-sort.values" id="sorting-of-multiple-columns-in-different-order-using-sort.values"></a>

In \[37]:

```
df.sort_values(['Type 1','Type 2','Total','HP'],ascending=[True,False,True,False])
```

Out\[37]:

|     | #   | Name                    | Type 1 | Type 2 | Total | HP  | Attack | Defense | Sp. Atk | Sp. Def | Speed | Generation | Legendary |
| --- | --- | ----------------------- | ------ | ------ | ----- | --- | ------ | ------- | ------- | ------- | ----- | ---------- | --------- |
| 307 | 283 | Surskit                 | Bug    | Water  | 269   | 40  | 30     | 32      | 50      | 52      | 65    | 3          | False     |
| 460 | 413 | WormadamTrash Cloak     | Bug    | Steel  | 424   | 60  | 69     | 95      | 69      | 95      | 36    | 4          | False     |
| 220 | 205 | Forretress              | Bug    | Steel  | 465   | 75  | 90     | 140     | 60      | 60      | 40    | 2          | False     |
| 693 | 632 | Durant                  | Bug    | Steel  | 484   | 58  | 109    | 112     | 48      | 48      | 109   | 5          | False     |
| 650 | 589 | Escavalier              | Bug    | Steel  | 495   | 70  | 135    | 105     | 60      | 105     | 20    | 5          | False     |
| ... | ... | ...                     | ...    | ...    | ...   | ... | ...    | ...     | ...     | ...     | ...   | ...        | ...       |
| 264 | 245 | Suicune                 | Water  | NaN    | 580   | 100 | 75     | 115     | 90      | 115     | 85    | 2          | True      |
| 548 | 490 | Manaphy                 | Water  | NaN    | 600   | 100 | 100    | 100     | 100     | 100     | 100   | 4          | False     |
| 12  | 9   | BlastoiseMega Blastoise | Water  | NaN    | 630   | 79  | 103    | 120     | 135     | 115     | 78    | 1          | False     |
| 421 | 382 | Kyogre                  | Water  | NaN    | 670   | 100 | 100    | 90      | 150     | 140     | 90    | 3          | True      |
| 422 | 382 | KyogrePrimal Kyogre     | Water  | NaN    | 770   | 100 | 150    | 90      | 180     | 160     | 90    | 3          | True      |

800 rows × 13 columns

***

{% hint style="info" %}
As you can see, We have sorted multiple columns in different order. **Type 1** and **Total** is in Ascending order , while **Type 2** and **HP** is in Descending Order.

\
You can also use 1 and 0 instead of True and False.

`df.sort_values(['Type 1','Type 2','Total','HP'],ascending=[1,0,1,0])`

Result will be same.
{% endhint %}

***

## How to Create New Column in DataFrame Using Old Ones: <a href="#how-to-create-new-column-in-dataframe-using-old-ones" id="how-to-create-new-column-in-dataframe-using-old-ones"></a>

Say , We want to create a new Column named **total\_sum** , that is addition of **HP,Attack,Defense,Sp.atk,Sp.def,Speed,Generation**.

In \[44]:

```
df['total_sum'] = df['Attack'] + df['Defense'] + df['Sp. Atk'] + df['Sp. Def'] + df['Speed']
df['total_sum']
```

Out\[44]:

```
0      273
1      345
2      445
3      545
4      270
      ... 
795    550
796    650
797    520
798    600
799    520
Name: total_sum, Length: 800, dtype: int64
```

We can also use **sum()** function to achieve same column , for Example :

In \[55]:

```
df['total_s'] = df.iloc[:,6:11].sum(axis=1)
df['total_s']
```

Out\[55]:

```
0      273
1      345
2      445
3      545
4      270
      ... 
795    550
796    650
797    520
798    600
799    520
Name: total_s, Length: 800, dtype: int64
```

***

**NOTE**

If i See my dataframe, it will add both columns. Let's see.

In \[56]:

```
df
```

Out\[56]:

|     | #   | Name                  | Type 1  | Type 2 | Total | HP  | Attack | Defense | Sp. Atk | Sp. Def | Speed | Generation | Legendary | T   | total\_sum | total\_s |
| --- | --- | --------------------- | ------- | ------ | ----- | --- | ------ | ------- | ------- | ------- | ----- | ---------- | --------- | --- | ---------- | -------- |
| 0   | 1   | Bulbasaur             | Grass   | Poison | 273   | 45  | 49     | 49      | 65      | 65      | 45    | 1          | False     | 273 | 273        | 273      |
| 1   | 2   | Ivysaur               | Grass   | Poison | 345   | 60  | 62     | 63      | 80      | 80      | 60    | 1          | False     | 345 | 345        | 345      |
| 2   | 3   | Venusaur              | Grass   | Poison | 445   | 80  | 82     | 83      | 100     | 100     | 80    | 1          | False     | 445 | 445        | 445      |
| 3   | 3   | VenusaurMega Venusaur | Grass   | Poison | 545   | 80  | 100    | 123     | 122     | 120     | 80    | 1          | False     | 545 | 545        | 545      |
| 4   | 4   | Charmander            | Fire    | NaN    | 270   | 39  | 52     | 43      | 60      | 50      | 65    | 1          | False     | 270 | 270        | 270      |
| ... | ... | ...                   | ...     | ...    | ...   | ... | ...    | ...     | ...     | ...     | ...   | ...        | ...       | ... | ...        | ...      |
| 795 | 719 | Diancie               | Rock    | Fairy  | 550   | 50  | 100    | 150     | 100     | 150     | 50    | 6          | True      | 550 | 550        | 550      |
| 796 | 719 | DiancieMega Diancie   | Rock    | Fairy  | 650   | 50  | 160    | 110     | 160     | 110     | 110   | 6          | True      | 650 | 650        | 650      |
| 797 | 720 | HoopaHoopa Confined   | Psychic | Ghost  | 520   | 80  | 110    | 60      | 150     | 130     | 70    | 6          | True      | 520 | 520        | 520      |
| 798 | 720 | HoopaHoopa Unbound    | Psychic | Dark   | 600   | 80  | 160    | 60      | 170     | 130     | 80    | 6          | True      | 600 | 600        | 600      |
| 799 | 721 | Volcanion             | Fire    | Water  | 520   | 80  | 110    | 120     | 130     | 90      | 70    | 6          | True      | 520 | 520        | 520      |

800 rows × 16 columns

## How to change Columns Positions : <a href="#how-to-change-columns-positions" id="how-to-change-columns-positions"></a>

In \[59]:

```
df=df[['#','Legendary', 'Generation', 'Speed', 'Sp.Def', 'Sp.Atk', 'Defense', 'Attack',
       'HP', 'Type 2', 'Type 1', 'Name']]
df
```

Out\[59]:

|     | #   | Name                  | Type 1  | Type 2 | HP  | Attack | Defense | Sp. Atk | Sp. Def | Speed | Generation | Legendary |
| --- | --- | --------------------- | ------- | ------ | --- | ------ | ------- | ------- | ------- | ----- | ---------- | --------- |
| 0   | 1   | Bulbasaur             | Grass   | Poison | 45  | 49     | 49      | 65      | 65      | 45    | 1          | False     |
| 1   | 2   | Ivysaur               | Grass   | Poison | 60  | 62     | 63      | 80      | 80      | 60    | 1          | False     |
| 2   | 3   | Venusaur              | Grass   | Poison | 80  | 82     | 83      | 100     | 100     | 80    | 1          | False     |
| 3   | 3   | VenusaurMega Venusaur | Grass   | Poison | 80  | 100    | 123     | 122     | 120     | 80    | 1          | False     |
| 4   | 4   | Charmander            | Fire    | NaN    | 39  | 52     | 43      | 60      | 50      | 65    | 1          | False     |
| ... | ... | ...                   | ...     | ...    | ... | ...    | ...     | ...     | ...     | ...   | ...        | ...       |
| 795 | 719 | Diancie               | Rock    | Fairy  | 50  | 100    | 150     | 100     | 150     | 50    | 6          | True      |
| 796 | 719 | DiancieMega Diancie   | Rock    | Fairy  | 50  | 160    | 110     | 160     | 110     | 110   | 6          | True      |
| 797 | 720 | HoopaHoopa Confined   | Psychic | Ghost  | 80  | 110    | 60      | 150     | 130     | 70    | 6          | True      |
| 798 | 720 | HoopaHoopa Unbound    | Psychic | Dark   | 80  | 160    | 60      | 170     | 130     | 80    | 6          | True      |
| 799 | 721 | Volcanion             | Fire    | Water  | 80  | 110    | 120     | 130     | 90      | 70    | 6          | True      |

800 rows × 12 columns

In \[ ]:

```
cols = df.columns
df = df[cols[0:4]+cols[4:12]]
df
```

## Exporting Data And Creating a New File : <a href="#exporting-data-and-creating-a-new-file" id="exporting-data-and-creating-a-new-file"></a>

### To Export File in CSV: <a href="#to-export-file-in-csv" id="to-export-file-in-csv"></a>

Let's say we have a data player\_score.txt and we want to convert it into learn\_pandas.csv. Here is our data **player\_score.txt** in text form.

![](<.gitbook/assets/image (112).png>)



```
import pandas as pd
df = pd.read_csv('player_score.txt')
df.to_csv('player_score.txt')
df
```

Out\[2]:

|   | # | Player | Match1 | Match2 | Match3 |
| - | - | ------ | ------ | ------ | ------ |
| 0 | 1 | Virat  | 100    | 25     | 75     |
| 1 | 2 | Dhoni  | 78     | 93     | 25     |
| 2 | 3 | Jadeja | 56     | 78     | 90     |
| 3 | 4 | Ashwin | 78     | 47     | 112    |
| 4 | 5 | Sachin | 112    | 45     | 78     |

If you do not want index in your file, you can simply put `index=False`

***

### **Parameters :** <a href="#parameters" id="parameters"></a>

**index :** Lets you insert index by changing `index=True` and `index=False`.

**sep :** lets you select sep , for example sep=',' or sep='@'.

***

Say, You want no index Column and separator should be ',' :

In \[4]:

```
df.to_csv('player_score.csv',index=False,sep=',')
df
```

Out\[4]:

|   | # | Player | Match1 | Match2 | Match3 |
| - | - | ------ | ------ | ------ | ------ |
| 0 | 1 | Virat  | 100    | 25     | 75     |
| 1 | 2 | Dhoni  | 78     | 93     | 25     |
| 2 | 3 | Jadeja | 56     | 78     | 90     |
| 3 | 4 | Ashwin | 78     | 47     | 112    |
| 4 | 5 | Sachin | 112    | 45     | 78     |

### To Export File in Excel: <a href="#to-export-file-in-excel" id="to-export-file-in-excel"></a>

In \[7]:

```
df.to_excel('player_score.xlsx')
df
```

Out\[7]:

|   | # | Player | Match1 | Match2 | Match3 |
| - | - | ------ | ------ | ------ | ------ |
| 0 | 1 | Virat  | 100    | 25     | 75     |
| 1 | 2 | Dhoni  | 78     | 93     | 25     |
| 2 | 3 | Jadeja | 56     | 78     | 90     |
| 3 | 4 | Ashwin | 78     | 47     | 112    |
| 4 | 5 | Sachin | 112    | 45     | 78     |

## Deleting a Column by using drop() : <a href="#deleting-a-column-by-using-drop" id="deleting-a-column-by-using-drop"></a>

DataFrame has a method called drop() that removes rows or columns according to specify column(label) names and corresponding axis.

### Parameters : <a href="#parameters" id="parameters"></a>

1.`inplace=True` means the operation would work on the original object.

2.`axis = 1` we are dropping the column, not the row.

In \[12]:

```
import pandas as pd
df = pd.read_csv('Pokemon.csv')
#Deleting a Column Generation
new_df = df.drop(columns=['Total'])
new_df
```

Out\[12]:

|     | #   | Name                  | Type 1  | Type 2 | HP  | Attack | Defense | Sp. Atk | Sp. Def | Speed | Generation | Legendary |
| --- | --- | --------------------- | ------- | ------ | --- | ------ | ------- | ------- | ------- | ----- | ---------- | --------- |
| 0   | 1   | Bulbasaur             | Grass   | Poison | 45  | 49     | 49      | 65      | 65      | 45    | 1          | False     |
| 1   | 2   | Ivysaur               | Grass   | Poison | 60  | 62     | 63      | 80      | 80      | 60    | 1          | False     |
| 2   | 3   | Venusaur              | Grass   | Poison | 80  | 82     | 83      | 100     | 100     | 80    | 1          | False     |
| 3   | 3   | VenusaurMega Venusaur | Grass   | Poison | 80  | 100    | 123     | 122     | 120     | 80    | 1          | False     |
| 4   | 4   | Charmander            | Fire    | NaN    | 39  | 52     | 43      | 60      | 50      | 65    | 1          | False     |
| ... | ... | ...                   | ...     | ...    | ... | ...    | ...     | ...     | ...     | ...   | ...        | ...       |
| 795 | 719 | Diancie               | Rock    | Fairy  | 50  | 100    | 150     | 100     | 150     | 50    | 6          | True      |
| 796 | 719 | DiancieMega Diancie   | Rock    | Fairy  | 50  | 160    | 110     | 160     | 110     | 110   | 6          | True      |
| 797 | 720 | HoopaHoopa Confined   | Psychic | Ghost  | 80  | 110    | 60      | 150     | 130     | 70    | 6          | True      |
| 798 | 720 | HoopaHoopa Unbound    | Psychic | Dark   | 80  | 160    | 60      | 170     | 130     | 80    | 6          | True      |
| 799 | 721 | Volcanion             | Fire    | Water  | 80  | 110    | 120     | 130     | 90      | 70    | 6          | True      |

800 rows × 12 columns

## Reset all the indexes : <a href="#reset-all-the-indexes" id="reset-all-the-indexes"></a>

If the original index are numbers, now we have indexes that are not continuous. Well, pandas has reset\_index() function. So to reset the index to the default integer index beginning at 0, We can simply use the reset\_index() function.

In \[13]:

```
new_df.reset_index(drop=True,inplace=True)
new_df
```

Out\[13]:

|     | #   | Name                  | Type 1  | Type 2 | HP  | Attack | Defense | Sp. Atk | Sp. Def | Speed | Generation | Legendary |
| --- | --- | --------------------- | ------- | ------ | --- | ------ | ------- | ------- | ------- | ----- | ---------- | --------- |
| 0   | 1   | Bulbasaur             | Grass   | Poison | 45  | 49     | 49      | 65      | 65      | 45    | 1          | False     |
| 1   | 2   | Ivysaur               | Grass   | Poison | 60  | 62     | 63      | 80      | 80      | 60    | 1          | False     |
| 2   | 3   | Venusaur              | Grass   | Poison | 80  | 82     | 83      | 100     | 100     | 80    | 1          | False     |
| 3   | 3   | VenusaurMega Venusaur | Grass   | Poison | 80  | 100    | 123     | 122     | 120     | 80    | 1          | False     |
| 4   | 4   | Charmander            | Fire    | NaN    | 39  | 52     | 43      | 60      | 50      | 65    | 1          | False     |
| ... | ... | ...                   | ...     | ...    | ... | ...    | ...     | ...     | ...     | ...   | ...        | ...       |
| 795 | 719 | Diancie               | Rock    | Fairy  | 50  | 100    | 150     | 100     | 150     | 50    | 6          | True      |
| 796 | 719 | DiancieMega Diancie   | Rock    | Fairy  | 50  | 160    | 110     | 160     | 110     | 110   | 6          | True      |
| 797 | 720 | HoopaHoopa Confined   | Psychic | Ghost  | 80  | 110    | 60      | 150     | 130     | 70    | 6          | True      |
| 798 | 720 | HoopaHoopa Unbound    | Psychic | Dark   | 80  | 160    | 60      | 170     | 130     | 80    | 6          | True      |
| 799 | 721 | Volcanion             | Fire    | Water  | 80  | 110    | 120     | 130     | 90      | 70    | 6          | True      |

800 rows × 12 columns

## Filtering Data with Multiple Conditions using loc\[]: <a href="#filtering-data-with-multiple-conditions-using-loc-5b-5d" id="filtering-data-with-multiple-conditions-using-loc-5b-5d"></a>

In \[14]:

```
filtered_df = df.loc[((df['Type 1'] == 'Grass') | (df['Type 2'] == 'Poison')) & (df['HP'] > 70)]
filtered_df
```

Out\[14]:

|     | #   | Name                    | Type 1 | Type 2   | Total | HP  | Attack | Defense | Sp. Atk | Sp. Def | Speed | Generation | Legendary |
| --- | --- | ----------------------- | ------ | -------- | ----- | --- | ------ | ------- | ------- | ------- | ----- | ---------- | --------- |
| 2   | 3   | Venusaur                | Grass  | Poison   | 525   | 80  | 82     | 83      | 100     | 100     | 80    | 1          | False     |
| 3   | 3   | VenusaurMega Venusaur   | Grass  | Poison   | 625   | 80  | 100    | 123     | 122     | 120     | 80    | 1          | False     |
| 50  | 45  | Vileplume               | Grass  | Poison   | 490   | 75  | 80     | 85      | 110     | 90      | 50    | 1          | False     |
| 77  | 71  | Victreebel              | Grass  | Poison   | 490   | 80  | 105    | 65      | 100     | 70      | 70    | 1          | False     |
| 79  | 73  | Tentacruel              | Water  | Poison   | 515   | 80  | 70     | 65      | 80      | 120     | 100   | 1          | False     |
| 111 | 103 | Exeggutor               | Grass  | Psychic  | 520   | 95  | 95     | 85      | 125     | 65      | 55    | 1          | False     |
| 168 | 154 | Meganium                | Grass  | NaN      | 525   | 80  | 82     | 100     | 83      | 100     | 80    | 2          | False     |
| 197 | 182 | Bellossom               | Grass  | NaN      | 490   | 75  | 80     | 95      | 90      | 100     | 50    | 2          | False     |
| 204 | 189 | Jumpluff                | Grass  | Flying   | 460   | 75  | 55     | 70      | 55      | 95      | 110   | 2          | False     |
| 207 | 192 | Sunflora                | Grass  | NaN      | 425   | 75  | 75     | 55      | 105     | 85      | 30    | 2          | False     |
| 298 | 275 | Shiftry                 | Grass  | Dark     | 480   | 90  | 100    | 60      | 90      | 60      | 80    | 3          | False     |
| 390 | 357 | Tropius                 | Grass  | Flying   | 460   | 99  | 68     | 83      | 72      | 87      | 51    | 3          | False     |
| 433 | 388 | Grotle                  | Grass  | NaN      | 405   | 75  | 89     | 85      | 55      | 65      | 36    | 4          | False     |
| 434 | 389 | Torterra                | Grass  | Ground   | 525   | 95  | 109    | 105     | 75      | 85      | 56    | 4          | False     |
| 505 | 455 | Carnivine               | Grass  | NaN      | 454   | 74  | 100    | 72      | 90      | 72      | 46    | 4          | False     |
| 510 | 460 | Abomasnow               | Grass  | Ice      | 494   | 90  | 92     | 75      | 92      | 85      | 60    | 4          | False     |
| 511 | 460 | AbomasnowMega Abomasnow | Grass  | Ice      | 594   | 90  | 132    | 105     | 132     | 105     | 30    | 4          | False     |
| 516 | 465 | Tangrowth               | Grass  | NaN      | 535   | 100 | 100    | 125     | 110     | 50      | 50    | 4          | False     |
| 550 | 492 | ShayminLand Forme       | Grass  | NaN      | 600   | 100 | 100    | 100     | 100     | 100     | 100   | 4          | True      |
| 551 | 492 | ShayminSky Forme        | Grass  | Flying   | 600   | 100 | 103    | 75      | 120     | 75      | 127   | 4          | True      |
| 556 | 497 | Serperior               | Grass  | NaN      | 528   | 75  | 75     | 95      | 75      | 95      | 113   | 5          | False     |
| 571 | 512 | Simisage                | Grass  | NaN      | 498   | 75  | 98     | 63      | 98      | 63      | 101   | 5          | False     |
| 617 | 556 | Maractus                | Grass  | NaN      | 461   | 75  | 86     | 67      | 106     | 67      | 60    | 5          | False     |
| 652 | 591 | Amoonguss               | Grass  | Poison   | 464   | 114 | 85     | 70      | 85      | 80      | 30    | 5          | False     |
| 659 | 598 | Ferrothorn              | Grass  | Steel    | 489   | 74  | 94     | 131     | 54      | 116     | 20    | 5          | False     |
| 701 | 640 | Virizion                | Grass  | Fighting | 580   | 91  | 90     | 72      | 90      | 129     | 108   | 5          | True      |
| 720 | 652 | Chesnaught              | Grass  | Fighting | 530   | 88  | 107    | 122     | 74      | 75      | 64    | 6          | False     |
| 741 | 673 | Gogoat                  | Grass  | NaN      | 531   | 123 | 100    | 62      | 97      | 81      | 68    | 6          | False     |

## To Replace Values in Column Based on Condition in Pandas : <a href="#to-replace-values-in-column-based-on-condition-in-pandas" id="to-replace-values-in-column-based-on-condition-in-pandas"></a>

In \[16]:

```
df.loc[df['Total'] > 500, 'Generation'] = 5
df
```

Out\[16]:

|     | #   | Name                  | Type 1  | Type 2 | Total | HP  | Attack | Defense | Sp. Atk | Sp. Def | Speed | Generation | Legendary |
| --- | --- | --------------------- | ------- | ------ | ----- | --- | ------ | ------- | ------- | ------- | ----- | ---------- | --------- |
| 0   | 1   | Bulbasaur             | Grass   | Poison | 318   | 45  | 49     | 49      | 65      | 65      | 45    | 1          | False     |
| 1   | 2   | Ivysaur               | Grass   | Poison | 405   | 60  | 62     | 63      | 80      | 80      | 60    | 1          | False     |
| 2   | 3   | Venusaur              | Grass   | Poison | 525   | 80  | 82     | 83      | 100     | 100     | 80    | 5          | False     |
| 3   | 3   | VenusaurMega Venusaur | Grass   | Poison | 625   | 80  | 100    | 123     | 122     | 120     | 80    | 5          | False     |
| 4   | 4   | Charmander            | Fire    | NaN    | 309   | 39  | 52     | 43      | 60      | 50      | 65    | 1          | False     |
| ... | ... | ...                   | ...     | ...    | ...   | ... | ...    | ...     | ...     | ...     | ...   | ...        | ...       |
| 795 | 719 | Diancie               | Rock    | Fairy  | 600   | 50  | 100    | 150     | 100     | 150     | 50    | 5          | True      |
| 796 | 719 | DiancieMega Diancie   | Rock    | Fairy  | 700   | 50  | 160    | 110     | 160     | 110     | 110   | 5          | True      |
| 797 | 720 | HoopaHoopa Confined   | Psychic | Ghost  | 600   | 80  | 110    | 60      | 150     | 130     | 70    | 5          | True      |
| 798 | 720 | HoopaHoopa Unbound    | Psychic | Dark   | 680   | 80  | 160    | 60      | 170     | 130     | 80    | 5          | True      |
| 799 | 721 | Volcanion             | Fire    | Water  | 600   | 80  | 110    | 120     | 130     | 90      | 70    | 5          | True      |

800 rows × 13 columns

## Aggregate Statistics (Groupby) perform grouping operations: <a href="#aggregate-statistics-groupby-perform-grouping-operations" id="aggregate-statistics-groupby-perform-grouping-operations"></a>

Pandas GroupBy is a powerful and versatile function in Python. It allows you to split your data into separate groups to perform computations for better analysis.

Let me take an example to elaborate on this. Let’s say we are trying to analyze the weight of a person in a city. We can easily get a fair idea of their weight by determining the mean weight of all the city dwellers. But here ‘s a question – would the weight be affected by the gender of a person?

We can group the city dwellers into different gender groups and calculate their mean weight. This would give us a better insight into the weight of a person living in the city. But we can probably get an even better picture if we further separate these gender groups into different age groups and then take their mean weight (because a teenage boy’s weight could differ from that of an adult male)!

In \[11]:

```
df.groupby(['Type 1', 'Type 2']).count()['count']
```

Out\[11]:

|     | #   | Name                  | Type 1  | Type 2 | Total | HP  | Attack | Defense | Sp. Atk | Sp. Def | Speed | Generation | Legendary | count |
| --- | --- | --------------------- | ------- | ------ | ----- | --- | ------ | ------- | ------- | ------- | ----- | ---------- | --------- | ----- |
| 0   | 1   | Bulbasaur             | Grass   | Poison | 318   | 45  | 49     | 49      | 65      | 65      | 45    | 1          | False     | 1     |
| 1   | 2   | Ivysaur               | Grass   | Poison | 405   | 60  | 62     | 63      | 80      | 80      | 60    | 1          | False     | 1     |
| 2   | 3   | Venusaur              | Grass   | Poison | 525   | 80  | 82     | 83      | 100     | 100     | 80    | 1          | False     | 1     |
| 3   | 3   | VenusaurMega Venusaur | Grass   | Poison | 625   | 80  | 100    | 123     | 122     | 120     | 80    | 1          | False     | 1     |
| 4   | 4   | Charmander            | Fire    | NaN    | 309   | 39  | 52     | 43      | 60      | 50      | 65    | 1          | False     | 1     |
| ... | ... | ...                   | ...     | ...    | ...   | ... | ...    | ...     | ...     | ...     | ...   | ...        | ...       | ...   |
| 795 | 719 | Diancie               | Rock    | Fairy  | 600   | 50  | 100    | 150     | 100     | 150     | 50    | 6          | True      | 1     |
| 796 | 719 | DiancieMega Diancie   | Rock    | Fairy  | 700   | 50  | 160    | 110     | 160     | 110     | 110   | 6          | True      | 1     |
| 797 | 720 | HoopaHoopa Confined   | Psychic | Ghost  | 600   | 80  | 110    | 60      | 150     | 130     | 70    | 6          | True      | 1     |
| 798 | 720 | HoopaHoopa Unbound    | Psychic | Dark   | 680   | 80  | 160    | 60      | 170     | 130     | 80    | 6          | True      | 1     |
| 799 | 721 | Volcanion             | Fire    | Water  | 600   | 80  | 110    | 120     | 130     | 90      | 70    | 6          | True      | 1     |

800 rows × 14 columns

## Initialize All Values of A Column : <a href="#initialize-all-values-of-a-column" id="initialize-all-values-of-a-column"></a>

Say We want to initialize all values of column **count** as 1.

In \[10]:

```
df['count']=1
df
```

Out\[10]:

|     | #   | Name                  | Type 1  | Type 2 | Total | HP  | Attack | Defense | Sp. Atk | Sp. Def | Speed | Generation | Legendary | count |
| --- | --- | --------------------- | ------- | ------ | ----- | --- | ------ | ------- | ------- | ------- | ----- | ---------- | --------- | ----- |
| 0   | 1   | Bulbasaur             | Grass   | Poison | 318   | 45  | 49     | 49      | 65      | 65      | 45    | 1          | False     | 1     |
| 1   | 2   | Ivysaur               | Grass   | Poison | 405   | 60  | 62     | 63      | 80      | 80      | 60    | 1          | False     | 1     |
| 2   | 3   | Venusaur              | Grass   | Poison | 525   | 80  | 82     | 83      | 100     | 100     | 80    | 1          | False     | 1     |
| 3   | 3   | VenusaurMega Venusaur | Grass   | Poison | 625   | 80  | 100    | 123     | 122     | 120     | 80    | 1          | False     | 1     |
| 4   | 4   | Charmander            | Fire    | NaN    | 309   | 39  | 52     | 43      | 60      | 50      | 65    | 1          | False     | 1     |
| ... | ... | ...                   | ...     | ...    | ...   | ... | ...    | ...     | ...     | ...     | ...   | ...        | ...       | ...   |
| 795 | 719 | Diancie               | Rock    | Fairy  | 600   | 50  | 100    | 150     | 100     | 150     | 50    | 6          | True      | 1     |
| 796 | 719 | DiancieMega Diancie   | Rock    | Fairy  | 700   | 50  | 160    | 110     | 160     | 110     | 110   | 6          | True      | 1     |
| 797 | 720 | HoopaHoopa Confined   | Psychic | Ghost  | 600   | 80  | 110    | 60      | 150     | 130     | 70    | 6          | True      | 1     |
| 798 | 720 | HoopaHoopa Unbound    | Psychic | Dark   | 680   | 80  | 160    | 60      | 170     | 130     | 80    | 6          | True      | 1     |
| 799 | 721 | Volcanion             | Fire    | Water  | 600   | 80  | 110    | 120     | 130     | 90      | 70    | 6          | True      | 1     |

800 rows × 14 columns

## Working With Large Amount of Data : <a href="#working-with-large-amount-of-data" id="working-with-large-amount-of-data"></a>

In \[14]:

```
new_df = pd.DataFrame(columns=df.columns)

for df in pd.read_csv('Pokemon.csv', chunksize=5):
    results = df.groupby(['Type 1']).count()
    
    new_df = pd.concat([new_df, results])

new_df
```

Out\[14]:

|         | #   | Name | Type 1 | Type 2 | Total | HP  | Attack | Defense | Sp. Atk | Sp. Def | Speed | Generation | Legendary |
| ------- | --- | ---- | ------ | ------ | ----- | --- | ------ | ------- | ------- | ------- | ----- | ---------- | --------- |
| Fire    | 1   | 1    | NaN    | 0      | 1     | 1   | 1      | 1       | 1       | 1       | 1     | 1          | 1         |
| Grass   | 4   | 4    | NaN    | 4      | 4     | 4   | 4      | 4       | 4       | 4       | 4     | 4          | 4         |
| Fire    | 4   | 4    | NaN    | 3      | 4     | 4   | 4      | 4       | 4       | 4       | 4     | 4          | 4         |
| Water   | 1   | 1    | NaN    | 0      | 1     | 1   | 1      | 1       | 1       | 1       | 1     | 1          | 1         |
| Bug     | 2   | 2    | NaN    | 0      | 2     | 2   | 2      | 2       | 2       | 2       | 2     | 2          | 2         |
| ...     | ... | ...  | ...    | ...    | ...   | ... | ...    | ...     | ...     | ...     | ...   | ...        | ...       |
| Fairy   | 1   | 1    | NaN    | 0      | 1     | 1   | 1      | 1       | 1       | 1       | 1     | 1          | 1         |
| Flying  | 2   | 2    | NaN    | 2      | 2     | 2   | 2      | 2       | 2       | 2       | 2     | 2          | 2         |
| Fire    | 1   | 1    | NaN    | 1      | 1     | 1   | 1      | 1       | 1       | 1       | 1     | 1          | 1         |
| Psychic | 2   | 2    | NaN    | 2      | 2     | 2   | 2      | 2       | 2       | 2       | 2     | 2          | 2         |
| Rock    | 2   | 2    | NaN    | 2      | 2     | 2   | 2      | 2       | 2       | 2       | 2     | 2          | 2         |

433 rows × 13 columns

## Generate a Column With Random Numbers : <a href="#generate-a-column-with-random-numbers" id="generate-a-column-with-random-numbers"></a>

You can generate a column with random numbers by using random module . For Example , here **total** column is random number column.

In \[18]:

```
import random
df['Total']=df['Total'].apply(lambda x: random.randint(1,100))
df
```

Out\[18]:

|     | #   | Name                  | Type 1  | Type 2 | Total | HP  | Attack | Defense | Sp. Atk | Sp. Def | Speed | Generation | Legendary |
| --- | --- | --------------------- | ------- | ------ | ----- | --- | ------ | ------- | ------- | ------- | ----- | ---------- | --------- |
| 0   | 1   | Bulbasaur             | Grass   | Poison | 54    | 45  | 49     | 49      | 65      | 65      | 45    | 1          | False     |
| 1   | 2   | Ivysaur               | Grass   | Poison | 69    | 60  | 62     | 63      | 80      | 80      | 60    | 1          | False     |
| 2   | 3   | Venusaur              | Grass   | Poison | 17    | 80  | 82     | 83      | 100     | 100     | 80    | 1          | False     |
| 3   | 3   | VenusaurMega Venusaur | Grass   | Poison | 34    | 80  | 100    | 123     | 122     | 120     | 80    | 1          | False     |
| 4   | 4   | Charmander            | Fire    | NaN    | 18    | 39  | 52     | 43      | 60      | 50      | 65    | 1          | False     |
| ... | ... | ...                   | ...     | ...    | ...   | ... | ...    | ...     | ...     | ...     | ...   | ...        | ...       |
| 795 | 719 | Diancie               | Rock    | Fairy  | 49    | 50  | 100    | 150     | 100     | 150     | 50    | 6          | True      |
| 796 | 719 | DiancieMega Diancie   | Rock    | Fairy  | 80    | 50  | 160    | 110     | 160     | 110     | 110   | 6          | True      |
| 797 | 720 | HoopaHoopa Confined   | Psychic | Ghost  | 43    | 80  | 110    | 60      | 150     | 130     | 70    | 6          | True      |
| 798 | 720 | HoopaHoopa Unbound    | Psychic | Dark   | 7     | 80  | 160    | 60      | 170     | 130     | 80    | 6          | True      |
| 799 | 721 | Volcanion             | Fire    | Water  | 67    | 80  | 110    | 120     | 130     | 90      | 70    | 6          | True      |

800 rows × 13 columns

![](<.gitbook/assets/image (78).png>)
