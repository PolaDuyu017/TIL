# matplotlib.animation
Python 프로그램의 시각화 한다.

## 기본구조
<pre><code>
import matplotlib.pyplot as plt 
import matplotlib.animation as animation
import numpy as np

data = np.vstack([[1,1],[2,2],[3,3],[4,4],[5,5]])

x = data[:,0]
y = data[:,1]

fig = plt.figure()
ax = fig.add_subplot(111)
line, = ax.plot([],[], '-')
line2, = ax.plot([],[],'--')
ax.set_xlim(np.min(x), np.max(x))
ax.set_ylim(np.min(y), np.max(y))

def animate(i,factor):
    line.set_xdata(x[:i])
    line.set_ydata(y[:i])
    line2.set_xdata(x[:i])
    line2.set_ydata(factor*y[:i])
    return line,line2

K = 0.75 # any factor
ani = animation.FuncAnimation(fig, animate, frames=len(x), fargs=(K,), interval=100, blit=True)
plt.show()
</code></pre>

## 요소 설명
figure : matplotlib로 시각화를 할때 바탕이 되는 창 1개를 의미  
subplot : figure안에서 그림이 그려지는 영역  
def init() : animate를 초기화하는 함수  
def animate() : 애니메이션이 가지는 변수들을 조작하는 함수  
animation.FuncAnimation : matplot의 애니메이션 시각화의 주요 구현체

## 주의사항
기본적으로 animation.FuncAnimation는 figure 1개에 하나만 존재해야지 오류가 나지않음
