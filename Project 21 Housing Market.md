# Housing Market

### Introduction:

This time we will create our own dataset with fictional numbers to describe a house market. As we are going to create random data don't try to reason of the numbers.

### Step 1. Import the necessary libraries


```python
import pandas as pd 
import numpy as np 
import matplotlib.pyplot as plt
import matplotlib.style as style
style.use('bmh')
%matplotlib inline

pd.options.display.max_rows = 11

from IPython.core.interactiveshell import InteractiveShell
InteractiveShell.ast_node_interactivity = "all"
```

### Step 2. Create 3 differents Series, each of length 100, as follows: 
1. The first a random number from 1 to 4 
2. The second a random number from 1 to 3
3. The third a random number from 10,000 to 30,000


```python
s1 = pd.Series(np.random.randint(1, high=5, size=100, dtype='l'))
s2 = pd.Series(np.random.randint(1, high=4, size=100, dtype='l'))
s3 = pd.Series(np.random.randint(10000, high=30001, size=100, dtype='l'))
```


```python
s1 
```




    0     2
    1     1
    2     2
    3     1
    4     4
         ..
    95    4
    96    2
    97    3
    98    1
    99    1
    Length: 100, dtype: int32




```python
s2
```




    0     2
    1     2
    2     1
    3     3
    4     2
         ..
    95    3
    96    2
    97    1
    98    3
    99    2
    Length: 100, dtype: int32




```python
s3
```




    0     29672
    1     12751
    2     26473
    3     28172
    4     29734
          ...  
    95    23986
    96    12262
    97    18526
    98    19508
    99    10251
    Length: 100, dtype: int32



### Step 3. Let's create a DataFrame by joinning the Series by column


```python
hs = pd.concat([s1 ,s2, s3], axis=1)
hs.head(10)
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
      <th>2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2</td>
      <td>2</td>
      <td>29672</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>2</td>
      <td>12751</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>1</td>
      <td>26473</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1</td>
      <td>3</td>
      <td>28172</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>2</td>
      <td>29734</td>
    </tr>
    <tr>
      <th>5</th>
      <td>1</td>
      <td>3</td>
      <td>13411</td>
    </tr>
    <tr>
      <th>6</th>
      <td>3</td>
      <td>1</td>
      <td>29443</td>
    </tr>
    <tr>
      <th>7</th>
      <td>1</td>
      <td>3</td>
      <td>16858</td>
    </tr>
    <tr>
      <th>8</th>
      <td>1</td>
      <td>3</td>
      <td>14044</td>
    </tr>
    <tr>
      <th>9</th>
      <td>4</td>
      <td>3</td>
      <td>14212</td>
    </tr>
  </tbody>
</table>
</div>



### Step 4. Change the name of the columns to bedrs, bathrs, price_sqr_meter


```python
hs.rename(columns={0:"bedrs", 1:"bathrs", 2:" price_sqr_meter"}, inplace=True)
hs.head(10)
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
      <th>bedrs</th>
      <th>bathrs</th>
      <th>price_sqr_meter</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2</td>
      <td>2</td>
      <td>29672</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>2</td>
      <td>12751</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>1</td>
      <td>26473</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1</td>
      <td>3</td>
      <td>28172</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>2</td>
      <td>29734</td>
    </tr>
    <tr>
      <th>5</th>
      <td>1</td>
      <td>3</td>
      <td>13411</td>
    </tr>
    <tr>
      <th>6</th>
      <td>3</td>
      <td>1</td>
      <td>29443</td>
    </tr>
    <tr>
      <th>7</th>
      <td>1</td>
      <td>3</td>
      <td>16858</td>
    </tr>
    <tr>
      <th>8</th>
      <td>1</td>
      <td>3</td>
      <td>14044</td>
    </tr>
    <tr>
      <th>9</th>
      <td>4</td>
      <td>3</td>
      <td>14212</td>
    </tr>
  </tbody>
</table>
</div>




```python
hs.describe()
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
      <th>bedrs</th>
      <th>bathrs</th>
      <th>price_sqr_meter</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>100.000000</td>
      <td>100.000000</td>
      <td>100.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>2.590000</td>
      <td>1.940000</td>
      <td>20473.370000</td>
    </tr>
    <tr>
      <th>std</th>
      <td>1.045384</td>
      <td>0.874094</td>
      <td>5770.354891</td>
    </tr>
    <tr>
      <th>min</th>
      <td>1.000000</td>
      <td>1.000000</td>
      <td>10251.000000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>2.000000</td>
      <td>1.000000</td>
      <td>16227.000000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>3.000000</td>
      <td>2.000000</td>
      <td>20380.000000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>3.000000</td>
      <td>3.000000</td>
      <td>25659.750000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>4.000000</td>
      <td>3.000000</td>
      <td>29971.000000</td>
    </tr>
  </tbody>
</table>
</div>



### Step 5. Create a one column DataFrame with the values of the 3 Series and assign it to 'bigcolumn'


```python
bc = pd.concat([s1 ,s2, s3], axis=0)
bc = bc.to_frame()
print(type(bc))
bc
```

    <class 'pandas.core.frame.DataFrame'>
    




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
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
    </tr>
    <tr>
      <th>95</th>
      <td>23986</td>
    </tr>
    <tr>
      <th>96</th>
      <td>12262</td>
    </tr>
    <tr>
      <th>97</th>
      <td>18526</td>
    </tr>
    <tr>
      <th>98</th>
      <td>19508</td>
    </tr>
    <tr>
      <th>99</th>
      <td>10251</td>
    </tr>
  </tbody>
</table>
<p>300 rows × 1 columns</p>
</div>



### Step 6. Oops, it seems it is going only until index 99. Is it true?


```python
len(bc)
```




    300



### Step 7. Reindex the DataFrame so it goes from 0 to 299


```python
bc.reset_index(drop=True , inplace=True)
bc 
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
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
    </tr>
    <tr>
      <th>295</th>
      <td>23986</td>
    </tr>
    <tr>
      <th>296</th>
      <td>12262</td>
    </tr>
    <tr>
      <th>297</th>
      <td>18526</td>
    </tr>
    <tr>
      <th>298</th>
      <td>19508</td>
    </tr>
    <tr>
      <th>299</th>
      <td>10251</td>
    </tr>
  </tbody>
</table>
<p>300 rows × 1 columns</p>
</div>




```python
x = hs.hist(bins=50, figsize=(20, 15))
```


    
![png](output_19_0.png)
    

