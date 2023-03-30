# pandas2

```python
import pandas as pd

df = pd.read_csv('https://bit.ly/ds-korean-idol')

# df의 모든 '이름'컬럼을 0으로 변경
new_df['이름'] = 0

new_df.head()

```

```python
# 갯수를 세는 count함수
df['키'].count()

#df['키']값을 낮은 값에서 높은 값으로 sort()하고, 
# 그중에 가운데 위치한 값을 중앙값이라고 한다.

df['키'].median()

가장 많이 관측되는 수, 주어진 데이터에서 가장 갯수가 많은 값
df['키'].mode()
```

### 피벗테이블
피벗테이블은 엑셀의 피벗테이블과 동일합니다.
데이터 열 중에서 두 개의 열을 각각 행 인덱스, 열 인덱스로 사용하여 데이터를 조회하여 펼쳐놓은 것을 의미합니다.
왼쪽에 나타나는 인덱스를 행 인덱스, 상단에 나타나는 인덱스를 열 인덱스라고 부릅니다.
```python
# 빅히트 지민과 정국이 같은 소속사이고 혈액형도 같은 경우
# 평균값으로 표현
# doc ref : https://pandas.pydata.org/docs/reference/api/pandas.pivot_table.html 

# index는 행 인덱스
# columns는 열 인덱스
# values는 조회하고 싶은 값
pd.pivot_table(df, index='소속사', columns='혈액형', values='키')

# aggfunc에는 추가 계산 옵션 (np.sum, np.mean) - 기본값은 평균
pd.pivot_table(df, index='그룹', columns='혈액형', values='브랜드평판지수', aggfunc=np.mean)

```

### GroupBy
groupby는 데이터를 그룹으로 묶어 분석할 때 활용합니다.
소속사별 키의 평균, 성별 키의 평균 등 특정, 그룹별 통계 및 데이터의 성질을 확인하고자 할 때 활용합니다.

```python
df.groupby('소속사')

# 소속사를 기준으로 데이터의 갯수를 확인
df.groupby('소속사').count()

# df중에서 수치 데이터에 대해서만 mean()를 실행
df.groupby('그룹').mean()

df.groupby('성별').sum()

# 특정열만 출력
df.groupby('혈액형')['키'].mean()

# 행 인덱스를 복합적으로 구성하고 싶은 경우는 인덱스를 리스트로 만들어 줍니다.
df.groupby(['혈액형', '성별']).mean()

# 데이터 재구조화
df2.unstack('혈액형')

df2.unstack('성별')

# index를 새로 매긴다.
df2 = df2.reset_index()
```

### 결측값 채우기 fillna

```python
df['키']

# NaN값을 찾아서 NaN인 경우 그 데이터를 특정값(-1)으로 채워주는 함수
df['키'].fillna(-1)

# df2의 결측치를 -1로 변경하고 df2에 저장
# inplace=True -> df2에 결과값을 저장

# 아래 코드는 df2['키'] = df2['키'].fillna(-1)와 같다.
df2['키'].fillna(-1, inplace=True)

# 결측치를 평균값, 중앙값, 최빈값으로
height = df2['키'].median()

# '키'의 결측치를 최빈값(mode)으로 채운다.
# 또는 평균값(mean), 중앙값(median)

df2['키'].fillna(height, inplace=True)
```

### 빈 값(NaN)이 있는 행을 제거

```python
# 결측치가 있는 행을 삭제
df.dropna()

# axis=0은 행을 드랍합니다.
df.dropna(axis=0)

# 결측치가 있는 그룹, 키 컬럼이 삭제된 것을 확인할 수 있다.
df.dropna(axis=1)

# dropna()와 같은 함수 실행시 인덱스가 변경될때, 다시 인덱스값을 부여할 때 
df.reset_index(drop=True)

# how='any' 행에서 하나의 컬럼 정보라도 NaN이면 그 행의 데이터 삭제
df.dropna(axis=0, how='any')

# how='all'는 행에 모든 정보가 NaN인 경우에는 데이터 삭제
df.dropna(axis=0, how='all')

# 10번째행에 전체가 NaN인 행이 추가
df.iloc[10] = np.nan

df.dropna(axis=0, how='all')
```
### column의 중복값 제거

```python

df['키']
df['키']=df['키'].fillna(178.0)

# 첫번째 데이터만 남기고 나머지는 다 삭제
df['키'].drop_duplicates()

```

### Drop-Column/row 제거

```python

# drop()을 활용하여 column을 제거할 수 있습니다. column을 제거할 때는 axis=1 옵션을 줍니다.
df.drop('그룹', axis=1)

# drop()을 활용하여 row를 제거할 수 있습니다. 
# row를 제거할 때는 제거하고자하는 index와 axis=0 옵션을 줍니다.

df.drop(3, axis=0)

###   8번 정리할 차레



