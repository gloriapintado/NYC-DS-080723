# Phase 2 Code Challenge

This code challenge is designed to test your understanding of the Phase 2 material. It covers:

- SQL
- Bayesian Statistics
- Normal Distribution
- Statistical Tests

_Read the instructions carefully_. You will be asked both to write code and to answer short answer questions.

## Code Tests

We have provided some code tests for you to run to check that your work meets the item specifications. Passing these tests does not necessarily mean that you have gotten the item correct - there are additional hidden tests. However, if any of the tests do not pass, this tells you that your code is incorrect and needs changes to meet the specification. To determine what the issue is, read the comments in the code test cells, the error message you receive, and the item instructions.

## Short Answer Questions 

For the short answer questions...

* _Use your own words_. It is OK to refer to outside resources when crafting your response, but _do not copy text from another source_.

* _Communicate clearly_. We are not grading your writing skills, but you can only receive full credit if your teacher is able to fully understand your response. 

* _Be concise_. You should be able to answer most short answer questions in a sentence or two. Writing unnecessarily long answers increases the risk of you being unclear or saying something incorrect.


```python
# Run this cell without changes to import the necessary libraries

import itertools
import numpy as np
import pandas as pd 
from numbers import Number
import sqlite3
from scipy import stats
import matplotlib.pyplot as plt
import seaborn as sns
import statsmodels.api as sm
import warnings
warnings.filterwarnings('ignore')

import pickle
```

---
## Part 1: SQL [Suggested time: 20 minutes]
---
In this part, you will create and execute three SQL queries on the Chinook database. For this challenge **you will need to access the `Album` and `Artist` tables**.

### 1.1) Connect to the Database.


```python
# CodeGrade step1.1
# Replace None with appropriate code
# Connect to the Database here ("Chinook_Sqlite.sqlite")

path = None
conn = sqlite3.connect(path)
```


```python
assert type(path) == str
```


```python
# Run this cell without changes to see all the
# tables in the database.

df = pd.read_sql(
    """
    SELECT *
    FROM sqlite_master
    """
, conn
)

df[df['type'] == 'table']
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>type</th>
      <th>name</th>
      <th>tbl_name</th>
      <th>rootpage</th>
      <th>sql</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>table</td>
      <td>Album</td>
      <td>Album</td>
      <td>2</td>
      <td>CREATE TABLE [Album]\n(\n    [AlbumId] INTEGER...</td>
    </tr>
    <tr>
      <th>1</th>
      <td>table</td>
      <td>Artist</td>
      <td>Artist</td>
      <td>3</td>
      <td>CREATE TABLE [Artist]\n(\n    [ArtistId] INTEG...</td>
    </tr>
    <tr>
      <th>2</th>
      <td>table</td>
      <td>Customer</td>
      <td>Customer</td>
      <td>4</td>
      <td>CREATE TABLE [Customer]\n(\n    [CustomerId] I...</td>
    </tr>
    <tr>
      <th>3</th>
      <td>table</td>
      <td>Employee</td>
      <td>Employee</td>
      <td>7</td>
      <td>CREATE TABLE [Employee]\n(\n    [EmployeeId] I...</td>
    </tr>
    <tr>
      <th>4</th>
      <td>table</td>
      <td>Genre</td>
      <td>Genre</td>
      <td>9</td>
      <td>CREATE TABLE [Genre]\n(\n    [GenreId] INTEGER...</td>
    </tr>
    <tr>
      <th>5</th>
      <td>table</td>
      <td>Invoice</td>
      <td>Invoice</td>
      <td>10</td>
      <td>CREATE TABLE [Invoice]\n(\n    [InvoiceId] INT...</td>
    </tr>
    <tr>
      <th>6</th>
      <td>table</td>
      <td>InvoiceLine</td>
      <td>InvoiceLine</td>
      <td>12</td>
      <td>CREATE TABLE [InvoiceLine]\n(\n    [InvoiceLin...</td>
    </tr>
    <tr>
      <th>7</th>
      <td>table</td>
      <td>MediaType</td>
      <td>MediaType</td>
      <td>14</td>
      <td>CREATE TABLE [MediaType]\n(\n    [MediaTypeId]...</td>
    </tr>
    <tr>
      <th>8</th>
      <td>table</td>
      <td>Playlist</td>
      <td>Playlist</td>
      <td>15</td>
      <td>CREATE TABLE [Playlist]\n(\n    [PlaylistId] I...</td>
    </tr>
    <tr>
      <th>9</th>
      <td>table</td>
      <td>PlaylistTrack</td>
      <td>PlaylistTrack</td>
      <td>16</td>
      <td>CREATE TABLE [PlaylistTrack]\n(\n    [Playlist...</td>
    </tr>
    <tr>
      <th>11</th>
      <td>table</td>
      <td>Track</td>
      <td>Track</td>
      <td>19</td>
      <td>CREATE TABLE [Track]\n(\n    [TrackId] INTEGER...</td>
    </tr>
  </tbody>
</table>
</div>



### 1.2) Write a query to return the last ten artists alphabetically.


```python
# CodeGrade step1.2
# Replace None with appropriate code
# Hint: Use the Artist table!

first_query = None

pd.read_sql(first_query, conn)
```


```python
# first_query should be a string
assert type(first_query) == str

# first_query should be a SQL query
first_query_df = pd.read_sql(first_query, conn)
```

### 1.3) Write a query to return all the albums in the database from Led Zeppelin.


```python
# CodeGrade step1.3
# Replace None with appropriate code
# Hint: Use the Artist and Album tables!

second_query = None

pd.read_sql(second_query, conn)
```


```python
# second_query should be a string
assert type(second_query) == str

# second_query should be a SQL query
second_query_df = pd.read_sql(second_query, conn)
```

### 1.4) Write a query to return both the artist with the most albums in the database and the number of albums.


```python
# CodeGrade step1.4
# Replace None with appropriate code

third_query = None

pd.read_sql(third_query, conn)
```


```python
# third_query should be a string
assert type(third_query) == str

# third_query should be a SQL query
third_query_df = pd.read_sql(third_query, conn)
```

---
## Part 2: Bayesian Statistics [Suggested time: 15 minutes]
---

A medical test is designed to diagnose a certain disease. The test has a false positive rate of 10%, meaning that 10% of people without the disease will get a positive test result. The test has a false negative rate of 2%, meaning that 2% of people with the disease will get a negative result. Only 1% of the population has this disease.

### 2.1) Create a numeric variable `p_pos_test` containing the probability of a person receiving a positive test result.

Assume that the person being tested is randomly selected from the broader population.


```python
# CodeGrade step2.1
# Replace None with appropriate code
    
false_pos_rate = 0.1
false_neg_rate = 0.02
population_rate = 0.01

p_pos_test = None
```


```python
# This test confirms that you have created a numeric variable named p_pos_test

assert isinstance(p_pos_test, Number)
```


```python
# These tests confirm that p_pos_test is a value between 0 and 1

assert p_pos_test >= 0
assert p_pos_test <= 1
```

### 2.2) Create a numeric variable `p_disease_given_pos` containing the probability of a person actually having the disease if they receive a positive test result.

Assume that the person being tested is randomly selected from the broader population.

Hint: Use your answer to the previous question to help answer this one.


```python
# CodeGrade step2.2
# Replace None with appropriate code
    
false_pos_rate = 0.1
false_neg_rate = 0.02
population_rate = 0.01

p_disease_given_pos = None
```


```python
# This test confirms that you have created a numeric variable named p_disease_given_pos

assert isinstance(p_disease_given_pos, Number)
```


```python
# These tests confirm that p_disease_given_pos is a value between 0 and 1

assert p_disease_given_pos >= 0
assert p_disease_given_pos <= 1
```

---
## Part 3: Normal Distribution [Suggested time: 20 minutes]
---
In this part, you will analyze check totals at a TexMex restaurant. We know that the population distribution of check totals for the TexMex restaurant is normally distributed with a mean of \\$20 and a standard deviation of \\$3. 

### 3.1) Create a numeric variable `z_score_26` containing the z-score for a \\$26 check. 


```python
# CodeGrade step3.1
# Replace None with appropriate code

z_score_26 = None
```


```python
# This test confirms that you have created a numeric variable named z_score_26

assert isinstance(z_score_26, Number)
```

### 3.2) Create a numeric variable `p_under_26` containing the approximate proportion of all checks that are less than \\$26.

Hint: Use the answer from the previous question along with the empirical rule, a Python function, or this [z-table](https://www.math.arizona.edu/~rsims/ma464/standardnormaltable.pdf).


```python
# CodeGrade step3.2
# Replace None with appropriate code

p_under_26 = None
```


```python
# This test confirms that you have created a numeric variable named p_under_26

assert isinstance(p_under_26, Number)

# These tests confirm that p_under_26 is a value between 0 and 1

assert p_under_26 >= 0
assert p_under_26 <= 1
```

### 3.3) Create numeric variables `conf_low` and `conf_high` containing the lower and upper bounds (respectively) of a 95% confidence interval for the mean of one waiter's check amounts using the information below. 

One week, a waiter gets 100 checks with a mean of \\$19 and a standard deviation of \\$3.


```python
# CodeGrade step3.3
# Replace None with appropriate code

n = 100
mean = 19
std = 3

conf_low = None
conf_high = None
```


```python
# These tests confirm that you have created numeric variables named conf_low and conf_high

assert isinstance(conf_low, Number)
assert isinstance(conf_high, Number)

# This test confirms that conf_low is below conf_high

assert conf_low < conf_high

# These statements print your answers for reference to help answer the next question

print('The lower bound of the 95% confidence interval is {}'.format(conf_low))
print('The upper bound of the 95% confidence interval is {}'.format(conf_high))
```

    The lower bound of the 95% confidence interval is 18.412
    The upper bound of the 95% confidence interval is 19.588


### 3.4) Short Answer: Interpret the 95% confidence interval you just calculated in Question 1.3.


```python
# Your answer here


```

---
## Part 4: Statistical Testing [Suggested time: 20 minutes]
---
The TexMex restaurant recently introduced queso to its menu.

We have a random sample containing 2000 check totals, all from different customers: 1000 check totals for orders without queso ("no queso") and 1000 check totals for orders with queso ("queso").

In the cell below, we load the sample data for you into the arrays `no_queso` and `queso` for the "no queso" and "queso" order check totals, respectively.


```python
# Run this cell without changes

# Load the sample data 
no_queso = pickle.load(open('./no_queso.pkl', 'rb'))
queso = pickle.load(open('./queso.pkl', 'rb'))
```

### 4.1) Short Answer: State null and alternative hypotheses to use for testing whether customers who order queso spend different amounts of money from customers who do not order queso.


```python
# Your answer here


```

### 4.2) Short Answer: What would it mean to make a Type I error for this specific hypothesis test?

Your answer should be _specific to this context,_  not a general statement of what Type I error is.


```python
# Your answer here


```

### 4.3) Create a numeric variable `p_value` containing the p-value associated with a statistical test of your hypotheses. 

You must identify and implement the correct statistical test for this scenario. You can assume the two samples have equal variances.

Hint: Use `scipy.stats` to calculate the answer - it has already been imported as `stats`. Relevant documentation can be found [here](https://docs.scipy.org/doc/scipy/reference/stats.html#statistical-tests).


```python
# CodeGrade step4.3
# Replace None with appropriate code

p_value = 
```


```python
# This test confirms that you have created a numeric variable named p_value

assert isinstance(p_value, Number)
```

### 4.4) Short Answer: Can you reject the null hypothesis using a significance level of $\alpha$ = 0.05? Explain why or why not.


```python
# Your answer here


```


```python

```
