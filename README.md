import numpy as np
import matplotlib.pyplot as plt
import matplotlib.animation as animation

# 하트 형태의 수학적 방정식
def heart_shape(t):
    x = 16 * np.sin(t)**3
    y = 13 * np.cos(t) - 5 * np.cos(2*t) - 2 * np.cos(3*t) - np.cos(4*t)
    return x, y

# 초기 입자 좌표 생성
n = 1000  # 입자 수
t = np.linspace(0, 2 * np.pi, n)
x, y = heart_shape(t)

# 입자에 약간의 노이즈 추가
x += np.random.normal(0, 0.3, size=n)
y += np.random.normal(0, 0.3, size=n)

# 애니메이션 업데이트 함수
def update(frame):
    factor = 1 + 0.1 * np.sin(frame * 0.2)
    scat.set_offsets(np.c_[x * factor, y * factor])
    return scat,

# 플롯 설정
fig, ax = plt.subplots(figsize=(6, 6))
ax.set_facecolor('black')
ax.set_xlim(-20, 20)
ax.set_ylim(-20, 20)
ax.axis('off')

# 산점도 생성
scat = ax.scatter(x, y, c='magenta', s=1, alpha=0.8)

# 애니메이션 생성
ani = animation.FuncAnimation(fig, update, frames=100, interval=50, blit=True)

plt.show()
