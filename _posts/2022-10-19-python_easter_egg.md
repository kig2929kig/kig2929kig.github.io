---
layout: single
title: 파이썬 이스터 에그(Easter egg)
classes: wide
categories:
  - 잠시,멈춤
---  

# 파이썬의 선(禪)

파이썬 인터프리터에서 다음과 같이 입력하면 "파이썬의 선"이라는 글이 출력됩니다.
선이란 불교에서 선을 의미하는 것 같습니다. 선이란 무엇일까?  
인터넷 검색을 통해서 얻은 답은 "마음을 가다듬고 정신을 통일하여 깨달음의 경지에 도달하게 하는 불교수행법."이라고 합니다.

```python
import this
```

이쯤해서 출력 내용을 보면 아래와 같습니다.  
```
The Zen of Python, by Tim Peters

Beautiful is better than ugly.
Explicit is better than implicit.
Simple is better than complex.
Complex is better than complicated.
Flat is better than nested.
Sparse is better than dense.
Readability counts.
Special cases aren't special enough to break the rules.
Although practicality beats purity.
Errors should never pass silently.
Unless explicitly silenced.
In the face of ambiguity, refuse the temptation to guess.
There should be one-- and preferably only one --obvious way to do it.
Although that way may not be obvious at first unless you're Dutch.
Now is better than never.
Although never is often better than *right* now.
If the implementation is hard to explain, it's a bad idea.
If the implementation is easy to explain, it may be a good idea.
Namespaces are one honking great idea -- let's do more of those!
```
다음은 번역기를 돌려서 해석한 내용입니다.
```
1. 아름다운 것은 못생긴 것보다 낫다.
2. 명시적은 암시적보다 낫다.
3. 단순한 것이 복잡한 것보다 낫다.
4. 복잡한(complicated) 것보다 복잡한(complex) 것이 낫다. 
 - complex는 문제가 쉬운지 어려운지와는 상관없이 많은 요소와 단계, 항목으로 이루어진 것을 의미
 - complicated는 많은 요소와  단계, 항목은 상관없고, 문제가 풀기 복잡하고 여러운 경우
5. 플랫이 내포된 것보다 낫습니다.
 - 코드 중첩의 문제를 이야기하는 것 같습니다. 
 - 코드를 읽기 어렵다. 문맥을 이해하기 어렵다.
6. 빽빽한 것보다는 희박한 것이 낫다.
7. 가독성이 중요합니다.
8. 특별한 경우는 규칙을 어길 만큼 특별하지 않다.
9. 비록 실용이 순수함을 능가하지만.
10. 오류는 절대 묵묵히 지나쳐서는 안된다.
11. 명시적으로 침묵하지 않는 한
12. 모호함에 직면했을 때, 추측하고 싶은 유혹을 거부하라.
13. 그것을 할 수 있는 방법이 하나, 가급적이면 단 하나 있어야 합니다.
14. 비록 당신이 네덜란드인이 아닌 이상 처음에는 그 방법이 분명하지 않을 수도 있지만.
15. 지금이 없는 것보다 낫다.
16. 비록 결코 지금보다 낫지 않을 때가 많지만
17. 구현이 설명하기 어렵다면, 그것은 나쁜 생각이다.
18. 구현이 설명하기가 쉽다면 좋은 생각이 될 수 있다.
19. 네임스페이스는 경적을 울리는 훌륭한 아이디어입니다. 더 많은 것을 해보죠!
```
너무 난해한 문장들입니다. 하나씩 찾아보고 이해하는 노력이 필요하지만, 언제나 눈앞의 문제가 아니라서 귀찮은 마음이 큽니다. 여러분들이 댓글로 찾아서 알려주세요.  

파이썬 디자인 원리와 철학들의 목록인데, 언어를 이해하고 사용하는 데 도움이 됩니다. Python 설계에 대한 기본 원칙을 20개의 격언으로 간결하게 표현했으며 그 중 19개만 기록되었다고 합니다. 
어쨌든 재미있는 이스터 에그(?)입니다. 참고로 이스터 에그(Easter Egg)는 숨겨진 메시지를 뜻합니다.
  
목록을 작성한 Tim Peters는 Timsort 하이브리드 정렬 알고리즘을 만들고 Python 프로그래밍 언어 구현에 크게 기여한 것으로 알려진 미국 소프트웨어 개발자입니다. [위키백과](https://en.m.wikipedia.org/wiki/Tim_Peters_(software_engineer))




