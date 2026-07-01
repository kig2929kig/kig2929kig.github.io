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

## 1. 딕셔너리를 이용한 방법

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

## 2. 아스키 코드 값을 이용한 방법

```python
#print(chr(65)) # A(65) ~ Z(90)
#print(ord('Z'))
key = 20
passwd = ""
plain_text = input('평문을 입력하세요 : ')
plain_text = plain_text.upper()
for p in plain_text :
  if p == " " :
    passwd = passwd + " "
  else :
    temp = ((ord(p) - 65) + key) % 26 
    #print(chr(temp+65))
    passwd = passwd + chr(temp+65)
print(passwd)
```

## 3. 카이사르 암호 해킹  

```python
ALPHABET = {'A':0, 'B':1, 'C':2, 'D':3, 'E':4, 'F':5, 'G':6, 'H':7, 'I':8, 'J':9, 'K':10, 
            'L':11, 'M':12, 'N':13, 'O': 14, 'P':15, 'Q':16, 'R':17, 'S':18, 'T':19, 'U':20, 
            'V':21, 'W':22, 'X':23, 'Y':24, 'Z':25}

def caesar_cipher_hacking(key) :
  plain_text = ""
  for p in passwd :
    if p == " " :
      plain_text = plain_text  + " "
    else :
      plain_text = plain_text + (list(ALPHABET.keys())[ (ALPHABET.get(p)-key)%26 ])
  
  return plain_text

print(">> 카이사르 암호 해킹 <<")
passwd = input("암호문을 입력하세요 : ")
passwd = passwd.upper()


for key in range(0, 26) :
  print(key, "key :", caesar_cipher_hacking(key))


```  

    >> 카이사르 암호 해킹 <<
    암호문을 입력하세요 : EH FDUHIXO IRU DVVDVVLQDWRU
    0 key : EH FDUHIXO IRU DVVDVVLQDWRU
    1 key : DG ECTGHWN HQT CUUCUUKPCVQT
    2 key : CF DBSFGVM GPS BTTBTTJOBUPS
    3 key : BE CAREFUL FOR ASSASSINATOR  
    4 key : AD BZQDETK ENQ ZRRZRRHMZSNQ
    5 key : ZC AYPCDSJ DMP YQQYQQGLYRMP
    6 key : YB ZXOBCRI CLO XPPXPPFKXQLO
    7 key : XA YWNABQH BKN WOOWOOEJWPKN
    8 key : WZ XVMZAPG AJM VNNVNNDIVOJM
    9 key : VY WULYZOF ZIL UMMUMMCHUNIL
    10 key : UX VTKXYNE YHK TLLTLLBGTMHK
    11 key : TW USJWXMD XGJ SKKSKKAFSLGJ
    12 key : SV TRIVWLC WFI RJJRJJZERKFI
    13 key : RU SQHUVKB VEH QIIQIIYDQJEH
    14 key : QT RPGTUJA UDG PHHPHHXCPIDG
    15 key : PS QOFSTIZ TCF OGGOGGWBOHCF
    16 key : OR PNERSHY SBE NFFNFFVANGBE
    17 key : NQ OMDQRGX RAD MEEMEEUZMFAD
    18 key : MP NLCPQFW QZC LDDLDDTYLEZC
    19 key : LO MKBOPEV PYB KCCKCCSXKDYB
    20 key : KN LJANODU OXA JBBJBBRWJCXA
    21 key : JM KIZMNCT NWZ IAAIAAQVIBWZ
    22 key : IL JHYLMBS MVY HZZHZZPUHAVY
    23 key : HK IGXKLAR LUX GYYGYYOTGZUX
    24 key : GJ HFWJKZQ KTW FXXFXXNSFYTW
    25 key : FI GEVIJYP JSV EWWEWWMREXSV  
    
