---
title: "July 6, 2022, Day15"
output: 
  html_document:
    toc: true
    toc_float: true
    keep_md: true
date: '2022-07-06 07:22:22'
---


```python
import seaborn as sns
titanic = sns.load_dataset('titanic')
titanic.info()
titanic.head(10)
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 891 entries, 0 to 890
    Data columns (total 15 columns):
     #   Column       Non-Null Count  Dtype   
    ---  ------       --------------  -----   
     0   survived     891 non-null    int64   
     1   pclass       891 non-null    int64   
     2   sex          891 non-null    object  
     3   age          714 non-null    float64 
     4   sibsp        891 non-null    int64   
     5   parch        891 non-null    int64   
     6   fare         891 non-null    float64 
     7   embarked     889 non-null    object  
     8   class        891 non-null    category
     9   who          891 non-null    object  
     10  adult_male   891 non-null    bool    
     11  deck         203 non-null    category
     12  embark_town  889 non-null    object  
     13  alive        891 non-null    object  
     14  alone        891 non-null    bool    
    dtypes: bool(2), category(2), float64(2), int64(4), object(5)
    memory usage: 80.7+ KB
    





  <div id="df-5b46856c-14e7-43b0-87d8-184603a46837">
    <div class="colab-df-container">
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
      <th>survived</th>
      <th>pclass</th>
      <th>sex</th>
      <th>age</th>
      <th>sibsp</th>
      <th>parch</th>
      <th>fare</th>
      <th>embarked</th>
      <th>class</th>
      <th>who</th>
      <th>adult_male</th>
      <th>deck</th>
      <th>embark_town</th>
      <th>alive</th>
      <th>alone</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>3</td>
      <td>male</td>
      <td>22.0</td>
      <td>1</td>
      <td>0</td>
      <td>7.2500</td>
      <td>S</td>
      <td>Third</td>
      <td>man</td>
      <td>True</td>
      <td>NaN</td>
      <td>Southampton</td>
      <td>no</td>
      <td>False</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>1</td>
      <td>female</td>
      <td>38.0</td>
      <td>1</td>
      <td>0</td>
      <td>71.2833</td>
      <td>C</td>
      <td>First</td>
      <td>woman</td>
      <td>False</td>
      <td>C</td>
      <td>Cherbourg</td>
      <td>yes</td>
      <td>False</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>3</td>
      <td>female</td>
      <td>26.0</td>
      <td>0</td>
      <td>0</td>
      <td>7.9250</td>
      <td>S</td>
      <td>Third</td>
      <td>woman</td>
      <td>False</td>
      <td>NaN</td>
      <td>Southampton</td>
      <td>yes</td>
      <td>True</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1</td>
      <td>1</td>
      <td>female</td>
      <td>35.0</td>
      <td>1</td>
      <td>0</td>
      <td>53.1000</td>
      <td>S</td>
      <td>First</td>
      <td>woman</td>
      <td>False</td>
      <td>C</td>
      <td>Southampton</td>
      <td>yes</td>
      <td>False</td>
    </tr>
    <tr>
      <th>4</th>
      <td>0</td>
      <td>3</td>
      <td>male</td>
      <td>35.0</td>
      <td>0</td>
      <td>0</td>
      <td>8.0500</td>
      <td>S</td>
      <td>Third</td>
      <td>man</td>
      <td>True</td>
      <td>NaN</td>
      <td>Southampton</td>
      <td>no</td>
      <td>True</td>
    </tr>
    <tr>
      <th>5</th>
      <td>0</td>
      <td>3</td>
      <td>male</td>
      <td>NaN</td>
      <td>0</td>
      <td>0</td>
      <td>8.4583</td>
      <td>Q</td>
      <td>Third</td>
      <td>man</td>
      <td>True</td>
      <td>NaN</td>
      <td>Queenstown</td>
      <td>no</td>
      <td>True</td>
    </tr>
    <tr>
      <th>6</th>
      <td>0</td>
      <td>1</td>
      <td>male</td>
      <td>54.0</td>
      <td>0</td>
      <td>0</td>
      <td>51.8625</td>
      <td>S</td>
      <td>First</td>
      <td>man</td>
      <td>True</td>
      <td>E</td>
      <td>Southampton</td>
      <td>no</td>
      <td>True</td>
    </tr>
    <tr>
      <th>7</th>
      <td>0</td>
      <td>3</td>
      <td>male</td>
      <td>2.0</td>
      <td>3</td>
      <td>1</td>
      <td>21.0750</td>
      <td>S</td>
      <td>Third</td>
      <td>child</td>
      <td>False</td>
      <td>NaN</td>
      <td>Southampton</td>
      <td>no</td>
      <td>False</td>
    </tr>
    <tr>
      <th>8</th>
      <td>1</td>
      <td>3</td>
      <td>female</td>
      <td>27.0</td>
      <td>0</td>
      <td>2</td>
      <td>11.1333</td>
      <td>S</td>
      <td>Third</td>
      <td>woman</td>
      <td>False</td>
      <td>NaN</td>
      <td>Southampton</td>
      <td>yes</td>
      <td>False</td>
    </tr>
    <tr>
      <th>9</th>
      <td>1</td>
      <td>2</td>
      <td>female</td>
      <td>14.0</td>
      <td>1</td>
      <td>0</td>
      <td>30.0708</td>
      <td>C</td>
      <td>Second</td>
      <td>child</td>
      <td>False</td>
      <td>NaN</td>
      <td>Cherbourg</td>
      <td>yes</td>
      <td>False</td>
    </tr>
  </tbody>
</table>
</div>
      <button class="colab-df-convert" onclick="convertToInteractive('df-5b46856c-14e7-43b0-87d8-184603a46837')"
              title="Convert this dataframe to an interactive table."
              style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
       width="24px">
    <path d="M0 0h24v24H0V0z" fill="none"/>
    <path d="M18.56 5.44l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94zm-11 1L8.5 8.5l.94-2.06 2.06-.94-2.06-.94L8.5 2.5l-.94 2.06-2.06.94zm10 10l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94z"/><path d="M17.41 7.96l-1.37-1.37c-.4-.4-.92-.59-1.43-.59-.52 0-1.04.2-1.43.59L10.3 9.45l-7.72 7.72c-.78.78-.78 2.05 0 2.83L4 21.41c.39.39.9.59 1.41.59.51 0 1.02-.2 1.41-.59l7.78-7.78 2.81-2.81c.8-.78.8-2.07 0-2.86zM5.41 20L4 18.59l7.72-7.72 1.47 1.35L5.41 20z"/>
  </svg>
      </button>

  <style>
    .colab-df-container {
      display:flex;
      flex-wrap:wrap;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

      <script>
        const buttonEl =
          document.querySelector('#df-5b46856c-14e7-43b0-87d8-184603a46837 button.colab-df-convert');
        buttonEl.style.display =
          google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
          const element = document.querySelector('#df-5b46856c-14e7-43b0-87d8-184603a46837');
          const dataTable =
            await google.colab.kernel.invokeFunction('convertToInteractive',
                                                     [key], {});
          if (!dataTable) return;

          const docLinkHtml = 'Like what you see? Visit the ' +
            '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
            + ' to learn more about interactive tables.';
          element.innerHTML = '';
          dataTable['output_type'] = 'display_data';
          await google.colab.output.renderOutput(dataTable, element);
          const docLink = document.createElement('div');
          docLink.innerHTML = docLinkHtml;
          element.appendChild(docLink);
        }
      </script>
    </div>
  </div>





```python
sns.histplot(data = titanic, x = 'age', bins = 30, hue = 'sex')
```




    <matplotlib.axes._subplots.AxesSubplot at 0x7f9047e37d50>




    
![png](../images/Review_Test/output_1_1.png)
    



```python
sns.histplot(data = titanic, x = 'age', bins = 20, hue = 'alive', multiple = 'stack')
```




    <matplotlib.axes._subplots.AxesSubplot at 0x7f9047ccb790>




    
![png](../images/Review_Test/output_2_1.png)
    



```python
sns.kdeplot(data = titanic, x = 'age', hue = 'sex', multiple = 'stack')
```




    <matplotlib.axes._subplots.AxesSubplot at 0x7f9047f59c50>




    
![png](../images/Review_Test/output_3_1.png)
    



```python
sns.kdeplot(data = titanic, x = 'age', hue = 'alive', multiple = 'stack')
```




    <matplotlib.axes._subplots.AxesSubplot at 0x7f9047b57cd0>




    
![png](../images/Review_Test/output_4_1.png)
    



```python
sns.displot(data = titanic, x = 'age')
```




    <seaborn.axisgrid.FacetGrid at 0x7f9047b102d0>




    
![png](../images/Review_Test/output_5_1.png)
    



```python
sns.displot(data = titanic, x = 'age', kde = True)
```




    <seaborn.axisgrid.FacetGrid at 0x7f9047af2090>




    
![png](../images/Review_Test/output_6_1.png)
    



```python
sns.displot(data = titanic, x = 'fare')
```




    <seaborn.axisgrid.FacetGrid at 0x7f9047a86d50>




    
![png](../images/Review_Test/output_7_1.png)
    



```python
sns.displot(data = titanic, x = 'fare', kde = True)
```




    <seaborn.axisgrid.FacetGrid at 0x7f90479d4590>




    
![png](../images/Review_Test/output_8_1.png)
    



```python
sns.barplot(x = 'class', y = 'age', data = titanic)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x7f9047771150>




    
![png](../images/Review_Test/output_9_1.png)
    



```python
sns.pointplot(x = 'class', y = 'age', data = titanic)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x7f90476dff50>




    
![png](../images/Review_Test/output_10_1.png)
    



```python
sns.barplot(x = 'sex', y = 'fare', data = titanic)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x7f90476c1990>




    
![png](../images/Review_Test/output_11_1.png)
    



```python
sns.pointplot(x = 'sex', y = 'fare', data = titanic)
titanic['sex'].value_counts()
```




    male      577
    female    314
    Name: sex, dtype: int64




    
![png](../images/Review_Test/output_12_1.png)
    



```python
sns.barplot(x = 'sex', y = 'age', data = titanic)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x7f90475abd10>




    
![png](../images/Review_Test/output_13_1.png)
    



```python
sns.boxplot(x = 'alive', y = 'age', data = titanic)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x7f9047509410>




    
![png](../images/Review_Test/output_14_1.png)
    



```python
sns.violinplot(x = 'alive' , y = 'age', hue = 'sex', data = titanic)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x7f9047ae5f90>




    
![png](../images/Review_Test/output_15_1.png)
    



```python
sns.violinplot(x = 'alive' , y = 'age', hue = 'sex', data = titanic, split = True)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x7f904741ba50>




    
![png](../images/Review_Test/output_16_1.png)
    



```python
sns.countplot(x = 'sex', data = titanic)
sns.countplot(x = 'alive', data = titanic)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x7f9047388750>




    
![png](../images/Review_Test/output_17_1.png)
    



```python
import pandas as pd

flights = sns.load_dataset('flights')
print(type(flights))
flights.head()
```

    <class 'pandas.core.frame.DataFrame'>
    





  <div id="df-8bd6ff5a-351a-43ed-a9d8-b31cac425258">
    <div class="colab-df-container">
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
      <th>year</th>
      <th>month</th>
      <th>passengers</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1949</td>
      <td>Jan</td>
      <td>112</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1949</td>
      <td>Feb</td>
      <td>118</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1949</td>
      <td>Mar</td>
      <td>132</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1949</td>
      <td>Apr</td>
      <td>129</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1949</td>
      <td>May</td>
      <td>121</td>
    </tr>
  </tbody>
</table>
</div>
      <button class="colab-df-convert" onclick="convertToInteractive('df-8bd6ff5a-351a-43ed-a9d8-b31cac425258')"
              title="Convert this dataframe to an interactive table."
              style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
       width="24px">
    <path d="M0 0h24v24H0V0z" fill="none"/>
    <path d="M18.56 5.44l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94zm-11 1L8.5 8.5l.94-2.06 2.06-.94-2.06-.94L8.5 2.5l-.94 2.06-2.06.94zm10 10l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94z"/><path d="M17.41 7.96l-1.37-1.37c-.4-.4-.92-.59-1.43-.59-.52 0-1.04.2-1.43.59L10.3 9.45l-7.72 7.72c-.78.78-.78 2.05 0 2.83L4 21.41c.39.39.9.59 1.41.59.51 0 1.02-.2 1.41-.59l7.78-7.78 2.81-2.81c.8-.78.8-2.07 0-2.86zM5.41 20L4 18.59l7.72-7.72 1.47 1.35L5.41 20z"/>
  </svg>
      </button>

  <style>
    .colab-df-container {
      display:flex;
      flex-wrap:wrap;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

      <script>
        const buttonEl =
          document.querySelector('#df-8bd6ff5a-351a-43ed-a9d8-b31cac425258 button.colab-df-convert');
        buttonEl.style.display =
          google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
          const element = document.querySelector('#df-8bd6ff5a-351a-43ed-a9d8-b31cac425258');
          const dataTable =
            await google.colab.kernel.invokeFunction('convertToInteractive',
                                                     [key], {});
          if (!dataTable) return;

          const docLinkHtml = 'Like what you see? Visit the ' +
            '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
            + ' to learn more about interactive tables.';
          element.innerHTML = '';
          dataTable['output_type'] = 'display_data';
          await google.colab.output.renderOutput(dataTable, element);
          const docLink = document.createElement('div');
          docLink.innerHTML = docLinkHtml;
          element.appendChild(docLink);
        }
      </script>
    </div>
  </div>





```python
flights['month'].value_counts()
```




    Jan    12
    Feb    12
    Mar    12
    Apr    12
    May    12
    Jun    12
    Jul    12
    Aug    12
    Sep    12
    Oct    12
    Nov    12
    Dec    12
    Name: month, dtype: int64




```python
import pandas as pd

flights_pivot = flights.pivot(index = 'month', columns = 'year', values = 'passengers')
flights_pivot
```





  <div id="df-aa216323-40e3-4a02-9dc0-c9a82d5f9bd4">
    <div class="colab-df-container">
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
      <th>year</th>
      <th>1949</th>
      <th>1950</th>
      <th>1951</th>
      <th>1952</th>
      <th>1953</th>
      <th>1954</th>
      <th>1955</th>
      <th>1956</th>
      <th>1957</th>
      <th>1958</th>
      <th>1959</th>
      <th>1960</th>
    </tr>
    <tr>
      <th>month</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Jan</th>
      <td>112</td>
      <td>115</td>
      <td>145</td>
      <td>171</td>
      <td>196</td>
      <td>204</td>
      <td>242</td>
      <td>284</td>
      <td>315</td>
      <td>340</td>
      <td>360</td>
      <td>417</td>
    </tr>
    <tr>
      <th>Feb</th>
      <td>118</td>
      <td>126</td>
      <td>150</td>
      <td>180</td>
      <td>196</td>
      <td>188</td>
      <td>233</td>
      <td>277</td>
      <td>301</td>
      <td>318</td>
      <td>342</td>
      <td>391</td>
    </tr>
    <tr>
      <th>Mar</th>
      <td>132</td>
      <td>141</td>
      <td>178</td>
      <td>193</td>
      <td>236</td>
      <td>235</td>
      <td>267</td>
      <td>317</td>
      <td>356</td>
      <td>362</td>
      <td>406</td>
      <td>419</td>
    </tr>
    <tr>
      <th>Apr</th>
      <td>129</td>
      <td>135</td>
      <td>163</td>
      <td>181</td>
      <td>235</td>
      <td>227</td>
      <td>269</td>
      <td>313</td>
      <td>348</td>
      <td>348</td>
      <td>396</td>
      <td>461</td>
    </tr>
    <tr>
      <th>May</th>
      <td>121</td>
      <td>125</td>
      <td>172</td>
      <td>183</td>
      <td>229</td>
      <td>234</td>
      <td>270</td>
      <td>318</td>
      <td>355</td>
      <td>363</td>
      <td>420</td>
      <td>472</td>
    </tr>
    <tr>
      <th>Jun</th>
      <td>135</td>
      <td>149</td>
      <td>178</td>
      <td>218</td>
      <td>243</td>
      <td>264</td>
      <td>315</td>
      <td>374</td>
      <td>422</td>
      <td>435</td>
      <td>472</td>
      <td>535</td>
    </tr>
    <tr>
      <th>Jul</th>
      <td>148</td>
      <td>170</td>
      <td>199</td>
      <td>230</td>
      <td>264</td>
      <td>302</td>
      <td>364</td>
      <td>413</td>
      <td>465</td>
      <td>491</td>
      <td>548</td>
      <td>622</td>
    </tr>
    <tr>
      <th>Aug</th>
      <td>148</td>
      <td>170</td>
      <td>199</td>
      <td>242</td>
      <td>272</td>
      <td>293</td>
      <td>347</td>
      <td>405</td>
      <td>467</td>
      <td>505</td>
      <td>559</td>
      <td>606</td>
    </tr>
    <tr>
      <th>Sep</th>
      <td>136</td>
      <td>158</td>
      <td>184</td>
      <td>209</td>
      <td>237</td>
      <td>259</td>
      <td>312</td>
      <td>355</td>
      <td>404</td>
      <td>404</td>
      <td>463</td>
      <td>508</td>
    </tr>
    <tr>
      <th>Oct</th>
      <td>119</td>
      <td>133</td>
      <td>162</td>
      <td>191</td>
      <td>211</td>
      <td>229</td>
      <td>274</td>
      <td>306</td>
      <td>347</td>
      <td>359</td>
      <td>407</td>
      <td>461</td>
    </tr>
    <tr>
      <th>Nov</th>
      <td>104</td>
      <td>114</td>
      <td>146</td>
      <td>172</td>
      <td>180</td>
      <td>203</td>
      <td>237</td>
      <td>271</td>
      <td>305</td>
      <td>310</td>
      <td>362</td>
      <td>390</td>
    </tr>
    <tr>
      <th>Dec</th>
      <td>118</td>
      <td>140</td>
      <td>166</td>
      <td>194</td>
      <td>201</td>
      <td>229</td>
      <td>278</td>
      <td>306</td>
      <td>336</td>
      <td>337</td>
      <td>405</td>
      <td>432</td>
    </tr>
  </tbody>
</table>
</div>
      <button class="colab-df-convert" onclick="convertToInteractive('df-aa216323-40e3-4a02-9dc0-c9a82d5f9bd4')"
              title="Convert this dataframe to an interactive table."
              style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
       width="24px">
    <path d="M0 0h24v24H0V0z" fill="none"/>
    <path d="M18.56 5.44l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94zm-11 1L8.5 8.5l.94-2.06 2.06-.94-2.06-.94L8.5 2.5l-.94 2.06-2.06.94zm10 10l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94z"/><path d="M17.41 7.96l-1.37-1.37c-.4-.4-.92-.59-1.43-.59-.52 0-1.04.2-1.43.59L10.3 9.45l-7.72 7.72c-.78.78-.78 2.05 0 2.83L4 21.41c.39.39.9.59 1.41.59.51 0 1.02-.2 1.41-.59l7.78-7.78 2.81-2.81c.8-.78.8-2.07 0-2.86zM5.41 20L4 18.59l7.72-7.72 1.47 1.35L5.41 20z"/>
  </svg>
      </button>

  <style>
    .colab-df-container {
      display:flex;
      flex-wrap:wrap;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

      <script>
        const buttonEl =
          document.querySelector('#df-aa216323-40e3-4a02-9dc0-c9a82d5f9bd4 button.colab-df-convert');
        buttonEl.style.display =
          google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
          const element = document.querySelector('#df-aa216323-40e3-4a02-9dc0-c9a82d5f9bd4');
          const dataTable =
            await google.colab.kernel.invokeFunction('convertToInteractive',
                                                     [key], {});
          if (!dataTable) return;

          const docLinkHtml = 'Like what you see? Visit the ' +
            '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
            + ' to learn more about interactive tables.';
          element.innerHTML = '';
          dataTable['output_type'] = 'display_data';
          await google.colab.output.renderOutput(dataTable, element);
          const docLink = document.createElement('div');
          docLink.innerHTML = docLinkHtml;
          element.appendChild(docLink);
        }
      </script>
    </div>
  </div>





```python
sns.heatmap(data = flights_pivot)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x7f90472669d0>




    
![png](../images/Review_Test/output_21_1.png)
    



```python
sns.lineplot(x = 'month', y = 'passengers', data = flights)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x7f90470d0850>




    
![png](../images/Review_Test/output_22_1.png)
    



```python
tips = sns.load_dataset('tips')
tips.head()
```





  <div id="df-518fa7f3-c2ae-4371-b992-128e8e419a71">
    <div class="colab-df-container">
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
      <th>total_bill</th>
      <th>tip</th>
      <th>sex</th>
      <th>smoker</th>
      <th>day</th>
      <th>time</th>
      <th>size</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>16.99</td>
      <td>1.01</td>
      <td>Female</td>
      <td>No</td>
      <td>Sun</td>
      <td>Dinner</td>
      <td>2</td>
    </tr>
    <tr>
      <th>1</th>
      <td>10.34</td>
      <td>1.66</td>
      <td>Male</td>
      <td>No</td>
      <td>Sun</td>
      <td>Dinner</td>
      <td>3</td>
    </tr>
    <tr>
      <th>2</th>
      <td>21.01</td>
      <td>3.50</td>
      <td>Male</td>
      <td>No</td>
      <td>Sun</td>
      <td>Dinner</td>
      <td>3</td>
    </tr>
    <tr>
      <th>3</th>
      <td>23.68</td>
      <td>3.31</td>
      <td>Male</td>
      <td>No</td>
      <td>Sun</td>
      <td>Dinner</td>
      <td>2</td>
    </tr>
    <tr>
      <th>4</th>
      <td>24.59</td>
      <td>3.61</td>
      <td>Female</td>
      <td>No</td>
      <td>Sun</td>
      <td>Dinner</td>
      <td>4</td>
    </tr>
  </tbody>
</table>
</div>
      <button class="colab-df-convert" onclick="convertToInteractive('df-518fa7f3-c2ae-4371-b992-128e8e419a71')"
              title="Convert this dataframe to an interactive table."
              style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
       width="24px">
    <path d="M0 0h24v24H0V0z" fill="none"/>
    <path d="M18.56 5.44l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94zm-11 1L8.5 8.5l.94-2.06 2.06-.94-2.06-.94L8.5 2.5l-.94 2.06-2.06.94zm10 10l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94z"/><path d="M17.41 7.96l-1.37-1.37c-.4-.4-.92-.59-1.43-.59-.52 0-1.04.2-1.43.59L10.3 9.45l-7.72 7.72c-.78.78-.78 2.05 0 2.83L4 21.41c.39.39.9.59 1.41.59.51 0 1.02-.2 1.41-.59l7.78-7.78 2.81-2.81c.8-.78.8-2.07 0-2.86zM5.41 20L4 18.59l7.72-7.72 1.47 1.35L5.41 20z"/>
  </svg>
      </button>

  <style>
    .colab-df-container {
      display:flex;
      flex-wrap:wrap;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

      <script>
        const buttonEl =
          document.querySelector('#df-518fa7f3-c2ae-4371-b992-128e8e419a71 button.colab-df-convert');
        buttonEl.style.display =
          google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
          const element = document.querySelector('#df-518fa7f3-c2ae-4371-b992-128e8e419a71');
          const dataTable =
            await google.colab.kernel.invokeFunction('convertToInteractive',
                                                     [key], {});
          if (!dataTable) return;

          const docLinkHtml = 'Like what you see? Visit the ' +
            '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
            + ' to learn more about interactive tables.';
          element.innerHTML = '';
          dataTable['output_type'] = 'display_data';
          await google.colab.output.renderOutput(dataTable, element);
          const docLink = document.createElement('div');
          docLink.innerHTML = docLinkHtml;
          element.appendChild(docLink);
        }
      </script>
    </div>
  </div>





```python
sns.scatterplot(x = 'total_bill', y = 'tip',  hue = 'day', data = tips)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x7f904708c350>




    
![png](../images/Review_Test/output_24_1.png)
    



```python
sns.scatterplot(x = 'total_bill', y = 'tip',  hue = 'sex', data = tips)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x7f9046e524d0>




    
![png](../images/Review_Test/output_25_1.png)
    



```python
sns.regplot(x = 'total_bill', y = 'tip', data = tips)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x7f9046d93850>




    
![png](../images/Review_Test/output_26_1.png)
    



```python
import numpy as np
import pandas as pd

np.random.seed(0)
intercept = 4
slope = 3

noise = np.random.randn(50, 1)
x = 5 * np.random.randn(50, 1)
y = slope * x + intercept + noise


# 데이터 프레임 생성
data = pd.DataFrame(
    { 'X' : x[:, 0],
      'Y' : y[:, 0]}
)

data
```





  <div id="df-585b0239-336a-4955-ba55-7653fef067b0">
    <div class="colab-df-container">
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
      <th>X</th>
      <th>Y</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>-4.477333</td>
      <td>-7.667946</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1.934512</td>
      <td>10.203695</td>
    </tr>
    <tr>
      <th>2</th>
      <td>-2.554026</td>
      <td>-2.683339</td>
    </tr>
    <tr>
      <th>3</th>
      <td>-5.903161</td>
      <td>-11.468590</td>
    </tr>
    <tr>
      <th>4</th>
      <td>-0.140911</td>
      <td>5.444825</td>
    </tr>
    <tr>
      <th>5</th>
      <td>2.141659</td>
      <td>9.447700</td>
    </tr>
    <tr>
      <th>6</th>
      <td>0.332586</td>
      <td>5.947847</td>
    </tr>
    <tr>
      <th>7</th>
      <td>1.512359</td>
      <td>8.385721</td>
    </tr>
    <tr>
      <th>8</th>
      <td>-3.171610</td>
      <td>-5.618050</td>
    </tr>
    <tr>
      <th>9</th>
      <td>-1.813706</td>
      <td>-1.030519</td>
    </tr>
    <tr>
      <th>10</th>
      <td>-3.362302</td>
      <td>-5.942863</td>
    </tr>
    <tr>
      <th>11</th>
      <td>-1.797766</td>
      <td>0.060976</td>
    </tr>
    <tr>
      <th>12</th>
      <td>-4.065731</td>
      <td>-7.436157</td>
    </tr>
    <tr>
      <th>13</th>
      <td>-8.631413</td>
      <td>-21.772564</td>
    </tr>
    <tr>
      <th>14</th>
      <td>0.887131</td>
      <td>7.105255</td>
    </tr>
    <tr>
      <th>15</th>
      <td>-2.008905</td>
      <td>-1.693040</td>
    </tr>
    <tr>
      <th>16</th>
      <td>-8.150992</td>
      <td>-18.958896</td>
    </tr>
    <tr>
      <th>17</th>
      <td>2.313911</td>
      <td>10.736576</td>
    </tr>
    <tr>
      <th>18</th>
      <td>-4.536492</td>
      <td>-9.296408</td>
    </tr>
    <tr>
      <th>19</th>
      <td>0.259727</td>
      <td>3.925085</td>
    </tr>
    <tr>
      <th>20</th>
      <td>3.645453</td>
      <td>12.383369</td>
    </tr>
    <tr>
      <th>21</th>
      <td>0.644915</td>
      <td>6.588362</td>
    </tr>
    <tr>
      <th>22</th>
      <td>5.697003</td>
      <td>21.955446</td>
    </tr>
    <tr>
      <th>23</th>
      <td>-6.174129</td>
      <td>-15.264552</td>
    </tr>
    <tr>
      <th>24</th>
      <td>2.011708</td>
      <td>12.304879</td>
    </tr>
    <tr>
      <th>25</th>
      <td>-3.424050</td>
      <td>-7.726517</td>
    </tr>
    <tr>
      <th>26</th>
      <td>-4.353986</td>
      <td>-9.016199</td>
    </tr>
    <tr>
      <th>27</th>
      <td>-2.894248</td>
      <td>-4.869929</td>
    </tr>
    <tr>
      <th>28</th>
      <td>-1.557763</td>
      <td>0.859491</td>
    </tr>
    <tr>
      <th>29</th>
      <td>0.280827</td>
      <td>6.311839</td>
    </tr>
    <tr>
      <th>30</th>
      <td>-5.825749</td>
      <td>-13.322300</td>
    </tr>
    <tr>
      <th>31</th>
      <td>4.504132</td>
      <td>17.890560</td>
    </tr>
    <tr>
      <th>32</th>
      <td>2.328312</td>
      <td>10.097151</td>
    </tr>
    <tr>
      <th>33</th>
      <td>-7.681218</td>
      <td>-21.024452</td>
    </tr>
    <tr>
      <th>34</th>
      <td>7.441261</td>
      <td>25.975871</td>
    </tr>
    <tr>
      <th>35</th>
      <td>9.479446</td>
      <td>32.594687</td>
    </tr>
    <tr>
      <th>36</th>
      <td>5.893898</td>
      <td>22.911984</td>
    </tr>
    <tr>
      <th>37</th>
      <td>-0.899624</td>
      <td>2.503507</td>
    </tr>
    <tr>
      <th>38</th>
      <td>-5.353763</td>
      <td>-12.448616</td>
    </tr>
    <tr>
      <th>39</th>
      <td>5.272259</td>
      <td>19.514473</td>
    </tr>
    <tr>
      <th>40</th>
      <td>-2.015885</td>
      <td>-3.096207</td>
    </tr>
    <tr>
      <th>41</th>
      <td>6.112225</td>
      <td>20.916658</td>
    </tr>
    <tr>
      <th>42</th>
      <td>1.041375</td>
      <td>5.417854</td>
    </tr>
    <tr>
      <th>43</th>
      <td>4.883195</td>
      <td>20.600361</td>
    </tr>
    <tr>
      <th>44</th>
      <td>1.781832</td>
      <td>8.835844</td>
    </tr>
    <tr>
      <th>45</th>
      <td>3.532866</td>
      <td>14.160523</td>
    </tr>
    <tr>
      <th>46</th>
      <td>0.052500</td>
      <td>2.904705</td>
    </tr>
    <tr>
      <th>47</th>
      <td>8.929352</td>
      <td>31.565548</td>
    </tr>
    <tr>
      <th>48</th>
      <td>0.634560</td>
      <td>4.289784</td>
    </tr>
    <tr>
      <th>49</th>
      <td>2.009947</td>
      <td>9.817100</td>
    </tr>
  </tbody>
</table>
</div>
      <button class="colab-df-convert" onclick="convertToInteractive('df-585b0239-336a-4955-ba55-7653fef067b0')"
              title="Convert this dataframe to an interactive table."
              style="display:none;">

  <svg xmlns="http://www.w3.org/2000/svg" height="24px"viewBox="0 0 24 24"
       width="24px">
    <path d="M0 0h24v24H0V0z" fill="none"/>
    <path d="M18.56 5.44l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94zm-11 1L8.5 8.5l.94-2.06 2.06-.94-2.06-.94L8.5 2.5l-.94 2.06-2.06.94zm10 10l.94 2.06.94-2.06 2.06-.94-2.06-.94-.94-2.06-.94 2.06-2.06.94z"/><path d="M17.41 7.96l-1.37-1.37c-.4-.4-.92-.59-1.43-.59-.52 0-1.04.2-1.43.59L10.3 9.45l-7.72 7.72c-.78.78-.78 2.05 0 2.83L4 21.41c.39.39.9.59 1.41.59.51 0 1.02-.2 1.41-.59l7.78-7.78 2.81-2.81c.8-.78.8-2.07 0-2.86zM5.41 20L4 18.59l7.72-7.72 1.47 1.35L5.41 20z"/>
  </svg>
      </button>

  <style>
    .colab-df-container {
      display:flex;
      flex-wrap:wrap;
      gap: 12px;
    }

    .colab-df-convert {
      background-color: #E8F0FE;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: none;
      fill: #1967D2;
      height: 32px;
      padding: 0 0 0 0;
      width: 32px;
    }

    .colab-df-convert:hover {
      background-color: #E2EBFA;
      box-shadow: 0px 1px 2px rgba(60, 64, 67, 0.3), 0px 1px 3px 1px rgba(60, 64, 67, 0.15);
      fill: #174EA6;
    }

    [theme=dark] .colab-df-convert {
      background-color: #3B4455;
      fill: #D2E3FC;
    }

    [theme=dark] .colab-df-convert:hover {
      background-color: #434B5C;
      box-shadow: 0px 1px 3px 1px rgba(0, 0, 0, 0.15);
      filter: drop-shadow(0px 1px 2px rgba(0, 0, 0, 0.3));
      fill: #FFFFFF;
    }
  </style>

      <script>
        const buttonEl =
          document.querySelector('#df-585b0239-336a-4955-ba55-7653fef067b0 button.colab-df-convert');
        buttonEl.style.display =
          google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
          const element = document.querySelector('#df-585b0239-336a-4955-ba55-7653fef067b0');
          const dataTable =
            await google.colab.kernel.invokeFunction('convertToInteractive',
                                                     [key], {});
          if (!dataTable) return;

          const docLinkHtml = 'Like what you see? Visit the ' +
            '<a target="_blank" href=https://colab.research.google.com/notebooks/data_table.ipynb>data table notebook</a>'
            + ' to learn more about interactive tables.';
          element.innerHTML = '';
          dataTable['output_type'] = 'display_data';
          await google.colab.output.renderOutput(dataTable, element);
          const docLink = document.createElement('div');
          docLink.innerHTML = docLinkHtml;
          element.appendChild(docLink);
        }
      </script>
    </div>
  </div>





```python
import matplotlib.pyplot as plt
fig, ax = plt.subplots()
ax.scatter(data['X'], data['Y'])
plt.show()
```


    
![png](../images/Review_Test/output_28_0.png)
    



```python
import seaborn as sns
sns.scatterplot(x = 'X', y = 'Y', data = data)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x7f9046552d90>




    
![png](../images/Review_Test/output_29_1.png)
    

