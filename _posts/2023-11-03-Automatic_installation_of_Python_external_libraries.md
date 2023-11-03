---
layout: single
title: "[python] 외부라이브러리 자동 설치"
classes: wide
categories:
  - python
---

# 파이썬 외부 라이브러리 자동 설치

```python

import sys
import subprocess

# 설치가 필요한 라이브러리를 리스트에 추가
package_list = ['yt_dlp', 'moviepy'] 

# pip 업그레이드
def upgrade_pip():
    subprocess.call([sys.executable, '-m', 'pip', 'install', '--upgrade', 'pip'])

# 외부 라이브러리를 설치
def install(package):
    #subprocess.call(['pip', 'install', package], stdout=subprocess.DEVNULL, stderr=subprocess.DEVNULL)
    subprocess.call(['pip', 'install', package])
    
def main(package_list):
    upgrade_pip()
    
    for package in package_list:
        try:
            __import__(package)
            print(f"'{package}' 모듈이 설치되어 있습니다.")
        except ImportError:
            print(f"'{package}' 모듈이 설치되어 있지 않습니다.")
            print(f"'{package}' 모듈을 설치합니다.")
            install(package)    

if __name__ == "__main__":
    main(package_list)

```
