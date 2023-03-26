## Numpy 2
### arange를 이용해서 순서대로 리스트에 값 생성

```python
# 1~10까지의 값 생성
arr = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
arr

# atange 사용
# 첫번째 인자에는 Start 이상, 두번째 인자에는 Stop미만
arr = np.arange(start=11, stop=1, step=-1)
arr
```
### 차원 정렬
```python
#1차원 정렬
import numpy as np
arr = np.array([1, 10, 5, 8, 2, 4, 3, 6, 8, 7, 9])

np.sort(arr)  #오름차순
np.sort(arr)[::-1]     #내림차순

#결과 다름
np.sort(arr)
arr.sort()
```

### N차원 정렬
```python

arr2d = np.array([[5, 6, 7, 8], 
                  [4, 3, 2, 1],
                  [10, 9, 12, 11]])
arr2d.shape

# 열 정렬(왼쪽에서 오른쪽)
import numpy as np
# 가로방향 같은 행 데이터 안에서 정렬
np.sort(arr2d, axis=1)

# 행 정렬(위에서 아래로)
# 세로방향 열 데이터간의 정렬
np.sort(arr2d, axis=0)
```

### index를 반환하는 argsort
```python
#정렬된 값을 반환하는 것이 아닌 index를 반환합니다.

arr2d = np.array([[5, 6, 7, 8], 
                  [4, 3, 2, 1],
                  [10, 9, 12, 11]])
                  
# sort를 해야할 index의 순서를 리턴한다.
#열정렬
np.argsort(arr2d, axis=1)                  

#행정렬
np.sort(arr2d, axis=0)
```

### 행렬 연산

```python

#sum
a = np.array([[1, 2, 3], 
              [2, 3, 4]])

np.sum(a, axis=0)
np.sum(a, axis=1)
```

### Broadcasting

```python
#숫자의 연산(단일)
a = np.array([[1, 2, 3], 
              [2, 3, 4]])

# broadcast의 +연산은 행렬의 모든 요소에 동일한 값을 더한다.
a + 3              
```


