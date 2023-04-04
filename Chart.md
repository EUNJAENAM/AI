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
```
