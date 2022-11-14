# Validation In Pandas

You must have once created a password and suddenly a pop up happens. Telling you , your password doesn not match our criterias. These are validations. Validations are really helpful in many cases. Sometimes it may happen, that we need to apply validation scripts on our data , eliminate data not matching these criterias , in a nutshell , We are going to cover applying Validation on our Datasets.

![](<.gitbook/assets/image (118).png>)

```
import pandas as pd

data = pd.read_csv('mydata.csv')
data
```

Out\[1]:

|   | S.No | FS0 Number   | First Name   | Last Name | Store Id | Circle | Code   |
| - | ---- | ------------ | ------------ | --------- | -------- | ------ | ------ |
| 0 | 1    | 733884567$88 | SATHISHRAAJ  | SM        | -13047   | RI     | -13047 |
| 1 | 2    | 8896763523   | G.K.         | Gupta     | 12087    | UP     | 34567  |
| 2 | 7    | 7338848678   | nihal        | SM        | -13047   | KE     | -13047 |
| 3 | 8    | 8890763523   | rahul88jain  | Gupta     | 12087    | JK     | 34567  |
| 4 | 9    | 8890763853   | yogesh.@jain | Gupta     | 12087    | PL     | 34567  |
| 5 | 3    | 6278032123   | Ravi.raj1    | Kumar$    | 11098    | BH     | 23456  |
| 6 | 4    | 6278.098123  | Rlavi        | Kumar     | 11098    | MP     | 23456  |
| 7 | 5    | 8890763599   | rahul        | Gupta     | 12087    | IP     | 34567  |
| 8 | 5    | 8890763523   | rahulk       | Gupta     | 12087    | GH     | 34567  |

So there are lots of things that is wrong with data and we need to fix it. Let's solve each problem step by step.

**Removing Duplicate Data:**

As you can see there are a few duplicate data that we need to remove. Now there is no validation here, but let's first solve it anyway.

We can use drop duplicates here to remove duplicate data.

In \[2]:

```
data = data.drop_duplicates(subset='S.No')
data
```

Out\[2]:

|   | S.No | FS0 Number   | First Name   | Last Name | Store Id | Circle | Code   |
| - | ---- | ------------ | ------------ | --------- | -------- | ------ | ------ |
| 0 | 1    | 733884567$88 | SATHISHRAAJ  | SM        | -13047   | RI     | -13047 |
| 1 | 2    | 8896763523   | G.K.         | Gupta     | 12087    | UP     | 34567  |
| 2 | 7    | 7338848678   | nihal        | SM        | -13047   | KE     | -13047 |
| 3 | 8    | 8890763523   | rahul88jain  | Gupta     | 12087    | JK     | 34567  |
| 4 | 9    | 8890763853   | yogesh.@jain | Gupta     | 12087    | PL     | 34567  |
| 5 | 3    | 6278032123   | Ravi.raj1    | Kumar$    | 11098    | BH     | 23456  |
| 6 | 4    | 6278.098123  | Rlavi        | Kumar     | 11098    | MP     | 23456  |
| 7 | 5    | 8890763599   | rahul        | Gupta     | 12087    | IP     | 34567  |

Before performing validation let us see data types of each column.

In \[3]:

```
data.info()
```

```
<class 'pandas.core.frame.DataFrame'>
Int64Index: 8 entries, 0 to 7
Data columns (total 7 columns):
 #   Column      Non-Null Count  Dtype 
---  ------      --------------  ----- 
 0   S.No        8 non-null      int64 
 1   FS0 Number  8 non-null      object
 2   First Name  8 non-null      object
 3   Last Name   8 non-null      object
 4   Store Id    8 non-null      int64 
 5   Circle      8 non-null      object
 6   Code        8 non-null      int64 
dtypes: int64(3), object(4)
memory usage: 512.0+ bytes
```

As you can see most of them are objects, so we can apply string methods that we have learned in python. Pandas offer numerous string methods in series that we can use to perform Validation.

You can refer this page while applying validation :[Click Here](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.Series.str.casefold.html)

## Validation In Phone Number : <a href="#validation-in-phone-number" id="validation-in-phone-number"></a>

**Validation1** : _**It should be numeric**_\
**Validation2** : _**It should have 10 digits**_\


**Validation1** : _**It should be numeric**_

So, to check if our phone number has only digits in it , we will use series.str.isdigit() method and store its result in a new column.

In \[4]:

```
data['only digit'] = data['FS0 Number'].str.isdigit()
data[['FS0 Number','only digit']]
```

```
C:\Users\abhis\AppData\Local\Temp/ipykernel_7664/1497754001.py:1: SettingWithCopyWarning: 
A value is trying to be set on a copy of a slice from a DataFrame.
Try using .loc[row_indexer,col_indexer] = value instead

See the caveats in the documentation: https://pandas.pydata.org/pandas-docs/stable/user_guide/indexing.html#returning-a-view-versus-a-copy
  data['only digit'] = data['FS0 Number'].str.isdigit()
```

Out\[4]:

|   | FS0 Number   | only digit |
| - | ------------ | ---------- |
| 0 | 733884567$88 | False      |
| 1 | 8896763523   | True       |
| 2 | 7338848678   | True       |
| 3 | 8890763523   | True       |
| 4 | 8890763853   | True       |
| 5 | 6278032123   | True       |
| 6 | 6278.098123  | False      |
| 7 | 8890763599   | True       |

**Validation2** : _**It should have 10 digits**_

So, to check if our phone number has only 10 digits in it , we will use series.str.len() method and store its result in a new column.

In \[5]:

```
data['ten digit'] = data['FS0 Number'].str.len() 
data[['FS0 Number','ten digit']]
```

```
C:\Users\abhis\AppData\Local\Temp/ipykernel_7664/3592959975.py:1: SettingWithCopyWarning: 
A value is trying to be set on a copy of a slice from a DataFrame.
Try using .loc[row_indexer,col_indexer] = value instead

See the caveats in the documentation: https://pandas.pydata.org/pandas-docs/stable/user_guide/indexing.html#returning-a-view-versus-a-copy
  data['ten digit'] = data['FS0 Number'].str.len()
```

Out\[5]:

|   | FS0 Number   | ten digit |
| - | ------------ | --------- |
| 0 | 733884567$88 | 12        |
| 1 | 8896763523   | 10        |
| 2 | 7338848678   | 10        |
| 3 | 8890763523   | 10        |
| 4 | 8890763853   | 10        |
| 5 | 6278032123   | 10        |
| 6 | 6278.098123  | 11        |
| 7 | 8890763599   | 10        |

Now that we have enough information about FS0 Number, we can perform multiple conditions and filter right data. Something like this:

In \[6]:

```
data[['FS0 Number','only digit','ten digit']]
```

Out\[6]:

|   | FS0 Number   | only digit | ten digit |
| - | ------------ | ---------- | --------- |
| 0 | 733884567$88 | False      | 12        |
| 1 | 8896763523   | True       | 10        |
| 2 | 7338848678   | True       | 10        |
| 3 | 8890763523   | True       | 10        |
| 4 | 8890763853   | True       | 10        |
| 5 | 6278032123   | True       | 10        |
| 6 | 6278.098123  | False      | 11        |
| 7 | 8890763599   | True       | 10        |

In \[7]:

```
data = data.loc[(data['only digit']==True) & (data['ten digit']==10)]
data
```

Out\[7]:

|   | S.No | FS0 Number | First Name   | Last Name | Store Id | Circle | Code   | only digit | ten digit |
| - | ---- | ---------- | ------------ | --------- | -------- | ------ | ------ | ---------- | --------- |
| 1 | 2    | 8896763523 | G.K.         | Gupta     | 12087    | UP     | 34567  | True       | 10        |
| 2 | 7    | 7338848678 | nihal        | SM        | -13047   | KE     | -13047 | True       | 10        |
| 3 | 8    | 8890763523 | rahul88jain  | Gupta     | 12087    | JK     | 34567  | True       | 10        |
| 4 | 9    | 8890763853 | yogesh.@jain | Gupta     | 12087    | PL     | 34567  | True       | 10        |
| 5 | 3    | 6278032123 | Ravi.raj1    | Kumar$    | 11098    | BH     | 23456  | True       | 10        |
| 7 | 5    | 8890763599 | rahul        | Gupta     | 12087    | IP     | 34567  | True       | 10        |

Now we can delete temporary columns , as now we do not need them.

In \[8]:

```
data = data.drop(columns = ['only digit','ten digit'])
data
```

Out\[8]:

|   | S.No | FS0 Number | First Name   | Last Name | Store Id | Circle | Code   |
| - | ---- | ---------- | ------------ | --------- | -------- | ------ | ------ |
| 1 | 2    | 8896763523 | G.K.         | Gupta     | 12087    | UP     | 34567  |
| 2 | 7    | 7338848678 | nihal        | SM        | -13047   | KE     | -13047 |
| 3 | 8    | 8890763523 | rahul88jain  | Gupta     | 12087    | JK     | 34567  |
| 4 | 9    | 8890763853 | yogesh.@jain | Gupta     | 12087    | PL     | 34567  |
| 5 | 3    | 6278032123 | Ravi.raj1    | Kumar$    | 11098    | BH     | 23456  |
| 7 | 5    | 8890763599 | rahul        | Gupta     | 12087    | IP     | 34567  |

## A Useful Example : <a href="#a-useful-example" id="a-useful-example"></a>

Suppose we want to keep all the Phone Numbers and eliminate special characters or any non-numeric value , we can use replace method of series.

In \[9]:

```
import pandas as pd

df = pd.read_csv('mydata.csv')
df['FS0 Number'] = df['FS0 Number'].str.replace('[^0-9]','')
df
```

```
C:\Users\abhis\AppData\Local\Temp/ipykernel_7664/3965905300.py:4: FutureWarning: The default value of regex will change from True to False in a future version.
  df['FS0 Number'] = df['FS0 Number'].str.replace('[^0-9]','')
```

Out\[9]:

|   | S.No | FS0 Number  | First Name   | Last Name | Store Id | Circle | Code   |
| - | ---- | ----------- | ------------ | --------- | -------- | ------ | ------ |
| 0 | 1    | 73388456788 | SATHISHRAAJ  | SM        | -13047   | RI     | -13047 |
| 1 | 2    | 8896763523  | G.K.         | Gupta     | 12087    | UP     | 34567  |
| 2 | 7    | 7338848678  | nihal        | SM        | -13047   | KE     | -13047 |
| 3 | 8    | 8890763523  | rahul88jain  | Gupta     | 12087    | JK     | 34567  |
| 4 | 9    | 8890763853  | yogesh.@jain | Gupta     | 12087    | PL     | 34567  |
| 5 | 3    | 6278032123  | Ravi.raj1    | Kumar$    | 11098    | BH     | 23456  |
| 6 | 4    | 6278098123  | Rlavi        | Kumar     | 11098    | MP     | 23456  |
| 7 | 5    | 8890763599  | rahul        | Gupta     | 12087    | IP     | 34567  |
| 8 | 5    | 8890763523  | rahulk       | Gupta     | 12087    | GH     | 3456   |

## Validation In First Name : <a href="#validation-in-first-name" id="validation-in-first-name"></a>

**Validation1** : _**It should have only alphabets and dots are allowed**_

**We need to remove spaces**

first thing that we need to do is to remove useless spaces if there are any in names. By useless space we mean, left and right spaces of names. We can do that by using strip() function.

In \[10]:

```
data['First Name'] = data['First Name'].str.strip()
data
```

Out\[10]:

|   | S.No | FS0 Number | First Name   | Last Name | Store Id | Circle | Code   |
| - | ---- | ---------- | ------------ | --------- | -------- | ------ | ------ |
| 1 | 2    | 8896763523 | G.K.         | Gupta     | 12087    | UP     | 34567  |
| 2 | 7    | 7338848678 | nihal        | SM        | -13047   | KE     | -13047 |
| 3 | 8    | 8890763523 | rahul88jain  | Gupta     | 12087    | JK     | 34567  |
| 4 | 9    | 8890763853 | yogesh.@jain | Gupta     | 12087    | PL     | 34567  |
| 5 | 3    | 6278032123 | Ravi.raj1    | Kumar$    | 11098    | BH     | 23456  |
| 7 | 5    | 8890763599 | rahul        | Gupta     | 12087    | IP     | 34567  |

Second thing is to check if they are alphabets, so we need to create a column to check if they are alphabets or not.

In \[11]:

```
data['check_alpha'] = data['First Name'].str.isalpha()
data
```

Out\[11]:

|   | S.No | FS0 Number | First Name   | Last Name | Store Id | Circle | Code   | check\_alpha |
| - | ---- | ---------- | ------------ | --------- | -------- | ------ | ------ | ------------ |
| 1 | 2    | 8896763523 | G.K.         | Gupta     | 12087    | UP     | 34567  | False        |
| 2 | 7    | 7338848678 | nihal        | SM        | -13047   | KE     | -13047 | True         |
| 3 | 8    | 8890763523 | rahul88jain  | Gupta     | 12087    | JK     | 34567  | False        |
| 4 | 9    | 8890763853 | yogesh.@jain | Gupta     | 12087    | PL     | 34567  | False        |
| 5 | 3    | 6278032123 | Ravi.raj1    | Kumar$    | 11098    | BH     | 23456  | False        |
| 7 | 5    | 8890763599 | rahul        | Gupta     | 12087    | IP     | 34567  | True         |

Now As you can see, First name (G.K.) should be True , but isalpha method won't allow it, so we need to find a workaround .

Why don't we replace (.) and if we replace it and our name falls true in isalpha , it will not be removed.

Now, while replacing , do remember to make a copy of the column and make all changes in it , so that we don't change original data.

In \[12]:

```
data['temp_name'] = data['First Name']
```

In \[13]:

```
data['temp_name'] = data['First Name'].str.replace('.','')
data
```

```
C:\Users\abhis\AppData\Local\Temp/ipykernel_7664/4143232602.py:1: FutureWarning: The default value of regex will change from True to False in a future version. In addition, single character regular expressions will *not* be treated as literal strings when regex=True.
  data['temp_name'] = data['First Name'].str.replace('.','')
```

Out\[13]:

|   | S.No | FS0 Number | First Name   | Last Name | Store Id | Circle | Code   | check\_alpha | temp\_name  |
| - | ---- | ---------- | ------------ | --------- | -------- | ------ | ------ | ------------ | ----------- |
| 1 | 2    | 8896763523 | G.K.         | Gupta     | 12087    | UP     | 34567  | False        | GK          |
| 2 | 7    | 7338848678 | nihal        | SM        | -13047   | KE     | -13047 | True         | nihal       |
| 3 | 8    | 8890763523 | rahul88jain  | Gupta     | 12087    | JK     | 34567  | False        | rahul88jain |
| 4 | 9    | 8890763853 | yogesh.@jain | Gupta     | 12087    | PL     | 34567  | False        | yogesh@jain |
| 5 | 3    | 6278032123 | Ravi.raj1    | Kumar$    | 11098    | BH     | 23456  | False        | Raviraj1    |
| 7 | 5    | 8890763599 | rahul        | Gupta     | 12087    | IP     | 34567  | True         | rahul       |

In \[14]:

```
data['check_alpha'] = data['temp_name'].str.isalpha()
data
```

Out\[14]:

|   | S.No | FS0 Number | First Name   | Last Name | Store Id | Circle | Code   | check\_alpha | temp\_name  |
| - | ---- | ---------- | ------------ | --------- | -------- | ------ | ------ | ------------ | ----------- |
| 1 | 2    | 8896763523 | G.K.         | Gupta     | 12087    | UP     | 34567  | True         | GK          |
| 2 | 7    | 7338848678 | nihal        | SM        | -13047   | KE     | -13047 | True         | nihal       |
| 3 | 8    | 8890763523 | rahul88jain  | Gupta     | 12087    | JK     | 34567  | False        | rahul88jain |
| 4 | 9    | 8890763853 | yogesh.@jain | Gupta     | 12087    | PL     | 34567  | False        | yogesh@jain |
| 5 | 3    | 6278032123 | Ravi.raj1    | Kumar$    | 11098    | BH     | 23456  | False        | Raviraj1    |
| 7 | 5    | 8890763599 | rahul        | Gupta     | 12087    | IP     | 34567  | True         | rahul       |

Now we need to remove data where names also do not fall in validation criteria.

In \[15]:

```
data = data.loc[data['check_alpha']==True]
data
```

Out\[15]:

|   | S.No | FS0 Number | First Name | Last Name | Store Id | Circle | Code   | check\_alpha | temp\_name |
| - | ---- | ---------- | ---------- | --------- | -------- | ------ | ------ | ------------ | ---------- |
| 1 | 2    | 8896763523 | G.K.       | Gupta     | 12087    | UP     | 34567  | True         | GK         |
| 2 | 7    | 7338848678 | nihal      | SM        | -13047   | KE     | -13047 | True         | nihal      |
| 7 | 5    | 8890763599 | rahul      | Gupta     | 12087    | IP     | 34567  | True         | rahul      |

Now we do not need **check\_alpha** and **temp\_name** , so let's remove them

In \[16]:

```
data = data.drop(columns=['check_alpha','temp_name'])
data
```

Out\[16]:

|   | S.No | FS0 Number | First Name | Last Name | Store Id | Circle | Code   |
| - | ---- | ---------- | ---------- | --------- | -------- | ------ | ------ |
| 1 | 2    | 8896763523 | G.K.       | Gupta     | 12087    | UP     | 34567  |
| 2 | 7    | 7338848678 | nihal      | SM        | -13047   | KE     | -13047 |
| 7 | 5    | 8890763599 | rahul      | Gupta     | 12087    | IP     | 34567  |

We can also use title method to capitalize first letter of name.

In \[17]:

```
data['First Name'] = data['First Name'].str.title()
data
```

Out\[17]:

|   | S.No | FS0 Number | First Name | Last Name | Store Id | Circle | Code   |
| - | ---- | ---------- | ---------- | --------- | -------- | ------ | ------ |
| 1 | 2    | 8896763523 | G.K.       | Gupta     | 12087    | UP     | 34567  |
| 2 | 7    | 7338848678 | Nihal      | SM        | -13047   | KE     | -13047 |
| 7 | 5    | 8890763599 | Rahul      | Gupta     | 12087    | IP     | 34567  |

## Validation In Store Id <a href="#validation-in-store-id" id="validation-in-store-id"></a>

In \[ ]:

```
 
```

## Validation In Circle: <a href="#validation-in-circle" id="validation-in-circle"></a>

Our company has already a list of circle , if any circle that is not present in our list we should remove it.

In \[18]:

```
c = ['UP','HP','RE','KP','KE','HH','TR']
```

In \[19]:

```
data = data.loc[data['Circle'].isin(c)]
data
```

Out\[19]:

|   | S.No | FS0 Number | First Name | Last Name | Store Id | Circle | Code   |
| - | ---- | ---------- | ---------- | --------- | -------- | ------ | ------ |
| 1 | 2    | 8896763523 | G.K.       | Gupta     | 12087    | UP     | 34567  |
| 2 | 7    | 7338848678 | Nihal      | SM        | -13047   | KE     | -13047 |

In \[ ]:

```
Let us say , we have a data of city wise sales like below:
```

In \[30]:

```
import pandas as pd

ef = pd.read_csv('city.csv')
print(ef)
```

```
             state           city  total_sales
0            delhi        Gharoli    34533.200
1            delhi  delhi-central    37373.373
2            delhi       Gokalpur     8322.430
3            delhi           delh   976858.430
4            delhi           delh    48483.230
5            delhi   delhi-110034     5757.670
6            delhi        Jaitpur    89786.120
7            delhi       new delh      574.340
8            delhi            del      575.120
9            delhi      Mukandpur    56744.120
10  andhra pradesh          Adoni      300.560
11  andhra pradesh      Amaravati      400.780
12  andhra pradesh      Anantapur      800.980
13  andhra pradesh    Chandragiri      120.450
14  andhra pradesh       Chittoor      345.230
15  andhra pradesh   Dowlaiswaram     1234.670
16  andhra pradesh          Eluru    75464.230
17  andhra pradesh         Guntur      232.400
18  andhra pradesh         Kadapa      343.100
19  andhra pradesh       Kakinada     3432.000
```

Can you spot any problem in data ?

You can see cities mentioned in delhi is not right. There are many irregularities.

In \[28]:

```
sf = ef.loc[ef['state']=='delhi']
sf
```

Out\[28]:

|    | state | city              | total\_sales |
| -- | ----- | ----------------- | ------------ |
| 10 | delhi | Gharoli           | 34533.200    |
| 11 | delhi | delhi-central     | 37373.373    |
| 12 | delhi | Gokalpur          | 8322.430     |
| 13 | delhi | delh              | 976858.430   |
| 14 | delhi | delh              | 48483.230    |
| 15 | delhi | delhi-110034      | 5757.670     |
| 16 | delhi | Jaitpur           | 89786.120    |
| 17 | delhi | new delh          | 574.340      |
| 18 | delhi | del               | 575.120      |
| 19 | delhi | Mukandpur         | 56744.120    |
| 20 | delhi | Mundka            | 4854.230     |
| 21 | delhi | Mitraon           | 574.320      |
| 22 | delhi | Nilothi           | 8766.340     |
| 23 | delhi | Nangloi Jat       | 5868.120     |
| 24 | delhi | Nithari           | 5855.450     |
| 25 | delhi | Neb Sarai         | 5858.450     |
| 26 | delhi | Nangli Sakrawati  | 575.450      |
| 27 | delhi | Pooth Kalan       | 797976.230   |
| 28 | delhi | Pooth Khurd       | 44.340       |
| 29 | delhi | Pul Pehlad        | 123.000      |
| 30 | delhi | Pehlad Pur Bangar | 455.120      |
| 31 | delhi | Qadipur           | 484.230      |
