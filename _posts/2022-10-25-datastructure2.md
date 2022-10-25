---
layout: single
title: "[자료구조] 하노이 탑"
classes: wide
categories:
  - Data Structure
---


# 하노이 탑
> 퍼즐의 일종으로 3개의 기둥에 꽂을 수 있는 크기가 다른 원판들이 있습니다. 퍼즐의 규칙은 한 번에 한개의 원판만을 옮길 수 있고, 가장 위에 있는 원판만 이동할 수 있습니다.
> 또한, 큰 원판이 작은 원판 위에 있어서는 안 됩니다.

>하노이 탑 문제는 재귀 함수를 이용하여 풀 수 있는 가장 유명한 예제 중 하나입니다. 일반적으로 원판이 n개가 있다면, 2<sup>n</sup> -1 번의 이동으로 원판을 모두 옮길 수 있습니다.
>2<sup>n</sup> -1는 메르센 수라고 부르며, 2의 거듭제곱에서 1이 모자란 숫자를 말합니다.

> 한 번의 실수 없이 64개의 원판을 옮기는 데 2<sup>n</sup> - 1 = 18,446,744,073,709,551,615번을 움직여야 하고, 1초당 한 번 원판을 움직일 때, 584,554,049,253년이 걸립니다.
> 하노이 탑은 프랑스의 수학자인 **에두아르 뤼카**가 클라우스 교수라는 필명으로 1883년에 발표했습니다. 

[참조](https://ko.wikipedia.org/wiki/%ED%95%98%EB%85%B8%EC%9D%B4%EC%9D%98_%ED%83%91)

```python
import copy
import sys

TOTAL_DISKS = 5

COMPLETE_TOWER = list(range(TOTAL_DISKS, 0, -1))
#print(COMPLETE_TOWER)

def main() :
  towers = {'A':copy.copy(COMPLETE_TOWER), "B": [], "C": []}
  #print(towers["A"])

  while True :
    displayTowers(towers)
    fromTower, toTower = askForPlayerMove(towers)

    disk = towers[fromTower].pop()
    towers[toTower].append(disk)

    if COMPLETE_TOWER in (towers['B'], towers['C']) :
      displayTowers(towers)
      print("You have solved the puzzle! Well done!")
      sys.exit(0)

def askForPlayerMove(towers) :
  while True :
    print("Enter the letters of 'from' and 'to' towers, or QUIT.")
    response = input("> ").upper().strip()

    if response == 'QUIT' :
      print("Thanks for playing!")
      sys.exit()
    
    if response not in ('AB', 'AC', 'BA', 'BC', 'CA', 'CB') :
      print("Enter one of AB, AC, BA, CA, or CB.")
      continue
    
    fromTower, toTower = response[0], response[1]

    if len(towers[fromTower]) == 0 :
      print("You selected a tower with no disk.")
      continue
    elif len(towers[toTower]) == 0:
      return fromTower, toTower
    elif towers[toTower][-1] < towers[fromTower][-1] :
      print("Can\'t put larger disks on top of smaller ones.")
      continue
    else :
      return fromTower, toTower

def displayTowers(towers) :

  for level in range(TOTAL_DISKS, 0, -1):
    for tower in (towers['A'], towers['B'], towers['C']) :
      if level > len(tower) :
        displayDisk(0)
      else :
        displayDisk(tower[level-1])
    print()
  emptySpace = ' ' * (TOTAL_DISKS)
  print('{0} A{0}{0} B{0}{0} C\n'.format(emptySpace))
def displayDisk(width) :
  emptySpace = ' ' * (TOTAL_DISKS - width)

  if width == 0 :
    print(emptySpace + '||' + emptySpace, end='')
  else :
    disk = '@' * width
    numLabel = str(width).rjust(2, '_')
    print(emptySpace + disk + numLabel + disk + emptySpace, end='')

if __name__ == "__main__" :
  main()
```
