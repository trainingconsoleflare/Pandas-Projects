# Seaborn

![](<.gitbook/assets/image (12).png>)

**Seaborn is a Python data visualization library based on matplotlib. It provides a high-level interface for drawing attractive and informative statistical graphics.**

## Install Seaborn <a href="#install-seaborn" id="install-seaborn"></a>

In \[1]:

```
pip install seaborn
```

## Get Data Repository: <a href="#get-data-repository" id="get-data-repository"></a>

When you install seaborn , it comes with datasets for you to practice on. You can go through [Data Repository](https://github.com/mwaskom/seaborn-data).

![](<.gitbook/assets/image (114).png>)



## Import All Libraries <a href="#import-all-libraries" id="import-all-libraries"></a>

In \[2]:

```
import matplotlib.pyplot as plt
import pandas as pd
import seaborn as sns
```

## Get Dataset names: <a href="#get-dataset-names" id="get-dataset-names"></a>

In \[3]:

```
sns.get_dataset_names()
```

Out\[3]:

```
['anagrams',
 'anscombe',
 'attention',
 'brain_networks',
 'car_crashes',
 'diamonds',
 'dots',
 'exercise',
 'flights',
 'fmri',
 'gammas',
 'geyser',
 'iris',
 'mpg',
 'penguins',
 'planets',
 'taxis',
 'tips',
 'titanic']
```



## Load Dataset <a href="#load-dataset" id="load-dataset"></a>

In \[4]:

```
import matplotlib.pyplot as plt
import pandas as pd
import seaborn as sns

df = sns.load_dataset('tips')
df.head()
```

Out\[4]:

|   | total\_bill | tip  | sex    | smoker | day | time   | size |
| - | ----------- | ---- | ------ | ------ | --- | ------ | ---- |
| 0 | 16.99       | 1.01 | Female | No     | Sun | Dinner | 2    |
| 1 | 10.34       | 1.66 | Male   | No     | Sun | Dinner | 3    |
| 2 | 21.01       | 3.50 | Male   | No     | Sun | Dinner | 3    |
| 3 | 23.68       | 3.31 | Male   | No     | Sun | Dinner | 2    |
| 4 | 24.59       | 3.61 | Female | No     | Sun | Dinner | 4    |

## How to create your first graph <a href="#how-to-create-your-first-graph" id="how-to-create-your-first-graph"></a>

### Load Dataset <a href="#load-dataset" id="load-dataset"></a>

We use **load\_dataset** method to load datasets from data repository.

In \[5]:

```
sns.load_dataset('tips')
```

Out\[5]:

|     | total\_bill | tip  | sex    | smoker | day  | time   | size |
| --- | ----------- | ---- | ------ | ------ | ---- | ------ | ---- |
| 0   | 16.99       | 1.01 | Female | No     | Sun  | Dinner | 2    |
| 1   | 10.34       | 1.66 | Male   | No     | Sun  | Dinner | 3    |
| 2   | 21.01       | 3.50 | Male   | No     | Sun  | Dinner | 3    |
| 3   | 23.68       | 3.31 | Male   | No     | Sun  | Dinner | 2    |
| 4   | 24.59       | 3.61 | Female | No     | Sun  | Dinner | 4    |
| ... | ...         | ...  | ...    | ...    | ...  | ...    | ...  |
| 239 | 29.03       | 5.92 | Male   | No     | Sat  | Dinner | 3    |
| 240 | 27.18       | 2.00 | Female | Yes    | Sat  | Dinner | 2    |
| 241 | 22.67       | 2.00 | Male   | Yes    | Sat  | Dinner | 2    |
| 242 | 17.82       | 1.75 | Male   | No     | Sat  | Dinner | 2    |
| 243 | 18.78       | 3.00 | Female | No     | Thur | Dinner | 2    |

244 rows × 7 columns

Creating graph with the help of seaborn is as easy as matplotlib.Suppose we want to create a **scatter plot** of relationship between **Totalbill** and **tips**. All you need to do is to use **scatterplot** method.

_**Note :We use scatterplot() method to create scatter plot instead of scatter like we used to do in matplotlib.**_

In \[8]:

```
sns.scatterplot(x='total_bill',y='tip',data=df)
plt.show()
```

![](<.gitbook/assets/image (85).png>)



### hue: <a href="#hue" id="hue"></a>

hue : (optional) This parameter take column name for colour encoding.

Suppose we also want to know smokers along with total\_bill and tip. We can show this third information with the help of hue.

In \[7]:

```
sns.scatterplot(x='total_bill',y='tip',hue='smoker',data=df)
plt.show()
```

![](<.gitbook/assets/image (46).png>)



You can also change order of hue by using hue\_order property.

In \[9]:

```
sns.scatterplot(x='total_bill',y='tip',hue='smoker',hue_order=['No','Yes'],data=df)
plt.show()
```

![](<.gitbook/assets/image (95).png>)



### Palette: <a href="#palette" id="palette"></a>

**What if you want to change color encoding for smokers and non-smokers.**

For this you can use _**palette**_ property.

In \[11]:

```
c = {'No':'Green','Yes':'Red'}
sns.scatterplot(x='total_bill',y='tip',hue='smoker',hue_order=['No','Yes'],palette = c,data=df)
plt.show()
```

![](<.gitbook/assets/image (88).png>)



**smoker** is a categorical value , but you can also use any numerical value in hue. Let's say i want to color encode sizes.

In \[12]:

```
# sns.scatterplot(x='total_bill',y='tip',hue='size',data=df)
# plt.show()
```

![](<.gitbook/assets/image (49).png>)



## relplot: <a href="#relplot" id="relplot"></a>

relplot is used for many purposes , but the main purpose behind using replot is **sub-plotting**. Suppose we want to suplot our graph based on **smoker** and **non-smoker**.

We can use **row**,**col** to achieve this result.

Let's see this with an example.

In \[14]:

```
sns.relplot(x='total_bill',y='tip',data=df,col='smoker')
plt.show()
```

![](<.gitbook/assets/image (44).png>)



What if i used **row** property.

In \[15]:

```
# sns.relplot(x='total_bill',y='tip',data=df,row='smoker')
# plt.show()
```

![](<.gitbook/assets/image (16) (1).png>)

Graph would have appeared like this.

We can do same with size by choosing col as size.

In \[17]:

```
# %matplotlib notebook
# sns.relplot(x='total_bill',y='tip',hue='size',data=df,col='size')
# plt.show()
```

\


![](<.gitbook/assets/image (113).png>)



Now as you can see it has one column and all the graphs are in a single column. We can use col\_wrap to restrict number of graphs in a single column.

In \[21]:

```
# %matplotlib inline
# sns.relplot(x='total_bill',y='tip',hue='size',data=df,col='size',col_wrap=3)
# plt.show()
```

![](<.gitbook/assets/image (34).png>)



## Applying Row and Column property in a single plot <a href="#applying-row-and-column-property-in-a-single-plot" id="applying-row-and-column-property-in-a-single-plot"></a>

what if i want to see data of smokers in column and data of time in rows, we can use col and row property in a single plot.

In \[22]:

```
sns.relplot(x='total_bill',y='tip',data=df,row='time',col='smoker')
plt.show()
```

![](<.gitbook/assets/image (38).png>)



### using categorical column <a href="#using-categorical-column" id="using-categorical-column"></a>

what if one of my axis is categorical column ?

In \[23]:

```
# sns.relplot(x='total_bill',y='time',data=df)
# plt.show()
```

![](<.gitbook/assets/image (108).png>)



## size <a href="#size" id="size"></a>

relplot offers a property **size** that changes the size of values. Let's see this with an example.

In \[25]:

```
sns.relplot(x='total_bill',y='tip',data=df,size='size')
plt.show()
```

![](<.gitbook/assets/image (65).png>)

## A Useful Example <a href="#a-useful-example" id="a-useful-example"></a>

Seaborn offers another dataset named **flights**. Let's see this data first.

In \[13]:

```
import matplotlib.pyplot as plt
import seaborn as sns
df = sns.load_dataset('flights')
df
```

Out\[13]:

|     | year | month | passengers |
| --- | ---- | ----- | ---------- |
| 0   | 1949 | Jan   | 112        |
| 1   | 1949 | Feb   | 118        |
| 2   | 1949 | Mar   | 132        |
| 3   | 1949 | Apr   | 129        |
| 4   | 1949 | May   | 121        |
| ... | ...  | ...   | ...        |
| 139 | 1960 | Aug   | 606        |
| 140 | 1960 | Sep   | 508        |
| 141 | 1960 | Oct   | 461        |
| 142 | 1960 | Nov   | 390        |
| 143 | 1960 | Dec   | 432        |

144 rows × 3 columns



If we want to know how many passengers were on board on a particular month and year.

In \[7]:

```
sns.relplot(x='passengers',y='month',hue = 'year',data=df)
```

![](<.gitbook/assets/image (111).png>)



## Categorical column and relplot <a href="#categorical-column-and-relplot" id="categorical-column-and-relplot"></a>

Whenever there is a categorical column and a numerical column , we donot use relplot. Let me show you why?

In \[15]:

```
import matplotlib.pyplot as plt
import seaborn as sns

df = sns.load_dataset('tips')
sns.relplot(x='time',y='tip',data=df)
```

![](<.gitbook/assets/image (116).png>)



This obviously is not a clear graph. So whenever we deal with categorical column we use catplot(categorical plot).

## Catplot <a href="#catplot" id="catplot"></a>

Categorical plot is always a best option if one value is Categorical and another is numerical.

In \[17]:

```
import matplotlib.pyplot as plt
import seaborn as sns

df = sns.load_dataset('tips')
sns.catplot(x='time',y='tip',data=df)
```

![](<.gitbook/assets/image (21).png>)



## A Useful example <a href="#a-useful-example" id="a-useful-example"></a>

Suppose we want to know **total bill** dayswise , we can use catplot as day is a categorical plot while total bill is numerical.

In \[23]:

```
import matplotlib.pyplot as plt
import seaborn as sns
import pandas as pd

df = sns.load_dataset('tips')
sns.catplot(x='total_bill',y='day',data=df)
plt.show()
```

![](<.gitbook/assets/image (48).png>)



You can change graph to bar by using **kind = 'bar'** property.

In \[25]:

```
import matplotlib.pyplot as plt
import seaborn as sns
import pandas as pd

df = sns.load_dataset('tips')
sns.catplot(x='total_bill',y='day',data=df,kind='bar')
plt.show()
```

![](<.gitbook/assets/image (7).png>)



You can change graph to bar by using **kind = 'point'** property.

In \[27]:

```
import matplotlib.pyplot as plt
import seaborn as sns
import pandas as pd

df = sns.load_dataset('tips')
sns.catplot(x='total_bill',y='day',data=df,kind='point')
plt.show()
```

![](<.gitbook/assets/image (20) (1).png>)



You can change graph to bar by using **kind = 'violin'** property.

In \[29]:

```
import matplotlib.pyplot as plt
import seaborn as sns
import pandas as pd

df = sns.load_dataset('tips')
sns.catplot(x='total_bill',y='day',data=df,kind='violin')
plt.grid()
plt.show()
```

![](<.gitbook/assets/image (106).png>)



From this violin chart it is very easy to figure out pattern of bills that were given on any day. Like on thursday most of the total bill were between 10 to 20 dollars.

You can change graph to bar by using **kind = 'boxen'** property.

In \[31]:

```
import matplotlib.pyplot as plt
import seaborn as sns
import pandas as pd

df = sns.load_dataset('tips')
sns.catplot(x='day',y='total_bill',data=df,kind='boxen')
plt.grid()
plt.show()
```

![](<.gitbook/assets/image (67).png>)



Boxen chart also works like violin chart.\
**The only difference is Boxen chart assigns darkest colour to the area where most of the data lies.**

**As you can see a horizontal line , this horizontal line is median of the data.**

**dots that you see in boxen chart are outliers**

You can change graph to bar by using **kind = 'box'** property.

In \[32]:

```
import matplotlib.pyplot as plt
import seaborn as sns
import pandas as pd

df = sns.load_dataset('tips')
sns.catplot(x='day',y='total_bill',data=df,kind='box')
plt.grid()
plt.show()
```

![](<.gitbook/assets/image (11).png>)

## Countplot <a href="#countplot" id="countplot"></a>

seaborn.countplot() method is used to Show the counts of observations in each categorical bin.



```
import matplotlib.pyplot as plt
import seaborn as sns

df = sns.load_dataset('tips')
sns.countplot(y='smoker',data=df)
```

![](<.gitbook/assets/image (62).png>)



## A Useful Example <a href="#a-useful-example" id="a-useful-example"></a>

Suppose we want to count **Type 1** of pokemon in our pokemon dataset. We can use countplot here.

In \[22]:

```
import matplotlib.pyplot as plt
import seaborn as sns
import pandas as pd

df = pd.read_csv('Pokemon.csv')
sns.countplot(y='Type 1',data=df)
```

![](<.gitbook/assets/image (2) (1).png>)



## Introduction to pairplot: <a href="#introduction-to-pairplot" id="introduction-to-pairplot"></a>

Plot pairwise relationships in a dataset.

By default, this function will create a grid of Axes such that each numeric variable in data will by shared across the y-axes across a single row and the x-axes across a single column.

In \[35]:

```
import matplotlib.pyplot as plt
import seaborn as sns

df = sns.load_dataset('tips')
sns.pairplot(data = df)
plt.show()
```

![](<.gitbook/assets/image (119).png>)



You can also add hue property to see gender of customers.

In \[36]:

```
import matplotlib.pyplot as plt
import seaborn as sns

df = sns.load_dataset('tips')
sns.pairplot(data = df,hue='sex')
plt.show()
```

![](<.gitbook/assets/image (103).png>)



## A Useful Example : <a href="#a-useful-example" id="a-useful-example"></a>

In \[38]:

```
import matplotlib.pyplot as plt
import seaborn as sns

df = sns.load_dataset('iris')
df
```

Out\[38]:

|     | sepal\_length | sepal\_width | petal\_length | petal\_width | species   |
| --- | ------------- | ------------ | ------------- | ------------ | --------- |
| 0   | 5.1           | 3.5          | 1.4           | 0.2          | setosa    |
| 1   | 4.9           | 3.0          | 1.4           | 0.2          | setosa    |
| 2   | 4.7           | 3.2          | 1.3           | 0.2          | setosa    |
| 3   | 4.6           | 3.1          | 1.5           | 0.2          | setosa    |
| 4   | 5.0           | 3.6          | 1.4           | 0.2          | setosa    |
| ... | ...           | ...          | ...           | ...          | ...       |
| 145 | 6.7           | 3.0          | 5.2           | 2.3          | virginica |
| 146 | 6.3           | 2.5          | 5.0           | 1.9          | virginica |
| 147 | 6.5           | 3.0          | 5.2           | 2.0          | virginica |
| 148 | 6.2           | 3.4          | 5.4           | 2.3          | virginica |
| 149 | 5.9           | 3.0          | 5.1           | 1.8          | virginica |

150 rows × 5 columns

## Check Range of Sepal length for species: <a href="#check-range-of-sepal-length-for-species" id="check-range-of-sepal-length-for-species"></a>

Now as we have discussed before in the note, whenever we are dealing with ranges , Histogram is always a better option. So let us create a histogram for species and their sepal length.

In \[40]:

```
import matplotlib.pyplot as plt
import seaborn as sns

df = sns.load_dataset('iris')
f = sns.FacetGrid(data = df,col='species')
f.map(plt.hist,'sepal_length')
plt.show()
```

![](<.gitbook/assets/image (74).png>)

