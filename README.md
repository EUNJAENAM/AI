### 파이썬을 쉬운 언어이다
```python
if 5 in [1,2,3,4]:print("4가 있습니다")
```

### 사칙연산
## %나머지  //몫  **제곱
```python
3 + 1
```
### 변수에 숫자 대입하고 계산하기
```python
a = 3
b = 1
c = a + b
```
### 자료형-문자열(String)
```python
"life is too short, You need Python"

a = "Python"
b = " is fun"
a + b

a * 2

print("-" * 20)
```
### 문자열 슬라이싱
```python
a = "I Like the weather today"
a[2:6]
```

###문자열포맷팅
```python
"I have %d apples" %3

"오늘은 %d월 %d일 %s요일 입니다." %(6,27,"월")

hour = 1
"나는 {0} {1}시간 공부했다".format("오늘",hour)

from datetime import datetime

y = datetime.today().year
m = datetime.today().month
d = datetime.today().day
h = datetime.today().hour
print("오늘은 %d월 %d일 %d시 입니다."%(m,d,h))
print("오늘은 {0}월 {1}일 {2}시 입니다.".format(m,d,h))

```

### 문자관련 함수들
```python
# 문자 개수세기
a = "happy"
a.count('p'
a

# 위치 알려주기, 값이 없으면 -1
a.find('c')

# 위치 알려주시, 값이 없으면 오류
a.index('c')

# 문자열 삽입
",".join('abcde')

# 소문자를 대문자로 바꾸기
a.upper()

# 대문자를 소문자로 바꾸기
a.lower()

# 공백지우기
a = '   happy    '
a.lstrip()
a.rstrip()
a.strip()

#문자열 바꾸기
a = "life is too short"
a.replace("life', 'your leg')

# 문자열 나누기
a = "life is too short"
a.split()

b = 'a l:b:c:d"
b.split(":")
```



