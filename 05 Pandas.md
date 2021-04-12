### Subsetting DataFrame
Use `.loc[]` to select a subest of a dataframe.
The first argument is the label of a row and the second is the label of a column (or list of columns)

```python
# select row labeled 1 and column labeled 'Name'
df.loc[1, 'Name']
```

Here we use a list to select multiple rows and columns
```python
df.loc[1:5, ['Name:Count']]
```

A single column is called a **series**, which is akin to a one dimensional array in NuPy so we can perform arithmetic on it.
```python
df.loc[:, 'Year'] * 2
```

Shorthand for selecting columns
```python
df.loc['Name']
df.loc[['Name','Count']]
```

### Selecting rows using criteria
Suppose we want to look at all the rows where the year is 2016
```python
df_2016 = df.loc[df['Year'] == 2016, :]
```

### Sorting rows
If we wanted to sort out DataFrame by a column 'Count'
```python
sorted_2016 = df_2016.sort_values('Count', ascending = False)
```

### Integer location
`.iloc` works like `.loc` but takes numeric indeces instead of labels.
For example, get the first 5 rows
```python
sorted_2016.iloc[0:5]
```

### Grouping
Group a DataFrame by 'Year' and 'Sex' and compute the most popular name for eache group.

`groupby()` on it's own doesn't return anything useful, so it needs to be combined with an aggregate function.
This aggregate function will be applied to each column of the DataFrame so we can restrict the output by slicing beforehand.
```python
df.groupby('Year')
df.groupby('Year').agg(len)
df[['Year', 'Count']].groupby('Year').agg(len)

# There are shortcuts for common functions like count, sum, and mean.
df[['Year', 'Count']].groupby('Year').count()
```

We can also group by multiple columns.
```python
grouped_df = df.groupby(['Year', 'Sex']).sum()
```
When you group by multiple columns, you'll have multiple labels for each row. 
So when you go to index these new DataFrames you need to enter a tuple to specify the row index.
```python
# specify the row corresponding to females in the year 2000
# and return the value in the 'Names' column
grouped_df.loc[(2000, 'F'), 'Name']
```

### Pivot tables
When grouping by two or more columns a pivot table is often an easier way to present your data.
```python
pd.pivot_table(df,
               index='Year',
               columns='Sex',
               values='Name',
               aggfunc=<your_func_here>)
```

### Apply
`.apply()` takes a function and applies it to every value in a **Series**
```python
names = df['Names']
names.apply(len)
```

### String manipulation
When manipulating strings in a DataFrame it's often faster to use the built in functions `.str`.
```python
names.str.len()

# get last letter of each name
names.str[-1]
```

### Syntax
When lines get long you can wrap the whole expression in parenthesis
and insert new lines before each method call
```python
new_df = (
    df[['Last','Sex','Count']]
    .groupby(['Last', 'Sex'])
    .sum()
)
```
