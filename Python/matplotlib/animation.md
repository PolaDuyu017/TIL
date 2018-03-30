# matplotlib.animation
Python 프로그램의 시각화 한다.

## 기본구조
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
ani = animation.FuncAnimation(fig, animate, frames=len(x), fargs=(K,),
                              interval=100, blit=True)
plt.show()