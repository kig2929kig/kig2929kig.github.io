---
layout: single
title: "[python] 디지털 시계 만들기"
classes: wide
toc : true
toc_sticky: true
categories:
  - python project
tags:
  - python
  - 파이썬
---

# 디지털 시계

```python

from datetime import datetime
from pytz import timezone
import sys, time, os

rows = ['','','']
seconds = ""

def digit(number) :
  if number == 0 :
    rows[0] += ' __ '
    rows[1] += '|  |'
    rows[2] += '|__|'
  elif number == 1 :
    rows[0] += '    '
    rows[1] += '   |'
    rows[2] += '   |'
  elif number == 2 :
    rows[0] += ' __ '
    rows[1] += ' __|'
    rows[2] += '|__ '
  elif number == 3 :
    rows[0] += ' __ '
    rows[1] += ' __|'
    rows[2] += ' __|'
  elif number == 4 :
    rows[0] += '    '
    rows[1] += '|__|'
    rows[2] += '   |'
  elif number == 5 :
    rows[0] += ' __ '
    rows[1] += '|__ '
    rows[2] += ' __|'
  elif number == 6 :
    rows[0] += ' __ '
    rows[1] += '|__ '
    rows[2] += '|__|'
  elif number == 7 :
    rows[0] += ' __ '
    rows[1] += '   |'
    rows[2] += '   |'
  elif number == 8 :
    rows[0] += ' __ '
    rows[1] += '|__|'
    rows[2] += '|__|'
  elif number == 9 :
    rows[0] += ' __ '
    rows[1] += '|__|'
    rows[2] += ' __|'
  elif number == '.':
    rows[0] += '    '
    rows[1] += '  * '
    rows[2] += '  * '


while True :

  try : 
    korea_time = datetime.now(timezone('Asia/Seoul'))
    hours = str(korea_time.hour)
    hours = hours.zfill(2)

    minutes = str(korea_time.minute)
    minutes = minutes.zfill(2)
    #print(minutes)

    seconds = str(korea_time.second)
    seconds = seconds.zfill(2)
    #print(seconds)

    digit(int(hours[0]))
    digit(int(hours[1]))
    digit('.')
    digit(int(minutes[0]))
    digit(int(minutes[1]))
    digit('.')
    digit(int(seconds[0]))
    digit(int(seconds[1]))
    
    #print("\n".join(rows))
    #print(rows[0])
    #print(rows[1])
    #print(rows[2])
    
    if datetime.now(timezone('Asia/Seoul')).second != seconds :
        os.system("cls")
        print("\n".join(rows))
        print()
        print('Press Ctrl-C to quit.')
        time.sleep(0.5)
        rows = ['', '', '']
     
  except KeyboardInterrupt :
    print("Digital Clock, by kig2929kig.github.io")
    sys.exit() # Ctrl-C is pressed

```  

![image](https://user-images.githubusercontent.com/47412229/196572789-45bf58e4-5655-436e-9a83-882d71f8e276.png)
