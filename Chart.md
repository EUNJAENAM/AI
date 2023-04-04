# Chart

### subplot  (여러개의 Chart 그리기)
```python

import matplotlib.pyplot as plt

sub_plots = plt.subplots(3, 2)   #subplot개체 생성

fig = sub_plots[0]       #plot의  figure정보를 담고 있는 객체
graph = sub_plots[1]     #배치된 좌표평면에 대한 정보

fig.suptitle('Multiple plots')
fig.tight_layout(pad=2)
plt.show()

f, ax = plt.subplots(1,2, figsize=(12,6))
# ax는 왼쪽이냐 오른쪽이냐
# ax[0]는 왼쪽, ax[1]는 오른쪽
 
# plot.pie()함수를 사용하여 원형 차트
df['Survived'].value_counts().plot.pie(explode=[0,0.05], autopct='%1.3f%%', ax=ax[0])
ax[0].set_title('Survived')

# seaborn의 countplot()함수를 사용하여 바 차트
sns.countplot(x=df['Survived'], ax=ax[1])
ax[1].set_title('Survived')

# plt.show()
```
