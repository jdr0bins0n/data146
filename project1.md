## 1 

__What is a package? What is a library?__
A package is a space that organizes libraries in a distributable manner. Libraries organize a set of functions that make sense to be together. 

__What are the two steps you need to execute in order to install a package and then make that library of functions accessible to your workspace and current python work session?__

The two steps you need to execute in order to install a package and then make that library accessible is to: 

1) find and install the package into the environment 
2) `import package_name` to install the package and `as nickname` to rename it as something easily accesible

For example, to import pandas:

1) `pip install package_path`
2) `import pandas as pd` 

To import matplotlib.pyplot

1) `pip install matplotlib_package_path`
2) `import matplotlib.pyplot` as plt

## 2

A dataframe is an object that stores data as a table of rows and columns. A library that is useful when working with data frames is pandas. To read a file that is stored on my operating system I would use the 

`pd.read_()` function. The first argument in the function is the path to the file. For example, 

```python 
data = pd.read_csv('gapminder.tsv', sep = '\t')
```

Here, we have to specify the `sep` argument, which is short for separator. `read_csv()` assumes that the data being imported is separated by commas, however, the gapminder data set is separated by tabs, so we must specify `sep = \t` -- `\t` for tab. If we did not specify the `sep` argument in this case, the data would not have been successfully imported. 

To look at the data frame we can call it by name:

```python
data 
```

To get the general idea of what a data frame looks like you can use the `df.describe` function: 

```python 
data.describe()
```

To get the rows and columns of a data frame you can use `df.shape` which puts the rows and columns in (x,y) format -- x for rows and y for columns: 

```python
data.shape()
```
Another way to describe a row in a data set is an observation, and another way to describe a column is a variable. If you would like to see all the column names, you can used the `df.columns` function. 

## 3 

The 'year' variable has regular intervals, it increases by 5 years with each additional row. If I were to add new outcomes to the raw data in order to update and make it more current, I would add 2012 and 2019 to keep wtith the regular intervals. 

Stretch goal: There are 142 unique countries, but each country is once for every date. So, if I were to add 2 dates I would need to add a date for every country. 2x142 = 184. I would need to add 184 more observations. 

## 4 
In 1992 Rwanda had the lowest life expectancy at 23. The life expectancy was so low in that year becuase from 1990-1994 Rwanda was experiencing a civil war in which the majority of casualties were civilians. This resulted in 500,000 to 800,000 deaths. With almost the entire population aged under 64, and half of it under 15, it is expected that in a civil war with such a high casuality rate many of the population did not live past 23.

## 5 

country     |year     |popXgdp
------------|---------|--------
Spain       |2007     |1.165760e+12
Italy       |2007     |1.661264e+12
France      |2007     |1.861228e+12
Germany     |2007     |1.165760e+12

## 6 

`&` AND operator. Evaluates to `True` only if both arguments specified are true. 

ex) If you needed to find a combination of two columns in a dataframe like a specific country for a given year. 

`|` - OR operator. Evaluates to `True` if one or both conditions specified are true.

ex) If you wanted to find one of two countries in a dataframe, you could use the `|` operator. 

`==` - Set equal to. This is to evaulate whether a condition is equal to what you are asking for. For example, if you wrote 

`4 == 2*2` 

it would evaluate to `True` because 2\*2 equals 4. 

`^` - EXCLUSIVE OR operator. Only evaluates to `True` if only one of two conditions specified is true. 

ex) If you need to locate one country or another in a dataframe, but only would like one or the other, you could use the `^` operator. 

## 7

`.loc` and `.iloc` are both methods within dataframes that allow index.  `iloc` is used for position-based indexing and `.loc` is used for label-based indexing. 

If I wanted to extract a series of consecutive observations from _n_ position to _k_ position I would use `.iloc[n:k-1]`


*stretch goal:* to extract all observations from a series of consecutive columns from rom _n_ position to _k_ position I would use `iloc[:, n:k-1]`

## 8 

API stands for Application Programming Interface. APIs are the interface consumers interact with when requesting access to a remote server. 

To construct a request to a remote server and pull from server and write to a local file:

```python
r = requests.get(url)
with open(filename, 'wb') as f:
    f.write(r.content)
 ```
Where `filename` is a name you contruct and `url` is the url of the server you are pulling from.


## 9 

The `apply()` function is a series method that sends each time of series into a function (the argument of apply). It's purpose is apply a function once over series versus having to repeat the function call for every row of the series. Using `apply()` is an alternative approach to iterating over a series with a `for` loop. `apply()` could be a preferred approach to iterating over a series because it requires less lines of code and is faster than interation. 

To import it to your current work session:

```python
df = pd.read_csv(filename)
```

## 10 

An alternative approach to filtering the number of columns in a data frame is to use the subsetting with brackets ([]). You can filter or select data from a dataframe and to assign it to a new dataframe you would use the syntax: 

`new_df = old_df[old_df[column] == 'data']]`
 
