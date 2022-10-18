---
layout: single
title: "[python] 카이사르 암호 만들기"
classes: wide
toc : true
toc_sticky: true
categories:
  - python project
tags:
  - python
  - 파이썬
---

# 카이사르 암호 (Caesar cipher)
카이사르 암호 또는 시저 암호는 암호학에서 가장 간단하고 널리 알려진 암호화 기술 중 하나입니다. 
일반 텍스트의 각 문자에 고정된 길이만큼 밀어서 다른 문자로 대체되는 일종의 대체 암호입니다.
실제로 로마의 황제 카이사르가 자신의 개인 서신에 사용했습니다.  

예를 들어 Key = 2이면 A는 C로 대체되고 B는 D가 되는 식입니다.  


    텍스트 : A B C D E F G H I J K L M N O P Q R S T U V W X Y Z    
    Key : 5  
    암호문 : F G H I J K L M N O P Q R S T U V W X Y Z A B C D E 

암살 위기에 처한 카이사르에게 가족들이 암호문을 보냈는데, 암호문은  "EH FDUHIXO IRU DVVDVVLQDWRU" 입니다. 이 암호문의 뜻은 "BE CAREFUL FOR ASSASSINATOR" 이며, 여기서 key는 3으로 원래의 알파벳을 일정한 간격(key=3)으로 이동시키면 암호문이 됩니다.


```python
ALPHABET = {'A':0, 'B':1, 'C':2, 'D':3, 'E':4, 'F':5, 'G':6, 'H':7, 'I':8, 'J':9, 'K':10, 
            'L':11, 'M':12, 'N':13, 'O': 14, 'P':15, 'Q':16, 'R':17, 'S':18, 'T':19, 'U':20, 
            'V':21, 'W':22, 'X':23, 'Y':24, 'Z':25}

key = 3

print(">> 카이사르 암호 <<")
plain_text = input("평문을 입력하세요 : ")
plain_text = plain_text.upper()
crypto_text = ""

for p in plain_text :
  if p == " " :
    crypto_text = crypto_text + " "
  else :
    #print(ALPHABET.keys()[ALPHABET.get(p)+3])
    crypto_text = crypto_text + (list(ALPHABET.keys())[ (ALPHABET.get(p)+3)%26 ])
print("암호문 :", crypto_text)
```

    >> 카이사르 암호 <<
    평문을 입력하세요 : BE CAREFUL FOR ASSASSINATOR
    암호문 : EH FDUHIXO IRU DVVDVVLQDWRU

