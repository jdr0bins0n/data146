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

To get the general idea of what a data frame looks like you can use the `pd.describe` function: 

```python 
data.describe()
```

To get the rows and columns of a data frame you can use `pd.shape` which puts the rows and columns in (x,y) format -- x for rows and y for columns. 

## 3 


There are a couple different ways to describe a 

