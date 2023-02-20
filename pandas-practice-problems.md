# Pandas Practice Problems

### Download DataSet :&#x20;

{% file src=".gitbook/assets/PracticeData.csv" %}

1. **`Given a dataframe containing the following columns: "Name", "Age", "City", and "Salary". How do you select all rows where the age is greater than 30 and the salary is greater than 50000?`**

<details>

<summary>Solution</summary>

```python
df[(df['Age'] > 30) & (df['Salary'] > 50000)]
```

</details>

2. **`How do you calculate the mean, median, and standard deviation of the column "Salary" in the dataframe?`**

<details>

<summary>Solution</summary>

```python
mean = df['Salary'].mean()
median = df['Salary'].median()
standard_deviation = df['Salary'].std()
```

</details>

3. **`Given a dataframe, how do you sort its values by the "Age" column in descending order?`**

<details>

<summary>Solution</summary>

```python
df.dropna(axis=0, how='any')
```

</details>

5. **`How do you group the dataframe by the "City" column and calculate the mean of the "Salary" column for each city?`**

<details>

<summary>Solution</summary>

```python
df.groupby('City')['Salary'].mean()
```

</details>

6. **`Given a dataframe containing the following columns: "Name", "Age", "City", and "Salary". How do you select all rows where the name starts with 'J'?`**

<details>

<summary>Solution</summary>

```python
df[df['Name'].str.startswith('J')]
```

</details>

8. **`How do you drop all duplicate rows in a dataframe?`**

<details>

<summary>Solution</summary>

```python
df.drop_duplicates(keep='first', inplace=True)
```

</details>

9.**`How do you rename the columns in a dataframe?`**

<details>

<summary>Solution</summary>

```python
df.rename(columns={'Old_Column_Name':'New_Column_Name'}, inplace=True)
```

</details>

10. **`How do you count the number of unique values in a column?`**

<details>

<summary>Solution</summary>

```python
df['City'].nunique()
```

</details>

11. **`How do you merge two dataframes on a specific column?`**

<details>

<summary>Solution</summary>

```python

merged_df = pd.merge(df1, df2, on='Column_Name')

```

</details>

12. **`How do you create a pivot table from a dataframe?`**

<details>

<summary>Solution</summary>

```python
pivot_table = df.pivot_table(index='Column1', columns='Column2', values='Column3')

```

</details>

13. **`How do you select the first 5 rows of a dataframe?`**

<details>

<summary>Solution</summary>

```python
df.head(5)

```

</details>

14. **`How do you select the last 5 rows of a dataframe?`**

<details>

<summary>Solution</summary>

```python
df.tail(5)

```

</details>

15. **`How do you select a specific column from a dataframe and make it into a new dataframe?`**

<details>

<summary>Solution</summary>

```python
new_df = df[['Column_Name']]

```

</details>

16. **`How do you concatenate two dataframes along the rows?`**

<details>

<summary>Solution</summary>

```python
concatenated_df = pd.concat([df1, df2], axis=0)

```

</details>

17. **`How do you find the maximum and minimum values of a column in a dataframe?`**

<details>

<summary>Solution</summary>

```python
max_value = df['Column_Name'].max()
min_value = df['Column_Name'].min()

```

</details>

18. **`How do you calculate the cumulative sum of a column in a dataframe?`**

<details>

<summary>Solution</summary>

```python
df['Column_Name'].cumsum()

```

</details>

19. **`How do you find the unique values of a column in a dataframe?`**

<details>

<summary>Solution</summary>

```python
df['Column_Name'].unique()

```

</details>

20. **`How do you drop a specific column from a dataframe?`**

<details>

<summary>Solution</summary>

```python

df.drop('Column_Name', axis=1, inplace=True)

```

</details>

21. **`How do you find the number of missing values in each column of a dataframe?`**

<details>

<summary>Solution</summary>

```python
df.isnull().sum()

```

</details>

22. **`How do you fill missing values in a specific column with a specific value?`**

<details>

<summary>Solution</summary>

```python
df['Column_Name'].fillna(value, inplace=True)

```

</details>

23. **`How do you drop all rows with more than two missing values in the dataframe?`**

<details>

<summary>Solution</summary>

```python
Solution:
df.dropna(thresh=len(df) - 2, axis=0, inplace=True)

```

</details>

Let's Do some Data Cleaning and Analysis on the Practice Data.

### Data Cleaning :&#x20;

Although there are many steps to clean , but lets start with dropping duplicate rows.

<details>

<summary>Solution</summary>

```python
df = df.drop_duplicates()
```

</details>

### Fill missing values :&#x20;

Find a way to fill missing values in Columns with Reasonable values.

<details>

<summary>Solution</summary>

```python
df['Name'].fillna(df['Name'].mode()[0], inplace=True)
df['Age'].fillna(df['Age'].mean(), inplace=True)
df['City'].fillna(df['City'].mode()[0], inplace=True)
df['Salary'].fillna(df['Salary'].mean(), inplace=True)
```

</details>

### Exploratory Data Analysis (EDA) :&#x20;

Generate a Statistical Summary.

<details>

<summary>Solution</summary>

```python
print(df.describe())
```

</details>

### Create histograms for each numeric column :&#x20;

<details>

<summary>Solution</summary>

```python
df.hist()
plt.show()
```

</details>

### Create a bar chart to compare the distribution of salary across different cities :&#x20;

<details>

<summary>Solution</summary>

```python
grouped_data = df.groupby('City')['Salary'].mean().reset_index()
plt.bar(grouped_data['City'], grouped_data['Salary'])
plt.xlabel('City')
plt.ylabel('Average Salary')
plt.show()
```

</details>

### Group the data by city and calculate the mean salary for each city :&#x20;

<details>

<summary>Solution</summary>

```python
city_group = df.groupby('City')
mean_salary_by_city = city_group['Salary'].mean().reset_index()
```

</details>

### Plot the mean salary for each city using a bar plot :&#x20;

<details>

<summary>Solution</summary>

```python
plt.bar(mean_salary_by_city['City'], mean_salary_by_city['Salary'])
plt.xlabel("City")
plt.ylabel("Mean Salary")
plt.title("Mean Salary by City")
plt.xticks(rotation=45)
plt.show()
```

</details>

### Plot a scatter plot to visualize the relationship between Age and Salary :&#x20;

<details>

<summary>Solution</summary>

```python
plt.scatter(df['Age'], df['Salary'])
plt.xlabel("Age")
plt.ylabel("Salary")
plt.title("Relationship between Age and Salary")
plt.show()
```

</details>

### Find the highest-paid person in each city :&#x20;

<details>

<summary>Solution</summary>

```python
top_paid_by_city = city_group['Salary'].max().reset_index()
print("The highest-paid person in each city:")
print(top_paid_by_city)
```

</details>

### Find the youngest and oldest person in the data :&#x20;

<details>

<summary>Solution</summary>

```python
min_age = df['Age'].min()
max_age = df['Age'].max()
print("The youngest person in the data is", df.loc[df['Age'] == min_age, 'Name'].iloc[0], "with an age of", min_age)
print("The oldest person in the data is", df.loc[df['Age'] == max_age, 'Name'].iloc[0], "with an age of", max_age)
```

</details>

## Group the data by age group and city and calculate the mean salary for each group and city

`age_group = df.groupby(['Age Group', 'City']) mean_salary_by_age_group_and_city = age_group['Salary'].mean().reset_index()`

## Pivot the table to display the mean salary for each age group and city

`pivot_table = pd.pivot_table(mean_salary_by_age_group_and_city, values='Salary', index='Age Group', columns='City')`&#x20;

`print("Mean Salary by Age Group and City:")`&#x20;

`print(pivot_table)`

## Plot the mean salary for each age group and city using a heatmap

`sns.heatmap(pivot_table, annot=True, cmap='Blues')`&#x20;

`plt.xlabel("City")`&#x20;

`plt.ylabel("Age Group")`&#x20;

`plt.title("Mean Salary by Age Group and City")`&#x20;

`plt.show()`

## Calculate the top 5 most common names in the data

`top_names = df['Name'].value_counts().head()`&#x20;

`print("The top 5 most common names in the data:")`&#x20;

`print(top_names)`

## Create a new column to indicate whether a person's age is below or above the average age

`mean_age = df['Age'].mean()`&#x20;

`df['Age Above Average'] = np.where(df['Age']>=mean_age, 1, 0)`

## Group the data by age above average and city and calculate the median salary for each group and city

`age_above_average_group = df.groupby(['Age Above Average', 'City'])`&#x20;

`median_salary_by_age_above_avg_and_city=age_above_average_group['Salary'].median().reset_index()`

## Pivot the table to display the median salary for each age above average group and city

`pivot_table2 = pd.pivot_table(median_salary_by_age_above_average_and_city, values='Salary', index='Age Above Average', columns='City')`&#x20;

`print("Median Salary by Age Above Average and City:")`&#x20;

`print(pivot_table2)`

## Plot the median salary for each age above average group and city using a stacked bar chart

`pivot_table2.plot(kind='bar', stacked=True)`&#x20;

`plt.xlabel("Age Above Average")`&#x20;

`plt.ylabel("Median Salary")`&#x20;

`plt.title("Median Salary by Age Above Average and City")`&#x20;

`plt.show()`
