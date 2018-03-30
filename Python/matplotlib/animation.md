# matplotlib.animation
Python 프로그램의 시각화를 해주는 matplotlib에서 애니메이션효과를 주는 모듈?라이브러리?이다.

## 기본구조
<pre><code>
import numpy as np
import random as rd
import matplotlib.pyplot as plt
import matplotlib.animation as animation


def return_random_point_arr():
    point_arr = []
    
    for i in range(50):
        a = rd.random() * 2000
        b = rd.random() * 2000
        point_arr.append([a,b])
    return point_arr



point_arr1 = np.vstack(return_random_point_arr())
point_arr2 = np.vstack(return_random_point_arr())
point_arr3 = np.vstack(return_random_point_arr())


fig = plt.figure()

ax = fig.add_subplot(111)

ax.set_xlim((0,2000))
ax.set_ylim((2000,0))

point, = ax.plot([0], [0], 'bx')
point2, = ax.plot([0], [0], 'rx')
line, = ax.plot([], [], lw=1, c="black")

def init():
    point.set_data(([], []))
    point2.set_data(([], []))
    line.set_data(([], []))
    
    return (point,point2,line)

def animate(t):
    x = point_arr1[:t, 0]
    y = point_arr1[:t, 1]
    point.set_data(x, y)
    
    x = point_arr2[:t, 0]
    y = point_arr2[:t, 1]
    point2.set_data(x, y)
    
    x = point_arr3[:t, 0]
    y = point_arr3[:t, 1]
    line.set_data(x, y)
    
    return (point,point2,line)

ani = animation.FuncAnimation(fig=fig, func=animate, init_func=init, frames=60, blit=True)

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
