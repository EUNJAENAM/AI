### loc/iloc
```python
if 5 in [1,2,3,4]:print("4가 있습니다")

a = 3
b = 1
c = a + b

'------------------------
print('"life is too short, You need Python"')

a = "Python"
b = " is fun"
a + b

'---------------------------------------
a = "나는 로봇입니다"
b = a[:3] + "사람" + a[-3:]
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
