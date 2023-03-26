## Numpy - n차원 배열 객체, 행렬연산과 비슷한 연산

###numpy 패키지를 np라는 별칭으로 불러오기
패키지 버전 확인하기

```python
import numpy as np
print(np.__version__)
```
### np array 생성
```python
arr = np.array([1,2,3,4], dtype=int)
arr
```
###type 확인
```python
type(arr)
```
### list로부터 생성하기
```python
mylist1 = [1, 2, 3, 4]
arr1 = mp.array(mylist1)
arr1
```
```python
mylist2 = [[1, 2, 3, 4],
           [5, 6, 7, 8]]
arr2 = mp.array(mylist2)
arr2
```

### shape 확인하기
```python
arr1.shape
```
```python
arr2.shape
```
### array에서의 data타입
```python
mylist=[1, 3.14, 'hello', '1234]
mylist
```
```python
mylist[1]
```
```python
mylist[2]
```
```python
arr = np.array([1, 2, 3, 3.14])
arr
```
```python
arr = np.array([1, 2, 3, 3.14], dtype=int)
arr
```
```python
arr = np.array([1, 3.14, 'abc', '1234'])
arr
```
```python
arr[0] + arr[1]
```
```python
arr = np.array([1, 3.14, '1234'], dtype=int)
arr
```

#### python에서 range함수를 사용하여 list를 생성할 수 있다.
```python
myList = list(range(10))
arr0 = np.array(myList)
arr0
```
```python
#1차원
arr = np.array([0, 1, 2, 3, 4, 5, 6, 7, 8, 9])

#2차원
arr2d = np.array([[1, 2, 3, 4], 
                  [5, 6, 7, 8], 
                  [9, 10, 11, 12]])           
```

### Boolean 인덱싱
조건 필터링을 통하여 Boolean값을 이용한 색인

```python
arr = np.array([1, 2, 3, 4, 5, 6, 7])
arr2d = np.array([[1, 2, 3, 4], 
                  [5, 6, 7, 8], 
                  [9, 10, 11, 12]])
                  
#True와 False 값으로 색인하기
arr>2

arr[arr>2]

myTrueFalse = [True, False, True, False, True, False, True]
arr[myTrueFalse]
```

###조건 연산자를 활용하여 필터 생성
```python
# result에는 boolean index배열이 저장된다.
result = arr2d > 2
```
필터를 활용하여 필터에 True 조건만 색인 합니다.
이럴 때 꺾쇠 괄호로 한 번 더 묶어만 주면 됩니다. (꺾쇠 괄호 안에 조건문 삽입)
arr2d[조건필터]

```python
arr2d = np.array([[1, 2, 3, 4], 
                  [5, 6, 7, 8], 
                  [9, 10, 11, 12]])
arr2d[ arr2d > 2 ]

arr2d[ arr2d < 5 ]
```
