```python
from google.colab import drive
drive.mount("/content/drive")
!jupyter nbconvert --to markdown "/content/drive/MyDrive/Colab Notebooks/pandas6.ipynb"
```

# 대한민국의 인구 분석 및 시각화

## 위키백과 - 대한민국의 인구
+ https://ko.wikipedia.org/wiki/%EB%8C%80%ED%95%9C%EB%AF%BC%EA%B5%AD%EC%9D%98_%EC%9D%B8%EA%B5%AC

+ html 문서의 테이블 가져오기




```python
import pandas as pd
url = "https://ko.wikipedia.org/wiki/%EB%8C%80%ED%95%9C%EB%AF%BC%EA%B5%AD%EC%9D%98_%EC%9D%B8%EA%B5%AC"
html = pd.read_html(url)
#len(population)
#html 
html[4] #url 문서의 4번째 인덱스 테이블 가져오기
```





  <div id="df-d5bf4ceb-fe44-457b-aadd-348f066eff31">
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
      <th>연도 (년)</th>
      <th>추계인구(명)</th>
      <th>출생자수(명)</th>
      <th>사망자수(명)</th>
      <th>자연증가수(명)</th>
      <th>조출생률 (1000명당)</th>
      <th>조사망률 (1000명당)</th>
      <th>자연증가율 (1000명당)</th>
      <th>합계출산율</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1925</td>
      <td>12997611</td>
      <td>558897</td>
      <td>359042</td>
      <td>199855</td>
      <td>43.0</td>
      <td>27.6</td>
      <td>15.4</td>
      <td>6.590</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1926</td>
      <td>13052741</td>
      <td>511667</td>
      <td>337948</td>
      <td>173719</td>
      <td>39.2</td>
      <td>25.9</td>
      <td>13.3</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1927</td>
      <td>13037169</td>
      <td>534524</td>
      <td>353818</td>
      <td>180706</td>
      <td>41.0</td>
      <td>27.1</td>
      <td>13.9</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1928</td>
      <td>13105131</td>
      <td>566142</td>
      <td>357701</td>
      <td>208441</td>
      <td>43.2</td>
      <td>27.3</td>
      <td>15.9</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1929</td>
      <td>13124279</td>
      <td>566969</td>
      <td>414366</td>
      <td>152603</td>
      <td>43.2</td>
      <td>31.6</td>
      <td>11.6</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>92</th>
      <td>2017</td>
      <td>51446201</td>
      <td>357771</td>
      <td>285534</td>
      <td>72237</td>
      <td>7.0</td>
      <td>5.5</td>
      <td>1.5</td>
      <td>1.052</td>
    </tr>
    <tr>
      <th>93</th>
      <td>2018</td>
      <td>51635256</td>
      <td>326822</td>
      <td>298820</td>
      <td>28002</td>
      <td>6.4</td>
      <td>5.8</td>
      <td>0.6</td>
      <td>0.977</td>
    </tr>
    <tr>
      <th>94</th>
      <td>2019</td>
      <td>51709098</td>
      <td>303054</td>
      <td>295132</td>
      <td>7922</td>
      <td>5.9</td>
      <td>5.7</td>
      <td>0.2</td>
      <td>0.918</td>
    </tr>
    <tr>
      <th>95</th>
      <td>2020</td>
      <td>51829023</td>
      <td>272337</td>
      <td>304948</td>
      <td>-32611</td>
      <td>5.3</td>
      <td>5.9</td>
      <td>-0.6</td>
      <td>0.837</td>
    </tr>
    <tr>
      <th>96</th>
      <td>2021</td>
      <td>51744876</td>
      <td>260494</td>
      <td>317773</td>
      <td>-57280</td>
      <td>5.1</td>
      <td>6.2</td>
      <td>-1.1</td>
      <td>0.810</td>
    </tr>
  </tbody>
</table>
<p>97 rows × 9 columns</p>
</div>
      <button class="colab-df-convert" onclick="convertToInteractive('df-d5bf4ceb-fe44-457b-aadd-348f066eff31')"
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
          document.querySelector('#df-d5bf4ceb-fe44-457b-aadd-348f066eff31 button.colab-df-convert');
        buttonEl.style.display =
          google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
          const element = document.querySelector('#df-d5bf4ceb-fe44-457b-aadd-348f066eff31');
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
birth_death_statistics = html[4] # 출생 및 사망 통계
#birth_death_statistics.shape
birth_death_statistics
```





  <div id="df-645ff4a1-14f2-416a-a0f3-6a265d2a31b2">
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
      <th>연도 (년)</th>
      <th>추계인구(명)</th>
      <th>출생자수(명)</th>
      <th>사망자수(명)</th>
      <th>자연증가수(명)</th>
      <th>조출생률 (1000명당)</th>
      <th>조사망률 (1000명당)</th>
      <th>자연증가율 (1000명당)</th>
      <th>합계출산율</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1925</td>
      <td>12997611</td>
      <td>558897</td>
      <td>359042</td>
      <td>199855</td>
      <td>43.0</td>
      <td>27.6</td>
      <td>15.4</td>
      <td>6.590</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1926</td>
      <td>13052741</td>
      <td>511667</td>
      <td>337948</td>
      <td>173719</td>
      <td>39.2</td>
      <td>25.9</td>
      <td>13.3</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1927</td>
      <td>13037169</td>
      <td>534524</td>
      <td>353818</td>
      <td>180706</td>
      <td>41.0</td>
      <td>27.1</td>
      <td>13.9</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1928</td>
      <td>13105131</td>
      <td>566142</td>
      <td>357701</td>
      <td>208441</td>
      <td>43.2</td>
      <td>27.3</td>
      <td>15.9</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1929</td>
      <td>13124279</td>
      <td>566969</td>
      <td>414366</td>
      <td>152603</td>
      <td>43.2</td>
      <td>31.6</td>
      <td>11.6</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>92</th>
      <td>2017</td>
      <td>51446201</td>
      <td>357771</td>
      <td>285534</td>
      <td>72237</td>
      <td>7.0</td>
      <td>5.5</td>
      <td>1.5</td>
      <td>1.052</td>
    </tr>
    <tr>
      <th>93</th>
      <td>2018</td>
      <td>51635256</td>
      <td>326822</td>
      <td>298820</td>
      <td>28002</td>
      <td>6.4</td>
      <td>5.8</td>
      <td>0.6</td>
      <td>0.977</td>
    </tr>
    <tr>
      <th>94</th>
      <td>2019</td>
      <td>51709098</td>
      <td>303054</td>
      <td>295132</td>
      <td>7922</td>
      <td>5.9</td>
      <td>5.7</td>
      <td>0.2</td>
      <td>0.918</td>
    </tr>
    <tr>
      <th>95</th>
      <td>2020</td>
      <td>51829023</td>
      <td>272337</td>
      <td>304948</td>
      <td>-32611</td>
      <td>5.3</td>
      <td>5.9</td>
      <td>-0.6</td>
      <td>0.837</td>
    </tr>
    <tr>
      <th>96</th>
      <td>2021</td>
      <td>51744876</td>
      <td>260494</td>
      <td>317773</td>
      <td>-57280</td>
      <td>5.1</td>
      <td>6.2</td>
      <td>-1.1</td>
      <td>0.810</td>
    </tr>
  </tbody>
</table>
<p>97 rows × 9 columns</p>
</div>
      <button class="colab-df-convert" onclick="convertToInteractive('df-645ff4a1-14f2-416a-a0f3-6a265d2a31b2')"
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
          document.querySelector('#df-645ff4a1-14f2-416a-a0f3-6a265d2a31b2 button.colab-df-convert');
        buttonEl.style.display =
          google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
          const element = document.querySelector('#df-645ff4a1-14f2-416a-a0f3-6a265d2a31b2');
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




## 한글 폰트 설정


```python
!sudo apt-get install -y fonts-nanum
!sudo fc-cache -fv
!rm ~/.cache/matplotlib -rf
```

## seaborn
+ Matplotlib을 기반으로 다양한 색상 테마와 통계용 차트 등의 기능을 추가한 시각화 패키지.
+ http://seaborn.pydata.org/


```python
#!pip install IPython
import seaborn as sns
import matplotlib.pyplot as plt

sns.set(font="NanumBarunGothic") # 글꼴 설정

plt.figure(figsize=(15,4)) # 차트의 크기
plt.xticks(rotation=90) # x축 레이블 각도
sns.pointplot(data=birth_death_statistics, x="연도 (년)", y="추계인구(명)")
```




    <matplotlib.axes._subplots.AxesSubplot at 0x7f30d4e98190>




![png](pandas6_files/pandas6_7_1.png)



```python
plt.figure(figsize=(15,4))
plt.xticks(rotation=60)
sns.lineplot(data=birth_death_statistics, x="연도 (년)", y="추계인구(명)")
```




    <matplotlib.axes._subplots.AxesSubplot at 0x7f30c4acf650>




![png](pandas6_files/pandas6_8_1.png)



```python
plt.figure(figsize=(15,4))
plt.xticks(rotation=60)
sns.pointplot(data=birth_death_statistics, x="연도 (년)", y="출생자수(명)")
```




    <matplotlib.axes._subplots.AxesSubplot at 0x7f30c4d63cd0>




![png](pandas6_files/pandas6_9_1.png)


 + y축의 의미 : 1e6 = 10**6


```python
plt.figure(figsize=(15,4))
plt.xticks(rotation=60)
sns.lineplot(data=birth_death_statistics, x="연도 (년)", y="사망자수(명)")
```




    <matplotlib.axes._subplots.AxesSubplot at 0x7f30c44c25d0>




![png](pandas6_files/pandas6_11_1.png)



```python
plt.figure(figsize=(15,8))
plt.xticks(rotation=60)
sns.lineplot(data=birth_death_statistics, x="연도 (년)", y="출생자수(명)")
sns.lineplot(data=birth_death_statistics, x="연도 (년)", y="사망자수(명)", color="orange")

```




    <matplotlib.axes._subplots.AxesSubplot at 0x7f30c019fa50>




![png](pandas6_files/pandas6_12_1.png)



```python
birth_death_statistics.columns
```




    Index(['연도 (년)', '추계인구(명)', '출생자수(명)', '사망자수(명)', '자연증가수(명)', '조출생률 (1000명당)',
           '조사망률 (1000명당)', '자연증가율 (1000명당)', '합계출산율'],
          dtype='object')



## pandas에서 기본으로 제공하는 plot을 이용하여 차트 만들기


```python
temp = birth_death_statistics[['연도 (년)','출생자수(명)','사망자수(명)']]
temp = temp.set_index('연도 (년)') # 연도 (년) 데이터를 x축으로 변경
temp.plot(figsize=(15,4))
```




    <matplotlib.axes._subplots.AxesSubplot at 0x7f30bfc6c050>




![png](pandas6_files/pandas6_15_1.png)



```python
temp
```





  <div id="df-69980f17-f095-435c-b042-509d372cd4bf">
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
      <th>출생자수(명)</th>
      <th>사망자수(명)</th>
    </tr>
    <tr>
      <th>연도 (년)</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1925</th>
      <td>558897</td>
      <td>359042</td>
    </tr>
    <tr>
      <th>1926</th>
      <td>511667</td>
      <td>337948</td>
    </tr>
    <tr>
      <th>1927</th>
      <td>534524</td>
      <td>353818</td>
    </tr>
    <tr>
      <th>1928</th>
      <td>566142</td>
      <td>357701</td>
    </tr>
    <tr>
      <th>1929</th>
      <td>566969</td>
      <td>414366</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>2017</th>
      <td>357771</td>
      <td>285534</td>
    </tr>
    <tr>
      <th>2018</th>
      <td>326822</td>
      <td>298820</td>
    </tr>
    <tr>
      <th>2019</th>
      <td>303054</td>
      <td>295132</td>
    </tr>
    <tr>
      <th>2020</th>
      <td>272337</td>
      <td>304948</td>
    </tr>
    <tr>
      <th>2021</th>
      <td>260494</td>
      <td>317773</td>
    </tr>
  </tbody>
</table>
<p>97 rows × 2 columns</p>
</div>
      <button class="colab-df-convert" onclick="convertToInteractive('df-69980f17-f095-435c-b042-509d372cd4bf')"
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
          document.querySelector('#df-69980f17-f095-435c-b042-509d372cd4bf button.colab-df-convert');
        buttonEl.style.display =
          google.colab.kernel.accessAllowed ? 'block' : 'none';

        async function convertToInteractive(key) {
          const element = document.querySelector('#df-69980f17-f095-435c-b042-509d372cd4bf');
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
#temp[-50:] #최근 50년
temp[-50:].plot(figsize=(15,8))
```




    <matplotlib.axes._subplots.AxesSubplot at 0x7f30c1620290>




![png](pandas6_files/pandas6_17_1.png)


## seaborn - barplot 만들기


```python
plt.figure(figsize=(15,4))
plt.xticks(rotation=60)
#sns.barplot(data=birth_death_statistics, x="연도 (년)", y="추계인구(명)")
sns.barplot(data=birth_death_statistics, x="연도 (년)", y="추계인구(명)", palette="Blues")
```




    <matplotlib.axes._subplots.AxesSubplot at 0x7f30bf85fc10>




![png](pandas6_files/pandas6_19_1.png)



```python
plt.figure(figsize=(15,4))
plt.xticks(rotation=60)
sns.pointplot(data=birth_death_statistics, x="연도 (년)", y="추계인구(명)", palette="Blues")
```




    <matplotlib.axes._subplots.AxesSubplot at 0x7f30c0d2bcd0>




![png](pandas6_files/pandas6_20_1.png)



```python
plt.figure(figsize=(15,4))
plt.xticks(rotation=60)
sns.lineplot(data=birth_death_statistics, x="연도 (년)", y="추계인구(명)")
```




    <matplotlib.axes._subplots.AxesSubplot at 0x7f30c083f3d0>




![png](pandas6_files/pandas6_21_1.png)

