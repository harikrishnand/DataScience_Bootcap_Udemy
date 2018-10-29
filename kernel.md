
---
title: pandas DataFrame
---

## DataFrame

In this section we will have a detailed look on the other important data-type of pandas DataFrame. In pandas, DataFrame is used as an object to represent multi-dimentional data. They are mainly used to repersent 2 dimensional or tabluar data with rows and columns. They can also be called as collection of `Series`.  

DataFrame also supports 3-D data using the multi index properties. It will be the replacement for the old and now existing `panel` object. A 3-D DataFrame can consist of multiple 2-D dataframes.

### Basic syntax of DataFrame


```python
pandas.DataFrame(data=None, index=None, columns=None, dtype=None, copy=False)
```

`Data`  : ndarray, dict,Series, another dataframe

`index`  : array-like or index. default to RangeIndex(1,2,3 . . n). Represents the index label.

`columns`  : array-like or index. default to RangeIndex(1,2,3 . . n). Represents the column label.

`dtype`  : dtype, default None. Data type of the DataFrame 

### Creating DataFrame in different ways:

As a first step lets import our pandas module:


```python
import pandas as pd
```

### Create an empty DataFrame:


```python
pd.DataFrame()
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
    </tr>
  </thead>
  <tbody>
  </tbody>
</table>
</div>



### Create using a list:


```python
input_data = [['Mark',87],['Tom',78],['Monika',97]]
pd.DataFrame(data = input_data)
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
      <th>0</th>
      <th>1</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Mark</td>
      <td>87</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Tom</td>
      <td>78</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Monika</td>
      <td>97</td>
    </tr>
  </tbody>
</table>
</div>




```python
print('DataFrame with column and row index labels:')
roll_no = [223,224,225]
pd.DataFrame(data= input_data,index= roll_no,
             columns=['Name','Score'])
```

    DataFrame with column and row index labels:





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
      <th>Name</th>
      <th>Score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>223</th>
      <td>Mark</td>
      <td>87</td>
    </tr>
    <tr>
      <th>224</th>
      <td>Tom</td>
      <td>78</td>
    </tr>
    <tr>
      <th>225</th>
      <td>Monika</td>
      <td>97</td>
    </tr>
  </tbody>
</table>
</div>



### Create using a dict:


```python
input_data = {'Name': ['Mark','Tom','Monika'],
              'Score': [87,78,97]}
pd.DataFrame(data=input_data,dtype= float)         # Notice that the score is change to float.
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
      <th>Name</th>
      <th>Score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Mark</td>
      <td>87.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Tom</td>
      <td>78.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Monika</td>
      <td>97.0</td>
    </tr>
  </tbody>
</table>
</div>



### Create using a list of dict:


```python
input_data = [{'Name': 'Mark','Score': 87},
              {'Name': 'Tom','Score': 78},
              {'Name': 'Monika', 'Score': 97}]
pd.DataFrame(data= input_data, index=roll_no)
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
      <th>Name</th>
      <th>Score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>223</th>
      <td>Mark</td>
      <td>87</td>
    </tr>
    <tr>
      <th>224</th>
      <td>Tom</td>
      <td>78</td>
    </tr>
    <tr>
      <th>225</th>
      <td>Monika</td>
      <td>97</td>
    </tr>
  </tbody>
</table>
</div>



### Create using a dict of Series:


```python
input_data = {'Name': pd.Series(['Mark','Tom','Monika','John']),
              'Score': pd.Series([87,78,97])}
pd.DataFrame(input_data)
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
      <th>Name</th>
      <th>Scores</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Mark</td>
      <td>87.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Tom</td>
      <td>78.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Monika</td>
      <td>97.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>John</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>



Notice the above output, For John the score is NaN(not a number). In pandas empty values are defaulted with numpy.nan.

### DataFrame Manipulations:

Now that we have a comprehensive idea on how to create a DataFrame and different kind of inputs we can use to create it. Lets move on to different manupulation operations we can do with a DataFrame.

### Column Manipulation:

Here we will discuss about below operation on the column level:
* Column selection
* Column addition
* Column deletion


```python
score_sheet = {'Name': pd.Series(['Mark','Tom','Monika','Lilly','Sam']),
               'Maths': pd.Series([89,87,83,78,77]),
               'Science': pd.Series([78,88,66,0,88])}
DF = pd.DataFrame(score_sheet)
print(DF)
```

         Name  Maths  Science
    0    Mark     89       78
    1     Tom     87       88
    2  Monika     83       66
    3   Lilly     78        0
    4     Sam     77       88


### Column selection:


```python
DF['Name']             # Selcting a particular column
```




    0      Mark
    1       Tom
    2    Monika
    3     Lilly
    4       Sam
    Name: Name, dtype: object




```python
type(DF['Maths'])
```




    pandas.core.series.Series



You can notice that each column in a DataFrame is considered as a Series and it supports all the Series type operations.  Example:`


```python
DF['Maths'].max()      # Finding the max score in maths
```




    89




```python
DF[['Name','Maths']]    # Selcting multiple column
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
      <th>Name</th>
      <th>Maths</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Mark</td>
      <td>89</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Tom</td>
      <td>87</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Monika</td>
      <td>83</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Lilly</td>
      <td>78</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Sam</td>
      <td>77</td>
    </tr>
  </tbody>
</table>
</div>



### Column addition:


```python
DF['English'] = pd.Series([88,89,98,88,0])   # Adding a new subject English.
DF
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
      <th>Name</th>
      <th>Maths</th>
      <th>Science</th>
      <th>English</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Mark</td>
      <td>89</td>
      <td>78</td>
      <td>88</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Tom</td>
      <td>87</td>
      <td>88</td>
      <td>89</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Monika</td>
      <td>83</td>
      <td>66</td>
      <td>98</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Lilly</td>
      <td>78</td>
      <td>0</td>
      <td>88</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Sam</td>
      <td>77</td>
      <td>88</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
</div>




```python
DF['Total Score'] = DF['Maths'] + DF['Science'] + DF['English']
DF
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
      <th>Name</th>
      <th>Maths</th>
      <th>Science</th>
      <th>English</th>
      <th>Total Score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Mark</td>
      <td>89</td>
      <td>78</td>
      <td>88</td>
      <td>255</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Tom</td>
      <td>87</td>
      <td>88</td>
      <td>89</td>
      <td>264</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Monika</td>
      <td>83</td>
      <td>66</td>
      <td>98</td>
      <td>247</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Lilly</td>
      <td>78</td>
      <td>0</td>
      <td>88</td>
      <td>166</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Sam</td>
      <td>77</td>
      <td>88</td>
      <td>0</td>
      <td>165</td>
    </tr>
  </tbody>
</table>
</div>



### Column deletion:


```python
#Using the del function:
del DF['English']
DF
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
      <th>Name</th>
      <th>Maths</th>
      <th>Science</th>
      <th>Total Score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Mark</td>
      <td>89</td>
      <td>78</td>
      <td>255</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Tom</td>
      <td>87</td>
      <td>88</td>
      <td>264</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Monika</td>
      <td>83</td>
      <td>66</td>
      <td>247</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Lilly</td>
      <td>78</td>
      <td>0</td>
      <td>166</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Sam</td>
      <td>77</td>
      <td>88</td>
      <td>165</td>
    </tr>
  </tbody>
</table>
</div>




```python
#Using the pop method:
DF.pop('Total Score')
DF
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
      <th>Name</th>
      <th>Maths</th>
      <th>Science</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Mark</td>
      <td>89</td>
      <td>78</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Tom</td>
      <td>87</td>
      <td>88</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Monika</td>
      <td>83</td>
      <td>66</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Lilly</td>
      <td>78</td>
      <td>0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Sam</td>
      <td>77</td>
      <td>88</td>
    </tr>
  </tbody>
</table>
</div>



### Row Manipulation:

As like colum we have the similar operation for rows as well. Now we will disscuss about those operations in row level in detail. We will use the same `DataFrame` DF we have created before.

### Row selection:

There are two method availabel in DataFrame for selection. They are .iloc() and .loc().

* .iloc() method is used to select based on position.
* loc() method is used to select based on the label value.

Now we will see about the .iloc() method.


```python
DF.iloc[2]              #retruns the 2nd row.
```




    Name       Monika
    Maths          83
    Science        66
    Name: 2, dtype: object




```python
type(DF.iloc[3])
```




    pandas.core.series.Series



The important thing to notice here is that it returns a series again. Not just the column is retruned as a Series , rows as well.


```python
DF[2:4]           # Sliceing the rows 
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
      <th>Name</th>
      <th>Maths</th>
      <th>Science</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2</th>
      <td>Monika</td>
      <td>83</td>
      <td>66</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Lilly</td>
      <td>78</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
</div>



### Row addition:


```python
new_student = pd.DataFrame(data = [['Ben',79,89]], 
                           columns=['Name','Maths','Science'], 
                           index=[5])

DF.append(new_student)             # Using the append method added a new column.
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
      <th>Name</th>
      <th>Maths</th>
      <th>Science</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Mark</td>
      <td>89</td>
      <td>78</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Tom</td>
      <td>87</td>
      <td>88</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Monika</td>
      <td>83</td>
      <td>66</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Lilly</td>
      <td>78</td>
      <td>0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Sam</td>
      <td>77</td>
      <td>88</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Ben</td>
      <td>79</td>
      <td>89</td>
    </tr>
  </tbody>
</table>
</div>



### Row deletion:


```python
# We delete using the drop method and we use index label for deleting:
DF.drop(3)
DF
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
      <th>Name</th>
      <th>Maths</th>
      <th>Science</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Mark</td>
      <td>89</td>
      <td>78</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Tom</td>
      <td>87</td>
      <td>88</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Monika</td>
      <td>83</td>
      <td>66</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Lilly</td>
      <td>78</td>
      <td>0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Sam</td>
      <td>77</td>
      <td>88</td>
    </tr>
  </tbody>
</table>
</div>



#### More Information:

[DataFrame](http://pandas.pydata.org/pandas-docs/version/0.23.4/generated/pandas.DataFrame.html)
