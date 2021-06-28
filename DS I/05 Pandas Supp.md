### Querying, Filtering, Sampling

| Pandas | Description |
|---------|------------|
| df.shape()| Get the dimensions of a data frame
| df.head()| Get the first rows of a data frame
| df.iloc[:9]| Get the first 8 rows of a data frame
|df.query('col1 == 1 & col2 == 1') | Return all the rows where col1 and col2 equal 1
| df[(df.col1 == 1) & (df.col2 == 1)] | Same as above
| df[ ['col1', 'col2'] ] | Select columns 1 and 2
| df.loc[:, 'col1:col3'] | Select columns 1 through 3
| df.drop(cols_to_drop, axis=1) | Remove columns
| df[ ['col1'] ].drop_duplicates() | Return DataFrame with duplicate rows removed
| df[ ['col1', 'col2'] ].drop_duplicates() | Remove duplicate rows from two columns
| df.sample(n=10) | Take a random sample from DataFrame
| df.sample(frac=0.5) | Take a random 50% sample from DataFrame

### Sorting
| Pandas | Description |
|---------|------------|
| df.sort_values(['col1', 'col2']) | Sort DataFrame by col1 then by col2
| df.sort_values('col1', ascending=False) | Sort DataFrame in reverse order

### Transforming
| Pandas | Description |
|--------|-------------|
| df.rename(columns={'col1': 'col_one'})['col_one'] | Rename a column and select it
| df.rename(columns{'col1': 'col_one'}) | Rename col1
| df.assign(c=df['a']-df['b']) | Create new column c = a-b

### Grouping and summarizing
| Pandas | Description |
|--------|-------------|
| df.describe() | Get summary statistics
| df.groupby('col1') | Group DataFrame by col1
| df.groupby('col1').agg({'col1': 'mean'}) | Group by col1 and return the mean
| df.groupby('col1').sum() | Group by col1 and take the sum

### Selecting
Select multiple columns `df[['a', 'c']]`
Conditional selection of columns
- `df.query('a <= b')`
- `df[df['a'] <= df['b']`
- `df.loc[df['a'] <= df['b']]`
- `df[df['A'] == 'Dinner']`
- `df[(df['A'] == 'Dinner') & (df['B'] > 5)]`
- `df[df['col1'].notna()]` Select non NULL values from column 1

### Viewing data
- `df.index` and `df.columns` to view indeces and columns
- `df.describe()` for summary statistics
- `df.sort_values(by='B')`

### Manipulation
- `df.eval('a + b')` Performing an operation on columns 
- `df.assign(new_col = df['a']/df['b']` Create new column
- `pd.concat([df1, df2])` rbind
- `pd.concat([df1, df2], axis=1)` cbind
- `pivot_table(df, values, index, columns)` Create a new DataFrame with rows `index` and columns `column` and populate with the data from the desired column `values`

### Categorical data
```python
# Create a DataFrame
df = pd.DataFrame(
	{'id': [1, 2, 3, 4, 5, 6],
	'raw_grade': ['a', 'b', 'b', 'a', 'a', 'e']}

# Convert raw_grade to categorical
df['grade'] = df['raw_grade'].astype('category')

# Rename the categories
df['grade'].cat.categories = ['very good', 'good', 'very bad']

# Reorder the categories and add missing ones
df['grade'].cat.set_categories(
	['very bad', 'bad', 'medium', 'good', 'very good']
)

# Sorting is done on the order of the categories not by lexical order.
df.sort_values(by='grade')

# Grouping by category can show category totals, including empty ones
df.groupby('grade').size()
```


### Column selection, insertion and deletion
```python
# Select a column as a Series
df['A']

# Select a column as a DataFrame
df[['A']]

# Select a list of columns
df[ ['A', 'B'] ]

# Select multiple columns using .loc
df.loc[:, ['A', 'B']]

# Swap column values
df.loc[:, ['B', 'A']] = df[ ['A', 'B'] ].to_numpy()

# Delete column
del df['C']

# Insert a new column (in the second column, named 'bar',
# with values of some ndarray in this case equal to our 
# column A).
df.insert(1, 'bar', df['A'])

# Select first 5 rows
df[:5]
```

### Create new columns
Python's recreation of R's `mutate`
```python
# Create new feature 'sepal_ratio'
iris.assign(sepal_ratio=iris['SepalWidth'] / iris['SepalLength'])

# Create column using lambda function
iris.assign(sepal_ratio=lambda x: (x['SepalWidth'] / x['SepalLength']))

# Using multiple chains of assign
(
	iris.query('SepalLength > 5')
	.assign(
		SepalRatio=lambda x: x.SepalWidth / x.SepalLength,
		PetalRatio=lamda x: x.PetalWidth / x.PetalLength,
	)
	.plot(kind='scatter', x='SepalRatio', y='PetalRatio')
)

# Referencing previous created columns
df.assign(C=lambda x: x['A'] + x['B'],
		  D=lambda x: x['A'] + x['C'])
```

### Basic functionality
```python
# Get axis dimensions
df.shape()

# Rename columns
df.columns = ['a', 'b', 'c']

# Check if two DataFrames are equal
# Note row index need to be in same order
(df + df).equals(df * 2)
```


### Imputation
```python
# Look at missing data from revenue column
revenue = movies_df['revenue_millions']

# Calculate the mean
revenue_mean = revenue.mean()

# Fill missing values with na
# inplace=True means our original DataFrame (movies_df)
# will also change.
revenue.fillna(revenue_mean, inplace=True)
```