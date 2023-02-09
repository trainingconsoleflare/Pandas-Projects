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

