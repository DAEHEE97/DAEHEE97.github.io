---
layout: post
title:  "Divide_and_conquer"
date:   2022-03-24 13:52:54 +0900
categories: jekyll update
---

# 분할 정복 (divide and conquer)

- 큰 문제를 작은 문제로 나눠서(분할하여) 푸는(정복하는) 방법을 알고리즘 설계 기법


- 입력 크기가 커서 풀기 어려웠던 문제도 반복해서 잘게 나누다 보면 굉장히 쉬운 문제(종료 조건)가 되는 원리를 이용


---

## 병합 정렬 (Merge sort) 

- 병합 정렬은 주어진 문제를 절반으로 나눈 다음 각각을 재귀 호출로 풀어 가는 방식



```python
# 병합 정렬
# 입력 : 리스트 lst
# 출력 : 없음(입력으로 주어진 lst가 정렬됨)
 
def merge_sort(lst):
    
    n = len(lst)
    
    # 종료 조건: 정렬할 리스트의 자료 개수가 한 개 이하이면 정렬할 필요가 없음
    # 즉 자료가 한 개뿐이거나 아예 비어 있다면 정렬할 필요가 없으므로 return
    
    if n <= 1:
        return
    
    # 그룹을 나누어 각각 병합 정렬을 호출하는 과정
    
    mid = n // 2    # 중간을 기준으로 두 그룹으로 나눔
    g1 = lst[:mid]
    g2 = lst[mid:]
    merge_sort(g1)  # 재귀 호출로 첫 번째 그룹을 정렬
    merge_sort(g2)  # 재귀 호출로 두 번째 그룹을 정렬
    
    
    # 두 그룹을 하나로 병합
    
    i1 = 0
    i2 = 0
    ia = 0
    
    while i1 < len(g1) and i2 < len(g2):
        
        if g1[i1] < g2[i2]:
            lst[ia] = g1[i1]
            i1 += 1
            ia += 1
        
        else:
            lst[ia] = g2[i2]
            i2 += 1
            ia += 1 
            
    # 남아 있는 리스트 값 처리
    
    while i1 < len(g1):
        lst[ia] = g1[i1]
        i1 += 1
        ia += 1
        
    while i2 < len(g2):
        lst[ia] = g2[i2]
        i2 += 1
        ia += 1

```


```python
lst = [6, 8, 3, 9, 10, 1, 2, 4, 7, 5]
merge_sort(lst)

print(lst)
```

    [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]


### 병합정렬 알고리즘 분석

- 분할 정복을 이용한 병합 정렬의 계산 복잡도는 **O(n·logn)**으로 선택 정렬이나 삽입 정렬의 계산 복잡도 O(n2)보다 낮습니다. 


- 따라서 정렬해야 할 자료의 개수가 많을수록 병합 정렬이 선택 정렬이나 삽입 정렬보다 훨씬 더 빠른 정렬 성능을 발휘합니다.

### 병합정렬 활용

- 병합 정렬은 외부 정렬의 기본이 되는 정렬 알고리즘입니다.


- 연결 리스트에 있는 데이터를 정렬할 때에도 퀵 정렬이나 힙 정렬보다 훨씬 효율적입니다.


- 멀티코어 CPU와 다수의 프로세서로 구성된 그래픽 처리 장치의 등장으로 정렬 알고리즘을 병렬화하는 데에 합병 정렬 알고리즘이 활용

---

## 퀵 정렬 (Quicksort)

- 퀵 정렬(Quicksort)은 그룹을 둘로 나눠 재귀 호출하는 방식은 병합 정렬과 같지만, 그룹을 나눌 때 미리 기준과 비교해서 나눈다는 점이 다릅니다.


- 즉, 먼저 기준과 비교해서 그룹을 나눈 다음 각각 재귀 호출하여 합치는 방식입니다.


```python
# 퀵 정렬
# 입력 : 리스트 lst
# 출력 : 없음(입력으로 주어진 lst가 정렬됨)

# 리스트(lst) 에서 어디부터(start) 어디까지(end)가 정렬 대상인지 범위를 지정하여 정렬하는 재귀 호출 함수

def quick_sort_sub(lst, start, end):
    
    # 종료 조건: 정렬 대상이 한 개 이하이면 정렬할 필요가 없음
    # 즉 자료가 한 개뿐이거나 아예 비어 있다면 정렬할 필요가 없으므로 return

    if end - start <= 0:
        return
    
    # 기준 값을 정하고 기준 값에 맞춰 리스트 안에서 각 자료의 위치를 맞춤
    # [기준 값보다 작은 값들, 기준 값, 기준 값보다 큰 값들]
    
    pivot = lst[end]   # 편의상 리스트의 마지막 값을 기준 값으로 정함
    i = start
    
    for j in range(start, end):
        
        if lst[j] <= pivot:
            lst[i], lst[j] = lst[j], lst[i]
            i += 1
    
    lst[i], lst[end] = lst[end], lst[i]
    
    
    # 재귀 호출 부분
    
    quick_sort_sub(lst, start, i - 1) # 기준 값보다 작은 그룹을 재귀 호출로 다시 정렬
    quick_sort_sub(lst, i + 1, end)  # 기준 값보다 큰 그룹을 재귀 호출로 다시 정렬

    
# 리스트 전체(0 ~ len(lst) -1)를 대상으로 재귀 호출 함수 호출

def quick_sort(lst):
    quick_sort_sub(lst, 0, len(lst) - 1)


```


```python
lst = [6, 8, 3, 9, 10, 1, 2, 4, 7, 5]
quick_sort(lst)
print(lst)
```

    [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]


### 퀵 정렬 알고리즘 분석

- 퀵 정렬의 계산 복잡도는 최악의 경우 선택 정렬이나 삽입 정렬과 같은 O(n2)이지만, 평균적일 때는 병합 정렬과 같은 **O(n·logn)**입니다.



- 편의상 리스트의 마지막 값을 pivot 기준 값으로 정하였지만, 최악의 경우 pivot값이 리스트중 최대값 혹은 최소값일 경우 한쪽 그룸으로만 몰리게 되어, 퀵 정렬의 효율이 낮아집니다.



- 따라서 퀵 정렬 에서는 pivot 선정 기준을 정하는 것이 중요합니다.



- 하지만 다행히도 좋은 기준 값을 정하는 알고리즘에 관해서는 이미 많이 연구가 되어 있기 때문에 퀵 정렬은 대부분의 경우 O(n·logn)으로 정렬을 마칠 수 있습니다.

###  퀵 정렬의 피봇 선정 방법

1. 랜덤하게 선정하는 방법

 
2. **3개의 숫자의 중앙값으로 선정하는 방법 (Median of Three)**

- 가장 왼쪽 숫자, 중간 숫자, 가장 오른쪽 숫자 중에서 중앙값으로 피봇을 정합니다.

- 예를 들어, [31, 1, 26] 중에서 중앙값인 26을 피봇으로 사용하는 것입니다.


3. **Median-of-Medians**
-  배열을 3등분한 후, 각 부분에서 가장 왼쪽 숫자, 중간 숫자, 가장 오른쪽 숫자 중에서 중앙값을 찾은 후, 세 중앙값들 중에서 중앙값으로 피봇을 정합니다

### 퀵 정렬 활용

 
- 커다란 크기의 입력에 대해서 가장 좋은 성능을 보이는 알고리즘


- 실질적으로 어느 정렬 알고리즘보다 좋은 성능


- 생물 정보 공학(Bioinformatics)에서 특정 유전자를 효율적으로 접미 배열과 함께 활용

---

##  선택 문제 알고리즘 (Selection) 

- 선택(Selection) 문제는 n개의 숫자들 중에서 k번째로 작은 숫자를 찾는 문제입니다.


    - 선택 정렬(Selection Sort)과는 다른 알고리즘입니다.




```python
from random import randint

def partition(lst, left, right):
    pi = randint(left, right)
    if pi != left:
        lst[pi], lst[left] = lst[left], lst[pi]

    p = left + 1
    q = right
    
    while True:
        
        while p < right and lst[p] < lst[left]:
            p += 1
        
        while q > left and lst[q] > lst[left]:
            q -= 1
        
        if p >= q:
            break

        lst[p], lst[q] = lst[q], lst[p]
        p +=1
        q -=1

    lst[left], lst[q] = lst[q], lst[left]
    
    return q

def selection(lst, left, right, k):
    
    pivot = partition(lst, left, right)
    sgs = pivot - left
    
    if k < sgs:
        return selection(lst, left, pivot - 1, k)
    
    elif k == sgs:
        return lst[pivot]
    
    else:
        return selection(lst, pivot + 1, right, k - pivot - 1)

    

```


```python
k = 4
lst = [6, 18, 23, 19, 100, 11, 26, 4, 17, 5]

value = selection(lst, 0, len(lst) - 1, k - 1)
```


```python
value
```




    11



### good 분할과 bad 분할의 정의

- 분할된 두 그룹 중의 하나의 크기가 입력 크기의 3/4과 같거나 그보다 크게 분할하면 나쁜(bad) 분할이라고 정의합니다.


- 반대의 경우는 좋은 (good) 분할입니다.


 
- 예를 들어 다음과 같이 16개의 숫자가 있다면, 1 ~ 4, 13 ~ 16 사이의 숫자를 피봇으로 고른다면, Bad 분할, 5~ 12사이의 숫자를 고른다면, Good 분할이 됩니다.



- good 분할이 되는 피봇을 선택할 확률과 bad 분할이 되는 피봇을 선택할 확률이 각각 1/2로 동일합니다.



### 선택 문제 알고리즘 분석

- 피봇을 랜덤하게 정했을 때 good 분할이 될 확률이 1/2이므로 평균 2회 연속해서 랜덤하게 피봇을 정하면 good 분할을 할 수 있습니다.

 
- 그렇다면, 2회 연속해서 피봇을 정하면 무조건 good 분할을 한다는 가정하에, good 분할의 연속하여 이루어졌을 때만의 시간 복잡도를 구하여, 그 값에 2를 곱하면 평균 경우 시간 복잡도를 얻을 수 있습니다.


- 입력 크기가 n에서부터 3/4배로(최대 3/4 크기고, 실제로는 3/4보다 작은 크기일 수도 있음 편의상 3/4이라고 지칭) 연속적으로 감소되고, 크기가 1일 때에는 더 이상 분할할 수 없습니다.

 
- Selection함수에서는 O(입력크기)의 시간 복잡도를 가지므로, Selection 알고리즘의 시간 복잡도는 각 Selection함수 호출마다 걸린 시간을 다 더한 것의 시간 복잡도입니다.
 
 
- 따라서 **Selection의 알고리즘은 평균 2회에 good 분할이 되므로 2 x O(n) = O(n)** 입니다. 




### 선택 알고리즘 활용

- 데이터 분석을 위한 중앙값(median)을 찾는데 활용


- 데이터 분석에서 평균값도 유용하지만, 중앙값이 더 설득력 있는 데이터 분석을 제공

---

##  최근접 점의 쌍 찾기 알고리즘 (Closest Pair of Points) 


- 최근접 점의 쌍(Closest Pair)을 찾는 문제는 2차원 평면상의 n개의 점이 입력으로 주어질 때, 거리가 가장 가까운 한 쌍의 점을 찾는 문제로 분할 정복을 이용


- **n개의 점을 1/2로 분할**하여 각각의 부분 문제에서 최근접 쌍을 찾고, **2개의 부분 해 중에서 짧은 거리를 가진 점의 쌍**을 일단 찾습니다.


- 분할된 왼쪽 점 중에 하나, 오른쪽 점 중에 하나가 최근접점 쌍이 될 수 있으므로 취합할 때 중간 영역을 고려해야합니다.  




```python
import math
import copy

class Point():
    def __init__(self, x, y):
        self.x = x
        self.y = y

def dist(p1, p2):
    return math.sqrt((p1.x - p2.x) *
                     (p1.x - p2.x) +
                     (p1.y - p2.y) *
                     (p1.y - p2.y))


def bruteForce(P, n):
    min_val = float('inf')
    
    for i in range(n):
        
        for j in range(i + 1, n):
            
            if dist(P[i], P[j]) < min_val:
                
                min_val = dist(P[i], P[j])

    return min_val

def stripClosest(strip, size, d):
    min_val = d

    for i in range(size):
        j = i + 1
        
        while j < size and (strip[j].y -strip[i].y) < min_val:
            
            min_val = dist(strip[i], strip[j])
            j += 1

    return min_val

def closestUtil(P, Q, n):

    if n <= 3:
        return bruteForce(P, n)

    mid = n // 2
    midPoint = P[mid]
    Pl = P[:mid]
    Pr = P[mid:]

    dl = closestUtil(Pl, Q, mid)
    dr = closestUtil(Pr, Q, n - mid)

    d = min(dl, dr)

    stripP = []
    stripQ = []
    lr = Pl + Pr
    
    for i in range(n):
        
        if abs(lr[i].x - midPoint.x) < d:
            stripP.append(lr[i])
        
        if abs(Q[i].x - midPoint.x) < d:
            stripQ.append(Q[i])

    stripP.sort(key = lambda point: point.y) #<-- REQUIRED
    
    min_a = min(d, stripClosest(stripP, len(stripP), d))
    min_b = min(d, stripClosest(stripQ, len(stripQ), d))
    
    return min(min_a,min_b)

def closest(P, n):
    P.sort(key = lambda point: point.x)
    Q = copy.deepcopy(P)
    Q.sort(key = lambda point: point.y)

    return closestUtil(P, Q, n)

P = [Point(2, 3), Point(12, 30),
     Point(40, 50), Point(5, 1),
     Point(12, 10), Point(3, 4)]

n = len(P)

print("The smallest distance is", closest(P, n))
```

    The smallest distance is 1.4142135623730951


### 최근접 점의 쌍 찾기 알고리즘 분석


x좌표를 기준으로 정렬된 점 리스트 : S , SL(분활된 왼쪽), SR(분활된 오른쪽)

- S에 n개의 점이 있으면 전처리과정으로서 S의 점을 x-좌표로 정렬: **O(nlogn)**


- S에 3개의 점이 있는 경우에 3번, 2개의 점이면 1번 거리 계산이 필요: **O(1)**


- 정렬된 S를 SL과 SR로 분할하는데, 이미 배열에 정렬되어 있으므로, 배열의 중간 인덱스로 분할: **O(1)**


- 3개의 점의 쌍 중에서 가장 짧은 거리를 가진 점의 쌍을 리턴: O(1)


- 중간 영역의 점 계산으로 인하여 ClosestPair 알고리즘에서는 해를 취합하여 올라가는 과정에서 O(nlogn) 시간이 필요합니다. 


- k층까지 분할된 후, 층별로 수행되는 취합 과정에서 각 층의 수행 시간은 O(nlogn), 여기에 층 수인 logn을 곱하면 최종 시간복잡도인 **$O(n*log^2n)$** 을 얻을 수 있습니다.
