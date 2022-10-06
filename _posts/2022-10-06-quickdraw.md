---
layout: single
title: "퀵, 드로우! 소개(1)"
classes: wide
toc : true
toc_sticky: true
categories:
  - 퀵, 드로우!
tags:
  - QUICK, DRAW!
  - 퀵, 드로우!
---

# 퀵, 드로우!(QUICK, DRAW!) 소개  

여러분의 낙서(그림)를 머신 러닝 기술을 통해서 학습하고 어떤 낙서(그림)인지 추측하는 게임으로, 머신 러닝을 재미있는 방식으로 활용할 수 있는 예를 소개하기 위해 제작되었다고 합니다.  
<p align="center"><img src = "https://user-images.githubusercontent.com/47412229/194256670-bfe7cc4a-da88-4563-91a3-d53ad99336d8.png" width="80%" height="80%"/></p>  

[참고 : QUICK, DRAW!](https://quickdraw.withgoogle.com/)  
[유튜브](https://youtu.be/X8v1GWzZYJ4)


## 1. 게임하기  
+ 6번의 낙서(그림)를 하면 인공지능이 어떤 낙서인지 추측합니다. 각각 20초 이내에 그려야 하며, 항상 정답을 맞히는 것은 아닙니다. 게임을 할수록 머신 러닝이 학습하여 더 정확한 추측을 할 수 있습니다.   

<p align="center"><img src ="https://user-images.githubusercontent.com/47412229/194258488-aa5243f7-d1f7-4547-b984-41d449aba95b.png" width="80%" height="80%"/></p>
<br>  
  
## 2. 세계 최대의 낙서 데이터 세트(?)  
+ 많은 사용자가 게임을 진행하면서 얻어진 다양한 결과(낙서)를 볼 수 있습니다. 또한, 결과(낙서)를 오픈 소스로 공유합니다.  

<p align="center"><img src ="https://user-images.githubusercontent.com/47412229/194261226-d1c6f930-97cf-4522-8899-014b0c3a357a.png" width="80%" height="80%"/></p>
<br>  
    
+ 비행기(airplane)를 클릭해 보면 비행기에 대한 다양한 그림을 볼 수 있습니다. 또한, 비행기라고 생각되지 않는 그림을 클릭하면 그림에 대한 정보(날짜, 나라)가 보이고 부적절하다고 판단된다면 제보할 수 있습니다.  

<p align="center"><img src = "https://user-images.githubusercontent.com/47412229/194263135-d4704c56-8ca3-40bb-8f02-1e45aecfb0b4.png" width="80%" height="80%"/></p>  
[Dataset](https://github.com/googlecreativelab/quickdraw-dataset)  

## 3. quickdraw API 따라하기  
[참고 : quickdraw API](https://quickdraw.readthedocs.io/en/latest/)

+ pip를 사용하여 파이썬 라이브러리 설치  

```
pip install quickdraw
```
![image](https://user-images.githubusercontent.com/47412229/194273702-96973813-deda-4fbe-8f67-b842fca9b89e.png)
    
+ 고양이 낙서 가져오기  

```
from quickdraw import QuickDrawData
qd = QuickDrawData()
cat = qd.get_drawing("cat")

print(cat)
```  
`QuickDrawData()` 클래스는 구글 quick, draw! 데이터 세트를 가져옵니다.    
`get_drawing(name, index)` 도면(낙서)을 가져옵니다. name(string)은 가져올 도면(낙서)의 이름(cat, airplane 등)이며 index(int)는 가져올 도면의 인덱스입니다.  

소스 코드 실행 결과는 `QuickDrawing key_id=4827440083894272`입니다. 고양이에 대한 key_id 값을 보여주며 실행할 때마다 key_id 값이 달라지는 것을 알 수 있습니다. 즉, 랜덤하게 고양이 도면(낙서)을 가지고 오는 것을 알 수 있습니다. key_id는 모든 도면(낙서)의 고유 식별자입니다.   

+ 도면(낙서)의 모든 속성 출력하기  

```
print(cat.name)
print(cat.key_id)
print(cat.countrycode)
print(cat.recognized)
print(cat.timestamp)
print(cat.no_of_strokes)
print(cat.image_data)
print(cat.strokes)
```

`name` 도면의 이름(cat, airplane ant 등)을 반환합니다.    
`countrycode` 도면의 국가 코드를 반환합니다.  
`recognized` 도면이 인식되었는지 여부를 나타내며 반환값은 부울(True, False)값입니다.  
`timestamp` 도면이 작성된 시간(초)을 반환합니다.  
`no_of_strokes` 도면을 만드는 데 사용되는 펜 스트로크 수를 반환합니다.  
`image_data` 원시 이미지 데이터를 X좌표 목록과 Y좌표 목록이 있는 획 목록으로 반환합니다.([이미지 데이터 표시 방식](https://github.com/googlecreativelab/quickdraw-dataset#simplified-drawing-files-ndjson))       
`strokes` 도면을 구성하는 (x,y) 좌표 목록이 포함된 펜 선 목록을 반환합니다.    

![image](https://user-images.githubusercontent.com/47412229/194285826-96470262-0220-441d-913d-35c3f26b2496.png)
  
  
+ 도면(낙서) 저장하기  

```
cat.image.save("my_cat.gif")
```

소스코드가 있는 위치에 그림이 저장됩니다.  
![image](https://user-images.githubusercontent.com/47412229/194287774-3a4091e3-3225-4b0d-acba-dd6a082ec860.png)

+ 도면(낙서) 보기  

```
cat.image.show()
```

도면(낙서)를 보여줍니다.   

![image](https://user-images.githubusercontent.com/47412229/194289715-4070eed6-ac4e-4412-8186-9a340d5abf28.png)




