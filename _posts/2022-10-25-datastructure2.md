

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
