```python
from google.colab import drive
drive.mount("/content/drive")
!jupyter nbconvert --to markdown "/content/drive/MyDrive/Colab Notebooks/wordcloud.ipynb"
```


```python
!sudo apt-get install -y fonts-nanum
```


```python
!sudo fc-cache -fv
!rm ~/.cache/matplotlib -rf
```


```python
!pip install wordcloud
!pip install konlpy
!pip install collection
!pip install requests
!pip install bs4
```


```python
from bs4 import BeautifulSoup
import requests
from konlpy.tag import Twitter
from collections import Counter
from wordcloud import WordCloud
import matplotlib.pyplot as plt
```


```python

```


```python
search_word = "안산공업고등학교"
start_num = 1
title_list = []
#print(req)

def get_title(start_num, end_num) :
  
  while start_num <= end_num :
    url = 'https://search.naver.com/search.naver?where=news&sm=tab_jum&query={}&start={}'.format(search_word,start_num)
    req = requests.get(url)
    
    if req.ok :
      html = req.text
      soup = BeautifulSoup(html, "html.parser")
      #print(soup)  
      titles = soup.select('.news_tit')
      for title in titles :
        title_list.append(title['title'])
    start_num += 1
  #print(title_list)
  #print(len(title_list))
get_title(1, 10)

def make_wordcloud(word_count) :
  twitter = Twitter()
  sentences_tag = []
  for sentence in title_list :
    morph = twitter.pos(sentence)
    sentences_tag.append(morph)
    #print(morph)
    #print("-" * 30)
  #print(sentences_tag)
  #print("\n" * 3)

  noun_adj_list = []

  for sentence in sentences_tag :
    for word, tag in sentence :
      if tag in ['Noun', 'Adjective'] :
        noun_adj_list.append(word)
    
  counts = Counter(noun_adj_list)
  tags = counts.most_common(word_count)
  #print(tags)
  
  wc = WordCloud(font_path = '/usr/share/fonts/truetype/nanum/NanumBarunGothic.ttf', background_color='white', width=800, height=600)
  print(dict(tags))
  plt.rc('font', family='NanumBarunGothic')
  cloud = wc.generate_from_frequencies(dict(tags))
  plt.figure(figsize=(10,8))
  plt.axis('off')
  plt.imshow(cloud)
  plt.show()


make_wordcloud(10)
```

    {'안산': 46, '대회': 46, '안산공고': 38, '학교': 33, '학생': 32, '공업고등학교': 30, '전국': 27, '제': 24, '안산시': 23, '대통령': 22}



![png](wordcloud_files/wordcloud_6_1.png)

