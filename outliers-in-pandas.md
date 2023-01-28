# Outliers In Pandas

![](<.gitbook/assets/image (32).png>)

## Introduction To Outliers <a href="#introduction-to-outliers" id="introduction-to-outliers"></a>

_**In statistics, an outlier is a data point that differs significantly from other observations.**_

![](<.gitbook/assets/image (26).png>)



To put it more simply , Values that **lies outside** from most of the other values are outliers.

To understand it more simply , let us take an example.

Let's say we have a data of Math scores of students of a class, Something like this:

In \[2]:

```
students = ['Abhishek','Raj','Deepak','Neha','Ramesh','Aaradhya','Mahesh','Sam']

scores = [25,29,3,32,85,33,27,28]
```

To filter out outliers , we must convert it in a line chart.

In \[5]:

```
import pandas as pd
import matplotlib.pyplot as plt

students = ['Abhishek','Raj','Deepak','Neha','Ramesh','Ajay','Mahesh','Sam']

scores = [25,29,3,32,85,33,27,28]

plt.scatter(students,scores)

plt.show()
```

![](<.gitbook/assets/image (56).png>)

Now as per our definition of outliers , Students that are outliers here are **Deepak with 3 marks** and **Ramesh with 85 marks**.

## Why Outliers are Important and should not be ignored ? <a href="#why-outliers-are-important-and-should-not-be-ignored" id="why-outliers-are-important-and-should-not-be-ignored"></a>

Outliers are unusual values in your dataset, and they can distort statistical analyses and violate their assumptions. Unfortunately, all analysts will confront outliers and be forced to make decisions about what to do with them. Given the problems they can cause, you might think that it’s best to remove them from your data.

## So let us deal with Outliers : <a href="#so-let-us-deal-with-outliers" id="so-let-us-deal-with-outliers"></a>

Now that we have understood what are outliers , there are certain things to know in detail before we deep dive into its complexities:

### Mean and Median and Mode and Range: <a href="#mean-and-median-and-mode-and-range" id="mean-and-median-and-mode-and-range"></a>

As we already know what are mean , median or mode , still for reference go through below image :&#x20;

![](<.gitbook/assets/image (98).png>)

## Normal Distribution <a href="#normal-distribution" id="normal-distribution"></a>

Early statisticians noticed the same shape coming up over and over again in different distributions—so they named it the normal distribution.

![](<.gitbook/assets/image (92).png>)

Let us assume , you have data of heights of people , Now they can either be too short or too tall or falls in average height category. And this is how statisticians found the same shape over and over again because this is how most of distributions would be.

### **Normal distributions have the following features:**

1. **Symmetric bell shape**
2. **Mean and Median are equal. Both located at the center of the distribution.**
3. **68(Approx.) percent of the data falls within 1 standard deviation of the mean**
4. **95(Approx.) percent of the data falls within 2 standard deviations of the mean**
5. **99.7(Approx.) percent of the data falls within 3 standard deviations of the mean**

## Standard Deviation <a href="#standard-deviation" id="standard-deviation"></a>

_**Deviation just means how far are you from the normal**_

_**A standard deviation is a measure of how dispersed the data is in relation to the mean. Low standard deviation means data are clustered around the mean, and high standard deviation indicates data are more spread out.**_

Imagine you have measured the height of dogs in millimeters and it looks something like this : &#x20;

![](<.gitbook/assets/image (96).png>)

The heights (at the shoulders) are: 600mm, 470mm, 170mm, 430mm and 300mm.

Find out the Mean, the Variance, and the Standard Deviation.

Your first step is to find the Mean:

In \[1]:

```
Mean=(600 + 470 + 170 + 430 + 300)/5
print(Mean)
```

```
394.0
```

so the mean (average) height is 394 mm. Let's plot this on the chart: &#x20;

![](<.gitbook/assets/image (101).png>)

Now we calculate each dog's difference from the Mean: &#x20;

![](<.gitbook/assets/image (31).png>)

To calculate the Variance, take each difference, square it, and then average the result:

In \[5]:

```
variance =( 206**2 + 76**2 + (-224)**2 + 36**2 + (-94)**2 ) / 5
print(variance)
```

```
21704.0
```

So the Variance is 21,704

And the Standard Deviation is just the square root of Variance, so:

In \[8]:

```
import math
standard_deviation = math.sqrt(variance)

print(round(standard_deviation))
```

```
147
```

And the good thing about the Standard Deviation is that it is useful. Now we can show which heights are within one Standard Deviation (147mm) of the Mean: &#x20;

![](<.gitbook/assets/image (3) (1).png>)

So, using the Standard Deviation we have a "standard" way of knowing what is normal, and what is extra large or extra small.

Rottweilers are tall dogs. And Dachshunds are a bit short, right?&#x20;

## Quartile in Pandas: <a href="#quartile-in-pandas" id="quartile-in-pandas"></a>

![](<.gitbook/assets/image (22) (1).png>)



**So, when we talk about quartiles, we are dividing the data set into 4 quarters.**

> **Each quarter is 25% of the total number of data points.**
>
> > _**The first quartile or Q1 :**_ Value in the data set such that 25% of the data points are less than this value and 75% of the data set is greater than this value.
> >
> > > _**The second quartile or Q2 :**_ Value in the data set such that 50% of the data points are less than this value and 50% of the data set are greater than this value.
> > >
> > > > _**The third quartile or Q3 :**_ Value such that 75% of the values are less than this value and 25% of the values are greater than this value.&#x20;

![](<.gitbook/assets/image (17).png>)

## Interquartile Range : <a href="#interquartile-range" id="interquartile-range"></a>

The term Interquartile Range (IQR) refers to the difference between Q3 and Q1 (IQR = Q3 – Q1).

## Box and Whisker Plot:  <a href="#box-and-whisker-plot" id="box-and-whisker-plot"></a>

![](<.gitbook/assets/image (80).png>)

Box plot diagram also termed as Whisker’s plot is a graphical method typically depicted by quartiles and inter quartiles that helps in defining the upper limit and lower limit beyond which any data lying will be considered as outliers. The very purpose of this diagram is to identify outliers and discard it from the data series before making any further observation so that the conclusion made from the study gives more accurate results not influenced by any extremes or abnormal values.

## Let's Find Outliers: <a href="#lets-find-outliers" id="lets-find-outliers"></a>

We have already dealt many times with **Walmart** Data set. Let's try to find outliers in Weekly\_Sales.

In \[2]:

```
import pandas as pd

wlmrt = pd.read_csv('walmart.csv')

wlmrt
```

Out\[2]:

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

## Let's Find max and min of the data: <a href="#lets-find-max-and-min-of-the-data" id="lets-find-max-and-min-of-the-data"></a>

In \[3]:

```
mx = wlmrt['Weekly_Sales'].max()
mn = wlmrt['Weekly_Sales'].min()
print(mx)
print(mn)
```

```
693099.36
-4988.94
```

We will use this later in finding outliers.

## Lower Extreme and Upper Extreme: <a href="#lower-extreme-and-upper-extreme" id="lower-extreme-and-upper-extreme"></a>

Outliers are data points that are more extreme than than **Q1 - 1.5 \* IQR** or **Q3 + 1.5 \* IQR**.

Lower Extreme : Q1 - 1.5 \* IQR

Upper Extreme : Q3 + 1.5 \* IQR

## Let's Find Q1 and Q3 : <a href="#lets-find-q1-and-q3" id="lets-find-q1-and-q3"></a>

To Find Lower extreme , we must find **Q1** and **Q3**. We will use percentile method of numpy to calculate quartiles.

In \[4]:

```
import numpy as np

q1,q3 = np.percentile(wlmrt['Weekly_Sales'],[25,75])

print(q1,q3)
```

```
2079.33 20245.745000000003
```

## Let's Find Interquartile Range (IQR): <a href="#lets-find-interquartile-range-iqr" id="lets-find-interquartile-range-iqr"></a>

In \[5]:

```
iqr = q3-q1
iqr
```

Out\[5]:

```
18166.415
```

## Let's Find Lower Extreme and Upper Extreme: <a href="#lets-find-lower-extreme-and-upper-extreme" id="lets-find-lower-extreme-and-upper-extreme"></a>

In \[6]:

```
lx = q1 - 1.5 * iqr
ux = q3 + 1.5 * iqr
print('Lower Extreme : ',lx)
print('Upper Extreme : ',ux)
```

```
Lower Extreme :  -25170.292500000003
Upper Extreme :  47495.36750000001
```

To find outliers beyond lower extreme our lower extreme must be greater than minimum value of dataset.

In \[7]:

```
outliers_present = lx>mn
outliers_present
```

Out\[7]:

```
False
```

Hence there are no outliers beyond lower extreme.

To find outliers beyond upper extreme our upper extreme must be smaller than maximum value of dataset.

In \[8]:

```
outliers_present = ux<mx
outliers_present
```

Out\[8]:

```
True
```

Hence there are outliers present beyond upper extreme.

## No Outliers: <a href="#no-outliers" id="no-outliers"></a>

So we must remove outliers and doing that is pretty simple!!

In \[9]:

```
no_outlier = wlmrt.loc[(wlmrt['Weekly_Sales']<ux) & (wlmrt['Weekly_Sales']>lx)]
no_outlier
```

Out\[9]:

|        | Store | Type | Department | Weekly\_Sales | Is\_Holiday | Temperature | Fuel\_Price | Unemployment | Date1      | Date2      |
| ------ | ----- | ---- | ---------- | ------------- | ----------- | ----------- | ----------- | ------------ | ---------- | ---------- |
| 1      | 1     | A    | 1          | 16333.14      | False       | 80.91       | 2.669       | 7.787        | 07-03-2010 | 07-04-2010 |
| 2      | 1     | A    | 1          | 19403.54      | False       | 46.63       | 2.561       | 8.106        | 26-02-2012 | 27-02-2012 |
| 3      | 1     | A    | 1          | 22517.56      | False       | 49.27       | 2.708       | 7.838        | 12-03-2011 | 12-03-2012 |
| 4      | 1     | A    | 1          | 17596.96      | False       | 66.32       | 2.808       | 7.808        | 16-04-2010 | 16-04-2010 |
| 5      | 1     | A    | 1          | 16555.11      | False       | 67.41       | 2.780       | 7.808        | 30-04-2010 | 30-04-2010 |
| ...    | ...   | ...  | ...        | ...           | ...         | ...         | ...         | ...          | ...        | ...        |
| 282446 | 45    | B    | 98         | 467.30        | False       | 65.32       | 4.038       | 8.684        | 21-09-2012 | 21-09-2012 |
| 282447 | 45    | B    | 98         | 508.37        | False       | 64.88       | 3.997       | 8.684        | 28-09-2012 | 28-09-2012 |
| 282448 | 45    | B    | 98         | 770.86        | True        | 37.00       | 3.640       | 8.424        | 02-10-2012 | 02-10-2012 |
| 282449 | 45    | B    | 98         | 727.49        | False       | 78.65       | 3.722       | 8.684        | 08-10-2012 | 08-10-2012 |
| 282450 | 45    | B    | 98         | 893.60        | False       | 61.24       | 3.889       | 8.567        | 05-11-2012 | 05-11-2012 |

258762 rows × 10 columns

![](<.gitbook/assets/image (9) (1).png>)
