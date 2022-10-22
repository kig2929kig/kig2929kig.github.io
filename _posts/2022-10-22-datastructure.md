# 재귀(recursion)
> 어떤한 것을 정의할 때 자기 자신을 참조하는 것. 함수가 자신의 정의에 의해 정의될 때의 개념.

## 1. 재귀 알고리즘 
> 하나의 함수에서 자신을 다시 호출하여 작업을 수행하는 방식.

### 1. 수열
초항이 1이고, 공차가 4인 등차수열  
예) 1 5 9 13  

```python
def sequence(n) :
  if n == 1 :
    return 1
  else :
    return sequence(n-1) + 4

for i in range(1, 5) :
  print(sequence(i), end= " ")
```

    1 5 9 13 

### 2. 피보나치 수(Fibonacci numbers)  
첫번째 및 둘째 항이 1이며 그 뒤의 모든 항은 바로 앞 두 항의 합인 수열    
예) 1 1 2 3 5 8 13 21 34  

#### 2-1. 재귀함수를 이용한 피보나치 수  

```python
def fibo(n) :
  if n == 1 or n == 2 :
    return 1
  else :
    return fibo(n-1) + fibo(n-2)

for i in range(1, 10) :
  print(fibo(i), end = " ")
```
    1 1 2 3 5 8 13 21 34  


#### 2-2. 반복문을 이용한 피보나치 수

```python
def fib(n) :
  a, b = 1, 1
  if n == 1 or n == 2 :
    return 1
  
  for i in range(1, n) :
    a, b = b, a + b
  return a

for i in range(1,10) :
  print(fib(i), end = " ")
```

    1 1 2 3 5 8 13 21 34 

2-1, 2-2 예제의 수열의 항복을 100으로 증가시키면 재귀적 함수의 문제점을 확인할 수 있습니다.  

### 3. 팩토리얼(factorial)

1! = 1  
2! = 1 x 2  
3! = 1 x 2 x 3  
4! = 1 x 2 x 3 x 4  

```python
def factorial(n) :
  if n == 1 :
    return 1
  else :
    return factorial(n-1) * n

print(factorial(5))
```

```python
def fact(n) :
  sum = 1
  for i in range(1,n+1) :
    sum = sum * i
  
  return sum

print(fact(5))
```
