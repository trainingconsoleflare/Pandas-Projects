# Matplotlib - Data Visualization

![](<.gitbook/assets/image (104).png>)

## Data Visualization With Matplotlib <a href="#data-visualization-with-matplotlib" id="data-visualization-with-matplotlib"></a>

![](<.gitbook/assets/image (40).png>)

## Introduction <a href="#introduction" id="introduction"></a>

**Data visualization is the graphic representation of data.** It involves producing images that communicate relationships among the represented data to viewers. Visualizing data is an essential part of _**data analysis**_ and _**machine learning.**_

We'll use Python libraries Matplotlib and Seaborn to learn and apply some popular data visualization techniques. We'll use the words chart, plot, and graph interchangeably in this tutorial.

To begin, let's install and import the libraries. We'll use the **matplotlib.pyplot module** for basic plots like line & bar charts. It is often imported with the alias _**plt**_.



### Download Matplotlib : <a href="#download-matplotlib" id="download-matplotlib"></a>

In \[ ]:

```
pip install matplotlib 
```

## Matplotlib Example : <a href="#matplotlib-example" id="matplotlib-example"></a>

Imagine a shop , where items are sold each day and shopkeeper wants to see , how many items are sold each day visually. So We have data for days and items sold for a week.

In \[2]:

```
import matplotlib.pyplot as plt

items = [10,5,7,9,20,6,11]
days = [1,2,3,4,5,6,7]

plt.plot(days,items)
plt.show()
```

![](<.gitbook/assets/image (42).png>)

Now here you can see on the **5th day** , most of the items are sold. When we see data in graph, it becomes more clear and we can take decisions accordingly.

## Categorical Column <a href="#categorical-column" id="categorical-column"></a>

As you have seen above example, all columns are numeric, say one column is categorical column like **Day1** and **Day2.**

****

```
import matplotlib.pyplot as plt

items = [10,5,7,9,20,6,11]
days = ['Day1','Day2','Day3','Day4','Day5','Day6','Day7']

plt.plot(days,items)
plt.show()
```

![](<.gitbook/assets/image (41).png>)

## Properties <a href="#properties" id="properties"></a>

### title: <a href="#title" id="title"></a>

_**title**_ property is used to give name or title to your graph.Say we want to name this graph **Shop - Data**

### x-label: <a href="#x-label" id="x-label"></a>

_**x-label**_ is a property to give name to x-axis. Say we want to give x-axis **Days** name.

### y-label: <a href="#y-label" id="y-label"></a>

_**y-label**_ is a property to give name to y-axis. Say we want to give y-axis **Items** name.

### linestyle: <a href="#linestyle" id="linestyle"></a>

You can change lines in line chart with this property. You can go through [linestyle ](https://matplotlib.org/3.5.0/gallery/lines\_bars\_and\_markers/linestyles.html)to check all kind of lines.

### colors : <a href="#colors" id="colors"></a>

You can change colors by using this property

### Grid: <a href="#grid" id="grid"></a>

_**grid**_ property is used to make graph more understandable. You are seeing the graph above , if you are not aware about data, you will face problems about the actual data but with the help of grid , graph is more readable.



```
import matplotlib.pyplot as plt

items = [10,5,7,9,20,6,11]
days = ['Day1','Day2','Day3','Day4','Day5','Day6','Day7']

plt.plot(days,items,color='red',linestyle = '--')
plt.title('Shop-Data')
plt.xlabel('Days')
plt.ylabel('Items')
plt.grid()
plt.show()
```

![](<.gitbook/assets/image (93).png>)

![](<.gitbook/assets/image (53).png>)



### Marker: <a href="#marker" id="marker"></a>

We can use marker keyword argument to mark each data point with a circle while creating line chart. You can go through all kind of markers from [here](https://matplotlib.org/3.5.0/gallery/lines\_bars\_and\_markers/marker\_reference.html).

In \[5]:

```
import matplotlib.pyplot as plt

items = [10,5,7,9,20,6,11]
days = ['Day1','Day2','Day3','Day4','Day5','Day6','Day7']

plt.plot(days,items,marker='o')
plt.title('Shop-Data')
plt.xlabel('Days')
plt.ylabel('Items')
plt.grid()
plt.show()
```

![](<.gitbook/assets/image (1) (1).png>)



first Data point is (Day1,10) and Second Data point is (Day2, 10) and so on.

## The Problem Of Overlapping and how to Overcome it <a href="#the-problem-of-overlapping-and-how-to-overcome-it" id="the-problem-of-overlapping-and-how-to-overcome-it"></a>

Let us say you have two data and you simply created a plot. But the plot was confusing as lines were overlapping each other.

In \[6]:

```
import matplotlib.pyplot as plt

data1 = [10,5,7,9,20,6,11]
data2 = [5,7,2,5,6,8,2]

plt.plot(data1,data2,marker='o')
plt.title('Data')
plt.xlabel('Data1')
plt.ylabel('Data2')
plt.grid()
plt.show()
```

![](<.gitbook/assets/image (79).png>)



Now here , our line chart is not clear and the whole point of graph is dismissed and it is happening because we donot have any order. To overcome this overlapping , all we need to do is to sort\_values. We can sort Data1 so that no overlapping occurs.

In \[7]:

```
import matplotlib.pyplot as plt
data1 = [10,5,7,9,20,6,11]
data2 = [5,7,2,5,6,8,2]
data2.sort()
plt.plot(data1,data2,marker='o')
plt.title('Data')
plt.xlabel('Data1')
plt.ylabel('Data2')
plt.grid()
plt.show()
```

![](<.gitbook/assets/image (69).png>)



## Let's add more data : <a href="#lets-add-more-data" id="lets-add-more-data"></a>

As of now we have dealt with two kinds of data , now in this example we will deal with more. Suppose a bunch of students gave two tests for mathematics and science.

In \[8]:

```
import matplotlib.pyplot as plt

students = ['abhishek','nihal','divya','ranjan']
maths = [90,98,100,78]
science = [45,74,83,60]
```

### To create Multiple Line chart: <a href="#to-create-multiple-line-chart" id="to-create-multiple-line-chart"></a>

You can create multiple line chart by using plot methods.

In \[9]:

```
plt.plot(students,maths,marker='o')
plt.plot(students,science,marker='o')
plt.xlabel('Students')
plt.ylabel('Marks')
plt.grid()
plt.show()
```

![](<.gitbook/assets/image (117).png>)



## Different types of plotting in Matplotlib: <a href="#different-types-of-plotting-in-matplotlib" id="different-types-of-plotting-in-matplotlib"></a>

### Bar Graph: <a href="#bar-graph" id="bar-graph"></a>

It is a type of visualization that helps in representing categorical data. It has rectangular bars (hence the name, bar graph) that can be represented horizontally and vertically. Let's take same example of students and their scores.

In \[11]:

```
import matplotlib.pyplot as plt

students = ['abhishek','nihal','divya','ranjan']
maths = [90,98,100,78]
maths.sort()
plt.bar(students,maths)
plt.title('Result')
plt.xlabel('Students')
plt.ylabel('Maths-Score')
plt.show()
```

![](<.gitbook/assets/image (1) (2) (1).png>)



For horizontal graph we use barh() method :

In \[12]:

```
import matplotlib.pyplot as plt

students = ['abhishek','nihal','divya','ranjan']
maths = [90,98,100,78]
plt.barh(students,maths)
plt.title('Result')
plt.xlabel('Students')
plt.ylabel('Maths-Score')
plt.show()
```

![](<.gitbook/assets/image (63).png>)



## Scatter Plot: <a href="#scatter-plot" id="scatter-plot"></a>

It helps visualize the relationship between 2 or more variables. In addition to this, it helps in identifying outliers(abnormalities) which could be present in a dataset. This way, the exceptions in data could be better understood and the reason behind the same could be found out.

Like if there are more than two variables , we can use scatter plot. So our example for maths and science score fits well here.

In \[13]:

```
import matplotlib.pyplot as plt

students = ['abhishek','nihal','divya','ranjan']
maths = [90,98,100,78]
science = [45,74,83,60]

plt.scatter(students,maths,label='Maths',color='r')  #You can choose colors like this
plt.scatter(students,science,label='Science',color='b')
plt.xlabel('Maths')
plt.ylabel('Science')
plt.legend()
plt.grid()
plt.show()
```

![](<.gitbook/assets/image (90).png>)

## Histogram: <a href="#histogram" id="histogram"></a>

A histogram is a graph showing frequency distributions.

It is a graph showing the number of observations within each given interval.

In simple words , let us say you have a data of weights , something like this :

_**weights = \[50,60,70,80,90]**_

and another data of people falling in the range of weight:

_**people\_weight = \[51,54,57,78,88,63,52,86]**_

As you can see,

_People who fall in the range of 50-60 : 51,54,57,52 People who fall in the range of 60-70 : 63 People who fall in the range of 70-80 : 78 People who fall in the range of 80-90 : 88,86_

So in histogram we pass two parameters :

**range(r) : Here weights is range.** **values : Here people\_weight is values**

```
import matplotlib.pyplot as plt

weights = [50,60,70,80,90]
people_weight = [51,54,57,78,88,63,52,86]

plt.hist(people_weight,bins=weights)
plt.show()
```

![](<.gitbook/assets/image (28).png>)



_**From this graph , It is clear that 4 people fall in range of 50 to 60 and only 1 person fall in range of 60 to 70 and as well as 70 to 80 and there are 2 people who fall in range of 80 to 90.**_

## A Useful Example: <a href="#a-useful-example" id="a-useful-example"></a>

Suppose we want to find out how many pokemons fall in a particular range of speed. We can use our Pokemon data set to find out.

In \[15]:

```
import matplotlib.pyplot as plt
import pandas as pd

df = pd.read_csv('Pokemon.csv')
range_speed = [0,50,100,150,200,250]
plt.hist(df['Speed'],bins=range_speed)
plt.show()
```

![](<.gitbook/assets/image (50).png>)



## Piechart: <a href="#piechart" id="piechart"></a>

Also known as a circle chart or Emma chart.It has been named as pie chart due to its resemblance to a piece of a pie.Usually the data shown in a pie chart are in percentages.

For an example , suppose we are making a dish where ingredients are put in a definite percentage. For an example i say this cake has 70% chocolate and 10% milk and so on.

In \[16]:

```
import matplotlib.pyplot as plt

ingredients = ['chocolate','milk','egg','sugar']
percentage = [70,10,15,5]

plt.pie(percentage,labels=ingredients) #autopct is used to show percentage.
plt.show()
```

![](<.gitbook/assets/image (73).png>)



## Properties of Piechart: <a href="#properties-of-piechart" id="properties-of-piechart"></a>

**autopct : you can use this property to show percentage.**

**colors : You can also use colors to change colors.You need to pass a list of colors to use this property. You can also use color codes instead of their name.**

In \[17]:

```
import matplotlib.pyplot as plt

ingredients = ['chocolate','milk','egg','sugar']
percentage = [12,15,70,21]
clrs = ['Yellow','Orange','Red','Blue']
plt.pie(percentage,labels=ingredients,autopct='%.1f%%',colors = clrs)
plt.show()
```

![](<.gitbook/assets/image (102).png>)



## A Useful Example: <a href="#a-useful-example" id="a-useful-example"></a>

Say if i want to know percentage of types of pokemons in our data set. Pie chart will be right option to choose.

In \[21]:

```
%matplotlib notebook
import matplotlib.pyplot as plt
import pandas as pd

df = pd.read_csv('Pokemon.csv')
count_pokemon_name = df.groupby('Type 1')['Name'].count()
count_pokemon_name = count_pokemon_name.reset_index()

plt.pie(count_pokemon_name['Name'],labels = count_pokemon_name['Type 1'],autopct='%1.1f%%')
plt.show()
```

![](<.gitbook/assets/image (76).png>)



## Stackplot: <a href="#stackplot" id="stackplot"></a>

**Stack Plots are used to visualize multiple linear plots, stacked on top of each other.**

For an example Suppose i have data of how many hours i studied and played for 7 days. This can be show with the help of stackplot.

In \[19]:

```
import matplotlib.pyplot as plt

days = [1,2,3,4,5,6,7]

played_hour = [4,3,2,6,1,5,4]

studied_hour = [7,6,8,0,3,9,7]

plt.stackplot(days,played_hour,studied_hour)

plt.show()
```

As you can see i spent total 11 hours playing and studying the first day. This is how we use stackplot.But it is not quite clear as of now , we can use legend and labels and make this graph much more understandable.

Here labels are more than one so we will be using a list to store all the labels. For example :

In \[20]:

```
%matplotlib notebook
import matplotlib.pyplot as plt

days = [1,2,3,4,5,6,7]

played_hour = [4,3,2,6,1,5,4]

studied_hour = [7,6,8,0,3,9,7]

l = ['Played','Studied']

plt.stackplot(days,played_hour,studied_hour,labels = l)

plt.legend()

plt.show()
```

![](<.gitbook/assets/image (57).png>)

### A Useful Example :&#x20;

{% file src=".gitbook/assets/gas_prices.csv" %}

<figure><img src=".gitbook/assets/image.png" alt=""><figcaption><p>Snapshot of Gas Price Data</p></figcaption></figure>

_**Create a Line chart Comparing all the countries Yearly.**_&#x20;

<details>

<summary>Solution</summary>



</details>

_****_

_****_

_**Congrats !!! You have made it. Now practice all kind of graphs and implement in your datasets. Next topic that we are going to cover is Seaborn.**_

![](<.gitbook/assets/image (70).png>)
