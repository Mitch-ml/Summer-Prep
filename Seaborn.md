### Quantitative Data

For quantitiative data, commonly used visualization techniques are *histograms, box plots,* and *scatter plots*.

**Histograms**

Use seaborns `distplot` to view a histogram

```python
import seaborn as sns
sns.set()

sns.distplot(df['age'])
```

![sns.distplot(df['age'])](https://www.textbook.ds100.org/_images/viz_quantitative_7_0.png)

We can also add a rugplot, which allows us to view each individual point on the x-axis.

```python
sns.distplot(df['age'], rug=True)
```

![rugplot](https://www.textbook.ds100.org/_images/viz_quantitative_9_0.png)

We can also plot just the distribution, without the distribution curve, and add more bins.

```python
sns.distplot(df['age'], kde=False, bins=30)
```

![histogram without kde](https://www.textbook.ds100.org/_images/viz_quantitative_11_0.png)

**Box Plots**

Box plots help visualize the inter quartile range, which allows for quick understanding of where most of the data lies, in addition to easy observation of outliers. 

Specifically, the edges of the box represent the 25th and 75th percentiles. The line within the box is the median, or 50th percentile. The whiskers extend to capture the remaining data except for outliers.

```python
sns.boxplot(x='fare', data=df)
```

![fare boxplot](https://www.textbook.ds100.org/_images/viz_quantitative_13_0.png)

The Inter-Quartile Range (IQR) is the 75th percentile - 25th percentile. We use this number to calculate the outliers, defined as 75th + 1.5 X IQR and 25th - 1.5 X IQR.

Boxplots are often easier to understand when the data is split into different categories.

```python
# fare (numerical) on the x-axis,
# who (nominal) on the y-axis
sns.boxplot(x='fare', y='who', data=df)
```

![boxplot by category](https://www.textbook.ds100.org/_images/viz_quantitative_19_0.png)


**Scatter Plots**

Scatter plots are used to compare two quantitative variables. 

```python
sns.lmplot(x='age', y='fare', data=df)
```

![basic scatter plot](https://www.textbook.ds100.org/_images/viz_quantitative_25_0.png)

By default seaborn fits a regression line with 95% confidence intervals. To remove the regression line

```python
sns.lmplot(x='age', y='fare', data=df, fit_reg=False)
```

![scatter plot without regression](https://www.textbook.ds100.org/_images/viz_quantitative_27_0.png)

We can color the points using a categorical variable.

```python
sns.lmplot(x='age', y='fare', hue='who', data=df, fit_reg=False)
```

![scatter plot by category](https://www.textbook.ds100.org/_images/viz_quantitative_29_0.png)

### Qualitative Data

For categorical data we mostly use bar charts and dot charts.

**Bar Charts**

There are two types of bar charts, `countplot` and `barplot`. The count plot method counts the number of times each category appears in a column.

```python
# count how many passengers suvived
# draw bars with corresponding heights.

sns.countplot(x='alive', data=df)
```

![countplot](https://www.textbook.ds100.org/_images/viz_qualitative_5_0.png)

Like with scatterplots, we can also break down categories further using color.

```python
sns.countplot(x='alive', hue='class', data=df)
```

![countplot by class](https://www.textbook.ds100.org/_images/viz_qualitative_7_0.png)

`barplot` takes a categorical column for x, and a numerical column for y. It groups the data by the categorical column and plots the average of the numerical column. 

For example, `sns.barplot(x='alive', y='age', data=df, ci=False)` looks at the set of alive/not alive passengers, and computes the average age for each group. Note by default barplot adds confidence intervals, this can take time to generate when dealing with larger datasets, so it is useful to turn them off.

![barplot](https://www.textbook.ds100.org/_images/viz_qualitative_9_0.png)

**Dot Charts**

The same as bar charts, except instead of plotting bars, a single dot is placed at the mean. 

```python
sns.pointplot(x='alive', y='age', data=df)

sns.pointplot(x='class', y='survived', data=df)

sns.pointplot(x='class', y='survived',
hue='adult_male', data=df)
```

|	|	|
|:-------:|:--------:|
| ![](https://www.textbook.ds100.org/_images/viz_qualitative_15_0.png) |	![](https://www.textbook.ds100.org/_images/viz_qualitative_17_0.png)|
| ![](https://www.textbook.ds100.org/_images/viz_qualitative_18_0.png) | |