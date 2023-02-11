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

