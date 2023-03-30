# Pandas

### Pandas의 Series와 DataFrame
1차원, 1개의 column은 Series라고 부름

```python
pd.series([1,2,3,4])
```
```python
a = [1,2,3,4]
pd.series(a)

mylist = [1,2,3,4]
test = pd.series(mylist)
type(test)
```

### DataFrame
```python
# 2차원 리스트로 values값을 생성
subway1 = [['1호선','서울역', 17896, 15468],
           ['2호선','강남', 22794, 21657],
           ['3호선','신사', 24131, 25592]]
subway1
```

```python
df1 = pd.DataFrame(subway1)
df1
```
```python
df1.columns = ['노선명', '역명', '승차총승객수','하차총승객수']
df1
```

### dict로 만들기
```python
# 데이터프레임을 생성할 때, dict타입으로 생성하면, columns와 values를 입력하고 시작 
# dict의 key값은 column
# dict의 value는 values->리스트
subway2 = {'지하철노선':['1호선', '2호선', '3호선'], 
            '역명': ['서울역','강남','신사'], 
            '승차총승객수': [17896, 22794, 24131],
            '하차총승객수': [15468, 21657, 25592]
           }
df2 = pd.DataFrame(subway2)
df2
```
### index를 특정 column으로 지정하기
```python
df1.index = df1['노선명']
df1
```
### CSV파일 읽어오기
```python
# csv파일이 구글드라이브에 저장된 주소의 '약식 주소'
df = pd.read_csv('http://bit.ly/ds-korean-idol')
df

#맨앞의 5행의 데이터 출력
df.head()
# tail() : 맨 끝에서5개의 데이터를 출력한다.
df.tail()

# pandas에서 dtype이 object인 경우 -> 문자열
df.columns

#column(열)이름 재정의하기
new_col = ['name', '그룹', '소속사', '성별', '생년월일', '키', '혈액형', '브랜드평판지수']
df.columns = new_col
df.columns
df

#index 출력
df.index

# column의 갯수, 컬럼별 Not Null count의 갯수, 컬럼별 데이터 타입
df.info()

# df에서 describe함수를 호출하면 숫자(int64, float64)로 
# 되어 있는 컬럼만 통계 데이터를 확인할 수 있다.
df.describe()

# 형태(차원) 알아보기
# 데이터 프레임이 (행,열)-> (15행, 8열)
df.shape

# 정렬
# sort_index()함수는 index를 기준으로 정렬해주는 함수
df.sort_index()

#내림차순 index정렬
df.sort_index(ascending=False)

# column 별로 정렬
df.sort_values(by='키')

#내림차순 정렬
df.sort_values(by='키', ascending=False)

# 복수 정렬
# 정렬 기준 1번 :'키', 키가 동일한 경우 정렬기준 2번
df.sort_values(by=['키', '브랜드평판지수'])

df.sort_values(by=['키', '브랜드평판지수'], ascending=False)
```

