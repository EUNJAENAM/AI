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

```python
# 특정 컬럼만 불러오기
df['혈액형']
```

### 범위선택
```python
# 데이터프레임의 index중 행만 지정
# 처음 행부터 3행미만
df[:3]

# loc는 ','를 기준으로 앞에 것은 행, 뒤에 것은 열
# 처음부터 끝까지 -> 모든 행, '이름'컬럼만
df.loc[:, '이름']

# 모든 행, 열을 리스트로 지정했다는 의미는 여러 컬럼명을 넣기 위해
df.loc[:, ['이름', '생년월일']]

# loc는 3행부터 8행이하 
df.loc[3:8, ['이름', '생년월일']]

# 2행~5행, '이름' 컬럼 ~ '생년월일' 컬럼까지
df.loc[2:5, '이름':'생년월일']


# iloc도 ','를 기준으로 행과 열
# iloc는 열을 지정할때 숫자로 표현
df.iloc[:, [0, 2]]
```

### Boolean Indexing -조건을 활용한 색인
```python
# 검색조건
result = df['키'] > 180
result

# 검색조건
df['키']>180

# 검색조건에 해당하는 데이터의 행만 선택
df[df['키']>180]

Boolean Index 로 받은 Index 를 활용해서 True인 값만 색인해 낼 수 있습니다.
df[] 꺾쇠로 감싸주고, 그안에 Boolean Index를 넣어주시면 됩니다.

df[ df['키'] < 170]

df[df['그룹'].isnull()]

df[ df['키'] > 180 ]['이름']

#주의할 것은 '이름','키'를 2차원 리스트형태로 사용
df[ df['키'] > 180 ][['이름', '키']]

df.loc[ df['키'] > 180, '이름': '성별']

df.loc[ df['키'] > 180, ['이름', '키']]
```
### isin을 활용한 색인
isin을 활용한 색인은 내가 조건을 걸고자 하는 값이 내가 정의한 list에 있을 때만 색인하려는 경우에 사용합니다.
```python
my_condition = ['플레디스', 'SM']
# 검색조건 -> 소속사중에 플레디스 or SM이 있는지
df['소속사'].isin(my_condition)

df.loc[ df['소속사'].isin(my_condition) ]

df.loc[ df['소속사'].isin(my_condition),'이름' ]

df.loc[ df['소속사'].isin(my_condition), '소속사' ]
```

### 결측값 알아보기
NaN 값에 대하여
Null 값은 비어있는 값, 고~급 언어로 결측값입니다.
pandas 에서는 NaN => Not a Number 로 표기 된 것을 확인해 볼 수 있습니다.

```python

#결측치 확인
df.isna()

# series에서 null값을 확인
df['그룹'].isnull()

#NaN이 아닌 값 색출
df['그룹'][df['그룹'].notnull()]

df.loc[ df['그룹'].notnull(), ['키', '혈액형'] ]
```


