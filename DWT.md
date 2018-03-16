Dynamic Time Warping Dynamic 
Time Warping 的目标是比较两个依赖于时间的序列 $X:=(x_1, x_2, \cdots, x_N), Y:=(y_1, y_2,\cdots, y_M)$，这些序列可以是离散信号（时间序列），或者更一般地，是在等距时间点采样的特征序列。记 $\mathcal{F}$为特征空间，则 $x_n, y_m\in\mathcal{F},n\in[1:N],m\in[1:M]$。为了比较两个不同的特征 $x,y\in\mathcal{F}$，需要引入一个局部花费度量（local cost measure），有时也称为局部距离度量（local distance measure），其定义为$c:\mathcal{F}\times\mathcal{F}\to\mathbb{R}_{\ge0}$
通常情况下，如果 $x$ 与 $y$ 相似，$c(x,y)$ 会比较小，否则会很大。通过计算序列 $X$ 和 $Y$ 的每个元素形成的数对的局部花费度量，可以得到花费矩阵 $C\in\mathbb{R}^{N\times M}$，定义为 $C(n,m):=c(x_n,y_m)$。那么我们的目标是寻找 $X$ 与 $Y$ 之间拥有最小整体花费的alignment。

**定义**  一个 $(N,M)-warping path$ 是一个序列 $p=(p_1,p_2,\cdots,p_L)$，其中 $p_l=(n_l,m_l)\in[1:N]\times[1:M],l\in[1:L]$ 满足下面三个条件：
1. 边界条件：$p_1=(1,1),\ p_L={N,M}$
2. 单调条件：$n_1\le n_2\le\cdots\le n_L,\ m_1\le m_2\le\cdots\le m_L$
3. 步长条件：$p_{i+1}-p_i\in\{(1,0),(0,1),(1,1)\},\ l\in[1:L-1]$
