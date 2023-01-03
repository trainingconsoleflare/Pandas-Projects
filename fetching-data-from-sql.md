# Fetching Data From SQL

```python
import pandas as pd
import pyodbc

connection = pyodbc.connect(
        driver = '{ODBC Driver 17 for SQL Server}',
        host = 'LAPTOP-PNUT53AO\SQLEXPRESS',
        database = 'sales',
        trusted_connection='yes',

)


print('connection is established')

sql_query = 'select * from prod'

df = pd.read_sql(sql=sql_query,con=connection)
print(df)


```
