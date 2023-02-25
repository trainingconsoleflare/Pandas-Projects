# CheatSheet In Pandas

Indexing and slicing in pandas are used to select a specific subset of data from a DataFrame or Series. Here is a cheat sheet for indexing and slicing in pandas:

**Indexing a DataFrame**

| Description                      | Syntax                                   |
| -------------------------------- | ---------------------------------------- |
| Select a single column           | `df['column_name']`                      |
| Select multiple columns          | `df[['column_name_1', 'column_name_2']]` |
| Select a row by label            | `df.loc[label]`                          |
| Select multiple rows by label    | `df.loc[[label_1, label_2]]`             |
| Select a row by integer location | `df.iloc[row_number]`                    |
| Select a scalar value            | `df.at[row, col]` or `df.iat[row, col]`  |

**Slicing a DataFrame**

| Description                 | Syntax                                          |
| --------------------------- | ----------------------------------------------- |
| Select rows by index range  | `df[start:end]` or `df[start:end:step]`         |
| Select rows by label range  | `df.loc[start:end]` or `df.loc[start:end:step]` |
| Select rows by boolean mask | `df[boolean_mask]`                              |

**Indexing a Series**

| Description                        | Syntax                                                 |
| ---------------------------------- | ------------------------------------------------------ |
| Select a single value              | `s[label]` or `s.at[label]`                            |
| Select multiple values             | `s[[label_1, label_2]]` or `s.loc[[label_1, label_2]]` |
| Select a value by integer location | `s.iloc[row_number]`                                   |

**Slicing a Series**

| Description                   | Syntax                                        |
| ----------------------------- | --------------------------------------------- |
| Select values by index range  | `s[start:end]` or `s[start:end:step]`         |
| Select values by label range  | `s.loc[start:end]` or `s.loc[start:end:step]` |
| Select values by boolean mask | `s[boolean_mask]`                             |

Note: In the examples above, `df` and `s` represent a DataFrame and Series object respectively, `label` represents an index label, `row_number` represents a row index number, `start` and `end` represent index labels or integers, and `boolean_mask` represents a boolean Series.

Joining and merging in pandas are used to combine multiple DataFrames into a single DataFrame based on common columns or indexes. Here is a cheat sheet for joining and merging in pandas:

**Joining DataFrames**

| Description | Syntax                                              |
| ----------- | --------------------------------------------------- |
| Inner join  | `pd.merge(df1, df2, on='column_name', how='inner')` |
| Left join   | `pd.merge(df1, df2, on='column_name', how='left')`  |
| Right join  | `pd.merge(df1, df2, on='column_name', how='right')` |
| Outer join  | `pd.merge(df1, df2, on='column_name', how='outer')` |

Note: `df1` and `df2` represent DataFrames to be joined, and `column_name` represents the common column name.

**Merging DataFrames**

| Description                       | Syntax                                                        |
| --------------------------------- | ------------------------------------------------------------- |
| Merge by index                    | `pd.merge(df1, df2, left_index=True, right_index=True)`       |
| Merge on a specific column        | `pd.merge(df1, df2, on='column_name')`                        |
| Merge on multiple columns         | `pd.merge(df1, df2, on=['col_name_1', 'col_name_2'])`         |
| Merge with different column names | `pd.merge(df1, df2, left_on='col1', right_on='col2')`         |
| Merge with a suffix               | `pd.merge(df1, df2, on='column_name', suffixes=['_1', '_2'])` |

Note: `df1` and `df2` represent DataFrames to be merged, and `column_name` represents the common column name.

**Joining and Merging with Duplicate Values**

| Description                     | Syntax                                                                |
| ------------------------------- | --------------------------------------------------------------------- |
| Merge and keep duplicate values | `pd.merge(df1, df2, on='column_name', how='outer', indicator=True)`   |
| Merge and drop duplicate values | `pd.merge(df1, df2, on='column_name', how='outer').drop_duplicates()` |

Note: `df1` and `df2` represent DataFrames to be merged, and `column_name` represents the common column name.

**Concatenating DataFrames**

| Description              | Syntax                          |
| ------------------------ | ------------------------------- |
| Concatenate vertically   | `pd.concat([df1, df2], axis=0)` |
| Concatenate horizontally | `pd.concat([df1, df2], axis=1)` |

Note: `df1` and `df2` represent DataFrames to be concatenated.

### Missing Values In Pandas&#x20;

Missing values in pandas are represented as `NaN` (Not a Number). Dealing with missing data is a common task in data analysis. Here is a cheat sheet for handling missing values in pandas:

**Checking for Missing Values**

| Description                                             | Syntax                   |
| ------------------------------------------------------- | ------------------------ |
| Check if there are any missing values in a DataFrame    | `df.isna().any()`        |
| Check the total number of missing values in a DataFrame | `df.isna().sum()`        |
| Check the percentage of missing values in a DataFrame   | `df.isna().mean() * 100` |

**Dealing with Missing Values**

| Description                                         | Syntax                                                                               |
| --------------------------------------------------- | ------------------------------------------------------------------------------------ |
| Drop rows with missing values                       | `df.dropna()` or `df.dropna(axis=0)`                                                 |
| Drop columns with missing values                    | `df.dropna(axis=1)`                                                                  |
| Fill missing values with a scalar value             | `df.fillna(value)`                                                                   |
| Fill missing values with the previous or next value | `df.fillna(method='ffill')` or `df.fillna(method='bfill')`                           |
| Fill missing values with mean, median, or mode      | `df.fillna(df.mean())` or `df.fillna(df.median())` or `df.fillna(df.mode().iloc[0])` |

Note: `df` represents a DataFrame object.

**Interpolating Missing Values**

| Description                | Syntax                                                  |
| -------------------------- | ------------------------------------------------------- |
| Interpolate missing values | `df.interpolate()` or `df.interpolate(method='linear')` |

Note: `df` represents a DataFrame object.

**Replacing Values**

| Description                | Syntax                                                   |
| -------------------------- | -------------------------------------------------------- |
| Replace a specific value   | `df.replace(value_to_replace, new_value)`                |
| Replace multiple values    | `df.replace([value1, value2], [new_value1, new_value2])` |
| Replace using a dictionary | `df.replace({value1: new_value1, value2: new_value2})`   |

Note: `df` represents a DataFrame object. `value_to_replace`, `new_value`, `value1`, `value2`, `new_value1`, and `new_value2` are scalar values.



### Aggregating Data In Pandas&#x20;

Aggregating data involves computing a summary statistic of a dataset or a group of data. Here is a cheat sheet for aggregating data in pandas:

**Aggregation Functions**

| Description                                | Syntax                       |
| ------------------------------------------ | ---------------------------- |
| Compute the sum of a column                | `df['column_name'].sum()`    |
| Compute the mean of a column               | `df['column_name'].mean()`   |
| Compute the median of a column             | `df['column_name'].median()` |
| Compute the mode of a column               | `df['column_name'].mode()`   |
| Compute the minimum of a column            | `df['column_name'].min()`    |
| Compute the maximum of a column            | `df['column_name'].max()`    |
| Compute the variance of a column           | `df['column_name'].var()`    |
| Compute the standard deviation of a column | `df['column_name'].std()`    |
| Compute the count of a column              | `df['column_name'].count()`  |

Note: `df` represents a DataFrame object.

**Grouping Data**

| Description                    | Syntax                                         |
| ------------------------------ | ---------------------------------------------- |
| Group data by a column         | `df.groupby('column_name')`                    |
| Group data by multiple columns | `df.groupby(['column_name1', 'column_name2'])` |

Note: `df` represents a DataFrame object.

**Aggregating Grouped Data**

| Description                             | Syntax                                                                                  |
| --------------------------------------- | --------------------------------------------------------------------------------------- |
| Aggregate data using a single function  | `df.groupby('column_name').agg(function)`                                               |
| Aggregate data using multiple functions | `df.groupby('column_name').agg([function1, function2])`                                 |
| Aggregate data using a dictionary       | `df.groupby('column_name').agg({'column_name1': function1, 'column_name2': function2})` |

Note: `df` represents a DataFrame object. `column_name` represents the column to group by. `function` represents an aggregation function such as sum, mean, median, etc.

**Pivoting Data**

| Description                                         | Syntax                                                                                                                |
| --------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------- |
| Pivot data using a single index and a single column | `df.pivot(index='index_name', columns='column_name', values='value_name')`                                            |
| Pivot data using multiple indexes and columns       | `df.pivot_table(index=['index_name1', 'index_name2'], columns=['column_name1', 'column_name2'], values='value_name')` |

### Datetime In Pandas

Working with date and time data is a common task in data analysis. Here is a cheat sheet for working with dates and times in pandas:

**Creating a DatetimeIndex**

| Description                                  | Syntax                                                       |
| -------------------------------------------- | ------------------------------------------------------------ |
| Convert a string to a datetime object        | `pd.to_datetime('2010-01-01')`                               |
| Convert a list of strings to a DatetimeIndex | `pd.to_datetime(['2010-01-01', '2010-01-02', '2010-01-03'])` |
| Create a DatetimeIndex from a range of dates | `pd.date_range(start='2010-01-01', end='2010-01-31')`        |

Note: `pd` represents the pandas module.

**Accessing Components of a Datetime**

| Description                     | Syntax                        |
| ------------------------------- | ----------------------------- |
| Access the year of a datetime   | `df['date_column'].dt.year`   |
| Access the month of a datetime  | `df['date_column'].dt.month`  |
| Access the day of a datetime    | `df['date_column'].dt.day`    |
| Access the hour of a datetime   | `df['date_column'].dt.hour`   |
| Access the minute of a datetime | `df['date_column'].dt.minute` |
| Access the second of a datetime | `df['date_column'].dt.second` |

Note: `df` represents a DataFrame object. `date_column` represents the name of the column containing datetime values.

**Resampling Time Series Data**

| Description               | Syntax                            |
| ------------------------- | --------------------------------- |
| Resample time series data | `df.resample(rule).agg(function)` |

Note: `df` represents a DataFrame object. `rule` represents the resampling frequency, such as 'D' for daily or 'M' for monthly. `function` represents an aggregation function, such as 'mean' or 'sum'.

**Shifting Dates**

| Description                     | Syntax                               |
| ------------------------------- | ------------------------------------ |
| Shift dates forward or backward | `df['date_column'].shift(periods=n)` |

Note: `df` represents a DataFrame object. `date_column` represents the name of the column containing datetime values. `n` represents the number of periods to shift the dates by.

**Rolling Windows**

| Description              | Syntax                                              |
| ------------------------ | --------------------------------------------------- |
| Compute a rolling window | `df['column_name'].rolling(window=n).agg(function)` |

Note: `df` represents a DataFrame object. `column_name` represents the name of the column to compute the rolling window on. `n` represents the size of the rolling window. `function` represents an aggregation function, such as 'mean' or 'sum'.

These are some common methods for working with dates and times in pandas, but there are many more methods and options available.

### Filtering In Pandas

Filtering and grouping data are common tasks in data analysis. Here is a cheat sheet for working with filtering and grouping in pandas:

**Filtering Data**

| Description                              | Syntax                                                              |
| ---------------------------------------- | ------------------------------------------------------------------- |
| Filter rows based on a condition         | `df[df['column_name'] < value]`                                     |
| Filter rows based on multiple conditions | `df[(df['column_name1'] < value1) & (df['column_name2'] > value2)]` |
| Filter rows based on a substring         | `df[df['column_name'].str.contains('substring')]`                   |
| Filter rows based on missing values      | `df[df['column_name'].isna()]` or `df[df['column_name'].notna()]`   |

Note: `df` represents a DataFrame object. `column_name` represents the name of the column to filter on. `value` represents the value to filter by.

**Grouping Data**

| Description                                     | Syntax                                                              |
| ----------------------------------------------- | ------------------------------------------------------------------- |
| Group by a single column                        | `df.groupby('column_name').agg(function)`                           |
| Group by multiple columns                       | `df.groupby(['column_name1', 'column_name2']).agg(function)`        |
| Apply multiple aggregation functions to a group | `df.groupby('column_name').agg(['mean', 'max', 'min'])`             |
| Group by time intervals                         | `df.groupby(pd.Grouper(key='date_column', freq='D')).agg(function)` |

Note: `function` represents an aggregation function, such as 'mean' or 'sum'. `pd.Grouper` is a pandas object for grouping time intervals. `key` represents the name of the column containing datetime values. `freq` represents the frequency of the time interval, such as 'D' for daily or 'M' for monthly.

These are some common methods for working with filtering and grouping in pandas, but there are many more methods and options available.

Here's a quick cheatsheet for some common visualization techniques using the Matplotlib library in Python:

### Importing the library

```python
import matplotlib.pyplot as plt
```

### Line plot

```python
plt.plot(x, y)
plt.xlabel('X Label')
plt.ylabel('Y Label')
plt.title('Title')
plt.show()
```

### Scatter plot

```python
plt.scatter(x, y)
plt.xlabel('X Label')
plt.ylabel('Y Label')
plt.title('Title')
plt.show()
```

### Bar plot

```python
plt.bar(x, height)
plt.xlabel('X Label')
plt.ylabel('Y Label')
plt.title('Title')
plt.show()
```

### Histogram

```python
plt.hist(x, bins=10)
plt.xlabel('X Label')
plt.ylabel('Y Label')
plt.title('Title')
plt.show()
```

### Box plot

```python
plt.boxplot(x)
plt.xlabel('X Label')
plt.ylabel('Y Label')
plt.title('Title')
plt.show()
```

### Pie chart

```python
plt.pie(x, labels=labels)
plt.title('Title')
plt.show()
```

### Heatmap

```python
plt.imshow(data, cmap='coolwarm')
plt.colorbar()
plt.title('Title')
plt.show()
```

Here's a quick cheatsheet for some common visualization techniques using the Seaborn library in Python:

### Importing the library

```python
import seaborn as sns
```

### Line plot

```python
sns.lineplot(x=x, y=y, hue=hue, style=style, markers=True)
sns.set_style("whitegrid")
sns.despine(left=True)
plt.xlabel('X Label')
plt.ylabel('Y Label')
plt.title('Title')
plt.show()
```

### Scatter plot

```python
sns.scatterplot(x=x, y=y, hue=hue, style=style, markers=True)
sns.set_style("whitegrid")
sns.despine(left=True)
plt.xlabel('X Label')
plt.ylabel('Y Label')
plt.title('Title')
plt.show()
```

### Bar plot

```python
sns.barplot(x=x, y=y, hue=hue)
sns.set_style("whitegrid")
sns.despine(left=True)
plt.xlabel('X Label')
plt.ylabel('Y Label')
plt.title('Title')
plt.show()
```

### Histogram

```python
sns.histplot(x, kde=True)
sns.set_style("whitegrid")
sns.despine(left=True)
plt.xlabel('X Label')
plt.ylabel('Y Label')
plt.title('Title')
plt.show()
```

### Box plot

```python
sns.boxplot(x=x, y=y, hue=hue)
sns.set_style("whitegrid")
sns.despine(left=True)
plt.xlabel('X Label')
plt.ylabel('Y Label')
plt.title('Title')
plt.show()
```

### Heatmap

```python
sns.heatmap(data, cmap='coolwarm')
plt.title('Title')
plt.show()
```

### Pair plot

```python
sns.pairplot(data, hue=hue)
plt.title('Title')
plt.show()
```
