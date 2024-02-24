---
sidebar_position: 1
description: 了解前缀和通项问题的基本技能．
---

# 求和问题基础

求和，指的是求数列的前缀和通项．高中数学中，需要掌握的 **可求前缀和通项** 的数列共有三种：

- **等差、等比** 数列．
- **等差乘等比** 数列．
- **裂项** 求和数列．

第一条最普通的等差、等比数列在前面的页面已经介绍，接下来介绍剩下的两类数列的前缀和求法．

## 等差乘等比数列

> 已知等比数列 $\{a_n\}$，公比 $q$，等差数列 $\{b_n\}$，公差 $d$，求 $\{a_n \cdot b_n\}$ 的前缀和 $S_n$．

这是一类套路题，属于必会类型，只需要按照下面的操作按部就班计算即可．

我们规定 $q \ne 1$（下面的操作会用到这个条件）．$q = 1$ 的情形与纯等差数列前缀和是一样的．

错位相减法：

$$
\begin{matrix}
S_n  & = & a_1 \cdot b_1 & + & a_2 \cdot b_2 & + & a_3 \cdot b_3 & + & \cdots & + & a_n \cdot b_n       &   & \\
qS_n & = &               &   & a_2 \cdot b_1 & + & a_3 \cdot b_2 & + & \cdots & + & a_n \cdot b_{n - 1} & + & a_{n + 1} \cdot b_n
\end{matrix}
$$

上减下（比下减上的负号少，更顺脑子）：

$$
(1 - q)S_n = a_1 \cdot b_1 - a_{n + 1} \cdot b_n + d(a_2 + a_3 + \cdots + a_n)
$$

$a_2 + a_3 + \cdots + a_n$ 可以使用等比数列求和公式：

$$
a_2 + a_3 + \cdots + a_n = a_1q \cdot \df{q^{n - 1} - 1}{q - 1}
$$

这里有一个小细节：$n = 1$ 时 $a_2 + a_3 + \cdots + a_n$ 为空，习惯上分类讨论．然而等比等差数列求和公式代入项数 $=0$ 的结果为 $0$，所以不讨论也完全正确，在这类题型中一般省略这种讨论．

因此最后的式子就是

$$
(1 - q)S_n = a_1 \cdot b_1 - a_{n + 1} \cdot b_n + a_1dq \cdot \df{q^{n - 1} - 1}{q - 1}
$$

最后将 $1 - q$ 除过去即可（**这步千万别忘了**）．

识别等差乘等比数列：

- 字面意思地给出：已知等比数列 $\{a_n\}$，等差数列 $\{b_n\}$，则 $\{a_n \cdot b_n\}$ 为等差乘等比数列．
- 给出通项：通项形如 $\{(xn + y) \cdot q^n\}$，即 **一个一次函数乘上一个幂函数** 的数列都是等差乘等比数列，如 $\{(3n+1)2^n\}$，$\{\df{n + 1}{2^n}\}$．

:::info 例题 1.1

已知 $a_n = \df{2n - 7}{3^n}$，求其前缀和 $S_n$．

:::

:::tip 例题 1.1 解答（写在卷子上的过程）

$$
\begin{matrix}
S_n  & = & \df{-5}{3^1} & + & \df{-3}{3^2} & + & \df{-1}{3^3} & + & \cdots & + & \df{2n - 7}{3^n}       &   & \\[1em]
\df 1 3 S_n & = &               &   & \df{-5}{3^2} & + & \df{-3}{3^3} & + & \cdots & + & \df{2n - 9}{3^n} & + & \df{2n - 7}{3^{n + 1}}
\end{matrix}
$$

（细节一：为了后面错位相减的直观，这里 **不应** 把每一项写成 **最简形式**，保留 **等差乘等比** 的形式即可；且可以将等差的结果展开算出，但 **不要展开等比的幂次**（即不用把 $3^2$ 写成 $9$ 等），因为没必要．）

上减下得

$$
\df 2 3 S_n = \df{-5}{3^1} + \df{2}{3^2} + \df{2}{3^3} + \cdots + \df{2}{3^n} \red{-} \df{2n - 7}{3^{n + 1}}
$$

（细节二：注意最后是减号，不要因为前面都是加号就跑偏了！）

$$
\df 2 3 S_n = -\df{5}{3} + \df{\df 2 9  [ 1 - (\df 1 3 )^{\red{n - 1}}]}{1 - \df 1 3} - \df{2n - 7}{3^{n + 1}}
$$

（细节三：中间使用等比数列求和公式时注意是 $n - 1$ 项！）

最后化简得

$$
\red{\df 2 3} S_n = - \df 4 3 - \df{2n - 4}{3^{n + 1}}
$$

（细节四：由于这里的化简计算过程比较辛苦，算出结果后很容易直接把它当成最终答案，但别忘了 $S_n$ 左侧还有系数！）

因此 $S_n = \df 3 2 (- \df 4 3 - \df{2n - 4}{3^{n + 1}}) = -2 - \df{n - 2}{3^n}$．

:::

:::info 例题 1.2

已知数列 $\{a_n\}$ 满足 $a_1 = 2$，$a_{m + n} = a_m + a_n, \quad m, n \in \N^\ast$，设 $b_n = \{\lfloor \log_2 a_n \rfloor\}$，$\{b_n\}$ 前缀和为 $\{S_n\}$，求：

（1）$S_{20}$ 的值．

（2）$\{S_{2^n}\}$ 的通项．

:::

:::tip 例题 1.2 解答

$a_{m + n} = a_m + a_n$ 等价于 $\{a_n\}$ 为首项与公差相等的等差数列，即 $a_n = 2n$．

考察 $\{b_n\}$ 数列的取值，容易发现 $b_n$ 的值为满足 $2^k \le a_n < 2^{k + 1}$ 的唯一正整数 $k$．

根据 $a_n = 2n$，又可知 $b_n$ 的值为满足 $2^{k - 1} \le n < 2^k$ 的唯一正整数 $k$．

即

- $2^0 \le n < 2^1$ 时，$b_n = 1$．
- $2^1 \le n < 2^2$ 时，$b_n = 2$．
- $2^2 \le n < 2^3$ 时，$b_n = 3$．
- $2^3 \le n < 2^4$ 时，$b_n = 4$．
- $2^4 \le n < 2^5$ 时，$b_n = 5$．
- ……

（1）

$S_{20}$ 的值为 $1 \times 1 + 2 \times 2 + 4 \times 3 + 8 \times 4 + 5 \times 5 = 74$．

（2）

考虑 $b_1$ 到 $b_{2^n}$ 的分布，其应为：$1$ 个 $1$，$2$ 个 $2$，$4$ 个 $3$，$8$ 个 $4$……$2^{n - 1}$ 个 $n$，以及 $1$ 个 $n + 1$．

最后的 $n + 1$ 拎出单算，前面的和构成一个等差乘等比数列的前缀和

$$
t = 1 \times 1 + 2 \times 2 + 4 \times 3 + \cdots + 2^{n - 1} \times n
$$

该式减去该式 $\times 2$ 的结果为

$$
\begin{aligned}
-t &= 1 \times 1 - 2^n \times n + 1 \times (2 + 4 + 8 + \cdots + 2^{n - 1}) \\
&= 1 - n \cdot 2^n + 2^n - 2 \\
&= (1 - n) \cdot 2^n - 1
\end{aligned}
$$

因此 $t = (n - 1) \cdot 2^n + 1$，$S_{2^n} = t + n + 1 = (n - 1) \cdot 2^n + n + 2$．

:::

注意到等差乘等比数列的计算比较繁杂，一些验证自己算对的手段是有必要的：

- $\{(xn + y) \cdot q^n\}$ 的前缀和形如 $\{(Xn + Y) \cdot q^n + C\}$．两侧一次函数的系数与常数 **可能不同**，幂的底 **一定相同**，且前缀和在 **最外面会多一个常数**．
- 因为原数列不分段，算出来的前缀和一定有 $S(0) = 0$，这等价于 $C + Y = 0$．因此，可以更进一步说 $\{(xn + y) \cdot q^n\}$ 的前缀和形如 $\{(Xn + Y) \cdot q^n - Y\}$．

因此可以检查自己的计算结果 $\{S_n\}$ 是否满足：

- 符合结构 $\{(Xn + Y) \cdot q^n - Y\}$．
- 满足 $S_1 = a_1$．

如果两个条件有一个不满足说明 $\{S_n\}$ 一定算错了，如果都满足说明很大概率算对．

## 裂项

裂项指的是对一类分式：**分母能因式分解为两不等项之积** 的分式——$\df{a}{pq}$ 的处理策略（$p \ne q$，下面会将 $p$ 与 $q$ 称作分式 $\df{a}{pq}$ 的「两个分母」）：

$$
\df{c}{pq} = \df c {q - p} (\df 1 p - \df 1 q )
$$

**括号外分式的形式** 是 $\df{分子}{分母差}$，且括号外分母相减的顺序与括号内恰好 **相反**．这个裂项形式应当 **熟练掌握**．

通常情况下题目会将 $p$ 与 $q$ 设计为正数，此时令 $p$ 为 **较小的** 分母，$q$ 为 **较大的** 分母比较合适，因为这样以来 $\df c {q - p}$ 与 $\df 1 p - \df 1 q$ 都是正的．

裂项可以解决一类 **分式求和** 问题，对于

$$
S_n = \df{c_1}{p_1q_1} + \df{c_2}{p_2q_2} + \cdots + \df{c_n}{p_nq_n}
$$

如果满足以下两个条件：

- $\df{c_n}{q_n - p_n}$（$\df{分子}{分母差}$）是一个 **与 $n$ 无关的常数**（设为 $C$）.
- $p_n$ 与 $q_n$ 可以刻画为 **同一个数列** $\{b_n\}$ 的第 $n$ 项与第 $n + k$ 项，$k$ 是一个常数．

那么它就可以裂项求和：

$$
\begin{aligned}
S_n &= \df{c_1}{p_1q_1} + \df{c_2}{p_2q_2} + \cdots + \df{c_n}{p_nq_n} \\[1em]
&=
\df{c_1}{q_1 - p_1}(\df 1 {p_1} - \df 1 {q_1}) + \df{c_2}{q_2 - p_2}(\df 1 {p_2} - \df 1 {q_2}) + \cdots +
\df{c_n}{q_n - p_n}(\df 1 {p_n} - \df 1 {q_n}) \\[1em]
&= C(\df 1 {p_1} - \df 1 {q_1} + \df 1 {p_2} - \df 1 {q_2} + \cdots + \df 1 {p_n} - \df 1 {q_n}) \\[1em]
&= C[
(\df 1 {p_1} + \df 1 {p_2} + \cdots + \df 1 {p_n}) -
(\df 1 {q_1} + \df 1 {q_2} + \cdots + \df 1 {q_n})
] \\[1em]
&= C[
(\df 1 {b_1} + \df 1 {b_2} + \cdots + \df 1 {b_n}) -
(\df 1 {b_{k + 1}} + \df 1 {b_{k + 2}} + \cdots + \df 1 {b_{k + n}})
]
\end{aligned}
$$

考察

$$
(\df 1 {b_1} + \df 1 {b_2} + \cdots + \df 1 {b_n}) -
(\df 1 {b_{k + 1}} + \df 1 {b_{k + 2}} + \cdots + \df 1 {b_{k + n}})
$$

可以视作数列 $\{\df 1 {b_n}\}$ 的 **两个连续段相减** 的形式，对于这种形式我们有专门的处理策略：

设 $\{\df 1 {b_n}\}$ 的前缀和为 $\{T_n\}$，则考察对象为 $T_n - (T_{n + k} - T_k) = T_n + T_k - T_{n + k}$．从这个式子可以看出，**考察对象的 $n$ 与 $k$ 互换，结果不变**．

因此考察对象等于

$$
(\df 1 {b_1} + \df 1 {b_2} + \cdots + \df 1 {b_k}) -
(\df 1 {b_{n + 1}} + \df 1 {b_{k + 2}} + \cdots + \df 1 {b_{k + n}})
$$

有

$$
S_n = C[
(\df 1 {b_1} + \df 1 {b_2} + \cdots + \df 1 {b_k}) -
(\df 1 {b_{n + 1}} + \df 1 {b_{k + 2}} + \cdots + \df 1 {b_{k + n}})
]
$$

最后一步 $n$，$k$ 互换的目的是：$n$ 是一个变量，而 $k$ 是一个常数，我们可能做不到求 $n$ 项的和，但一定能做到求 $k$ 项的和，因此求和完毕．

:::info 例题 2.1

求 $a_n = \df 1 {n(n + 2)}$ 的前缀和．

:::

:::tip 例题 2.1 解答

对每个 $a_n$ 裂项：

$$
S_n = \df 1 2(1 - \df 1 3 + \df 1 2 - \df 1 4 + \cdots + \df 1 n - \df 1 {n + 2})
$$

括号里的式子如何进一步化简：

$$
\begin{aligned}
& \phantom = 1 - \df 1 3 + \df 1 2 - \df 1 4 + \cdots + \df 1 n - \df 1 {n + 2} \\
& \red= (1 + \df 1 2 + \cdots + \df 1 n) - (\df 1 3 + \df 1 4 + \cdots + \df 1 {n + 2}) \\
& \red= 1 + \df 1 2 - (\df 1 {n + 1} + \df 1 {n + 2} ) \\[1em]
& = \df 3 2 - \df{2n + 3}{(n + 1)(n + 2)}
\end{aligned}
$$

因此 $S_n = \df 3 4 - \df{2n + 3}{2(n + 1)(n + 2)}$．

保留上面这个形式就已经足够了，如果乘开，结果是 $\df{3n^2 + 5n}{4n^2 + 12n + 8}$．

:::

:::warning 解题细节

第一个红色等号我们 **将正与负分类开**，写成 **两段连续的和相减的形式**，推荐读者也这么做，因为

$$
(1 + \df 1 2 + \cdots + \df 1 n) - (\df 1 3 + \df 1 4 + \cdots + \df 1 {n + 2})
$$

这种分类隔开的形式，一定比

$$
1 - \df 1 3 + \df 1 2 - \df 1 4 + \cdots + \df 1 n - \df 1 {n + 2}
$$

这种混在一起的式子 **更加直观，好处理**，是一个解题好习惯．

:::

:::note 有关第二个红色等号

来看这一步：

$$
\begin{aligned}
& \phantom = (1 + \df 1 2 + \cdots + \df 1 n) - (\df 1 3 + \df 1 4 + \cdots + \df 1 {n + 2}) \\
& = 1 + \df 1 2 - (\df 1 {n + 1} + \df 1 {n + 2} )
\end{aligned}
$$

这一步笔者给出的理解是：$\{\df 1 n\}$ 的前缀和 $\{T_n\}$，有 $T_n - (T_{n + 2} - T_2) = T_2 - (T_{n + 2} - T_n)$，将两段长度为 $n$ 的和相减转化为长度为 $2$ 的和相减．

但在更普遍，或许也更好理解的教学中，一般会称这一步是「相消」的体现．在相消法中的解释是：

> 两个括号内重叠的部分 $\df 1 3 + \df 1 4 + \cdots + \df 1 n$ 可以消去，只剩下了 $1 + \df 1 2 - (\df 1 {n + 1} + \df 1 {n + 2} )$．

其实一部分敏锐的读者能看出这个操作存在一些逻辑疏漏——这个「相消」似乎在默认「$n$ 足够大」．如果 $n$ 比较小的时候，还存在这样的「消」吗？

更具体地，这个解释在 $n > 2$ 时都没有任何问题；$n = 2$ 时，上面的重叠部分不存在，剩下的结构正好是 $1 + \df 1 2 - (\df 1 {n + 1} + \df 1 {n + 2} )$，所以也没问题．但 $n$ 更小的情况呢？

来看 $n = 1$ 的结果：

$$
\begin{aligned}
2S_1 & =  1 - \df 1 3 \\
& = 1 + \df 1 2 - (\df 1 2 + \df 1 3 )
\end{aligned}
$$

很明显第二个等号不能从相消得到，相反，$n$ 很小的时候这里是在补项．这就是相消法的逻辑疏漏所在了．

当然，「前缀和 $T_n + T_k - T_{n + k}$ 中 $n$，$k$ 可以互换」这个逻辑可以没有纰漏地解释这个等式．

:::

上面我们初步感受到了裂项求和的操作流程．对于 $a_n = \df{c_n}{p_nq_n}$，只要我们将 $a_n$ 成功进行了合适的裂项，后面的操作就相当固定了．

但需要注意的是，虽然任何分式都能裂项（分母不难写成两个不等项之积），然而 **能够求和的裂项** 却必须满足两个条件：

- $\df{c_n}{q_n - p_n}$（$\df{分子}{分母差}$）是一个 **与 $n$ 无关的常数**（设为 $C$）．这个条件是为了每一项裂项后产生的系数 $C$ 可以 **在求和时作为一个公因式提出**．
- $p_n$ 与 $q_n$ 可以刻画为 **同一个数列** $\{b_n\}$ 的第 $n$ 项与第 $n + k$ 项，$k$ 是一个常数．这个条件是为了 **最后裂成的分式可以统一为某个数列的一个连续段减去另一个连续段的形式**．

由于 **只有满足上面两个条件的裂项可以求和**，我们简单粗暴地认为：只有满足上面两个条件的裂项才称作裂项，不满足上面两个条件的不再称作裂项．

这样以来，对分式进行裂项也是一门学问，我们来看下面的例子：

:::info 例题 2.2

已知 $\{a_n\}$ 的通项公式为 $a_n = 3 \cdot 4 ^{n - 1}$，$\{a_n\}$ 的前缀和为 $S_n$，$b_n = \df{a_{n + 1}}{(a_{n + 1} - 3)S_{n + 1}}$，求 $\{b_n\}$ 的前缀和 $T_n$．

:::

:::tip 例题 2.2 解答

$\{a_n\}$ 是首项 $a_1 = 3$，公比 $q = 4$ 的等比数列，因此

$$
S_n = a_1 \cdot \df{q^n - 1}{q - 1} = 4^n - 1
$$

因此

$$
b_n = \df{3 \cdot 4^n}{(3 \cdot 4^n - 3)(4^{n + 1} - 1)}
$$

但这个形式可以裂项吗？答案是 **不可以**：

- $\df{分子}{分母差}$ 不是与 $n$ 无关的常数．
- 两个分母也不能统一为同一个数列的第 $n$ 项和第 $n + k$ 项．

但是，只要我们对分子分母同时约去 $3$：

$$
b_n = \df{4^n}{(4^n - 1)(4^{n + 1} - 1)}
$$

- $\df{分子}{分母差}$ 是与 $n$ 无关的常数 $\df 1 3$．
- 两个分母明显能统一为同一个数列的第 $n$ 项和第 $n + k$ 项：$4^n - 1$ 的第 $n$ 项和第 $n + 1$ 项，$k = 1$．

因此这个形式 **可以裂项**．

$$
\df{4^n}{(4^{n + 1} - 1) - (4^n - 1)} = \df{4^n}{4^{n + 1} - 4^n} = \df{1}{4 - 3} = \df 1 3
$$

因此 $b_n$ 裂项的结果是：

$$
b_n = \df 1 3 (\df 1 {4^n - 1} - \df 1 {4^{n + 1} - 1})
$$

也可以写成

$$
3b_n = \df 1 {4^n - 1} - \df 1 {4^{n + 1} - 1}
$$

现在可以开始求 $T_n$ 了，这里求和就按照正负分类来写：

$$
3T_n = (\df 1 {4 - 1} + \df 1 {4^2 - 1} + \cdots + \df 1 {4^n - 1}) - (\df 1 {4^2 - 1} + \df 1 {4^3 - 1} + \cdots + \df 1 {4^{n + 1} - 1})
$$

$n$，$k$ 互换原则（或者理解为相消）：

$$
3T_n = \df 1 3 - \df 1 {4^{n + 1} - 1}
$$

即

$$
T_n = \df 1 9 - \df 1 {3 \cdot 4^{n + 1} - 3}
$$

化简到这里就可以了，不用再通分了．

:::

可以看到，一个分式的某个形式可能无法进行裂项，但换个形式就可以了，下面给一些例子：

:::info 例题 2.3.1

$$
\df{3}{36n^2 - 24n - 5}
$$

:::

:::tip 例题 2.3.1 解答

分母 $36n^2 - 24n - 5$ 可以因式分解为 $(6n - 5)(6n + 1)$，因此目标分式即

$$
\df{3}{(6n - 5)(6n + 1)}
$$

- $\df{分子}{分母差}$ 为常数 $\df 1 2$．
- 两个分母可以写成数列 $\{6n - 5\}$ 的第 $n$ 项和第 $n + 1$ 项，$k = 1$．

因此可以裂项为

$$
\df 1 2 (\df 1 {6n - 5} - \df 1 {6n + 1})
$$

:::

:::info 例题 2.3.2

$$
\df{2}{3n(n + 1)}
$$

:::

:::tip 例题 2.3.2 解答

这个式子无法裂项（$3n$ 与 $n + 1$ 无法统一为同一个数列的两项）．应该上下同时除以 $3$：

$$
\df{\df 2 3}{n(n + 1)}
$$

再裂项为 $\df 2 3(\df 1 n - \df 1 {n + 1})$．

当然，也可以理解为将 $\df 2 3$ 提出，变为 $\df 2 3 \cdot \df 1 {n(n + 1)}$，再对后者裂项．

:::

:::info 例题 2.3.3

$$
\df{2n + 1}{n^2(2n + 2)^2}
$$

:::

:::tip 例题 2.3.3 解答

提出一个 $\df 1 4$：

$$
\df 1 4 \cdot \df{2n + 1}{n^2(n + 1)^2}
$$

后面的分式满足：

- $\df{分子}{分母差}$ 为常数 $\df{2n + 1}{2n + 1} = 1$．
- 分母可以写为 $\{(n + 1)^2\}$ 的第 $n$ 项和第 $n + 1$ 项．

因此可裂项为 $\df{1}{n^2} - \df 1 {(n + 1)^2}$．

最终的裂项结果为 $\df 1 4 (\df{1}{n^2} - \df 1 {(n + 1)^2})$．

:::

:::info 例题 2.3.4

$$
\df{4^n}{(4^n + 3)(4^{n + 1} + 3)}
$$

:::

:::tip 例题 2.3.4 解答

- $\df{分子}{分母差}$ 为常数 $\df{4^n}{3 \cdot 4^n} = \df 1 3$．
- 分母可以写为 $\{4^n + 3\}$ 的第 $n$ 项和第 $n + 1$ 项．

因此可以裂项为

$$
\df 1 3 (\df 1 {4^{n} + 3} - \df 1 {4^{n + 1} + 3})
$$

其实是一个很普通的裂项，但 **指数形式的裂项在高中阶段比较常考**，因此这里放一道例题起强调作用．

:::

:::info 例题 2.3.5

已知 $b_n = n \cdot 2^{n - 1}$，$a_n = \df{b_{n + 2}}{b_nb_{n + 1}}$，求 $\{a_n\}$ 的裂项．

:::

:::tip 例题 2.3.5 解答

$\{a_n\}$ 的通项分母已经自动表示成一个数列的第 $n$ 项和第 $n + 1$ 项了，此时第一反应一定是算一下 $\df{分子}{分母差}$：

$$
\df{b_{n + 2}}{b_{n + 1} - b_n} = \df{(n + 2)2^{n + 1}}{(n+1)2^n - n2^{n - 1}} = \df{(n + 2)2^{n + 1}}{2^{n - 1}[2(n + 1) - n]} = \df{4(n + 2)}{n + 2} = 4
$$

因此可以裂项为 $a_n = 4(\df 1 {n2^{n - 1}} - \df 1 {(n + 1)2^n})$．

这个题提示我们：**如果分母自动写成了一个数列的两项相乘，优先计算 $\df{分子}{分母差}$ 判断是否可以裂项**．如果我们展开再约分，变成

$$
a_n = \df{n + 2}{n(n + 1)2^{n - 2}}
$$

这个形态反而没那么容易看出裂项了．

:::

根据例题 2.3.5 的启发，可以再积累一个裂项：

:::info 例题 2.3.6（积累）

$$
\df{n + 2}{n(n + 1)2^n}
$$

:::

:::tip 例题 2.3.6 解答思路一（先变形，再证明 $\df{分子}{分母差}$ 为常数）

$$
\df{n + 2}{n(n + 1)2^n} = \df{(n + 2)2^{n - 1}}{n2^{n - 1}(n + 1)2^n}
$$

观察到

$$
(n + 2)2^{n - 1} = (2n + 2 - n)2^{n - 1} = (2n + 2)2^{n - 1} - n2^{n - 1} = (n + 1)2^n - n2^{n - 1}
$$

即分子等于分母差，因此我们有

$$
\df{n + 2}{n(n + 1)2^n} = \df 1 {n2^{n - 1}} - \df 1{(n + 1)2^n}
$$

:::

:::tip 例题 2.3.6 解答思路二（直接变形裂项）

$$
\df{n + 2}{n(n + 1)2^n} = \df{2(n + 1)}{n(n + 1)2^n} - \df n {n(n + 1)2^n} = \df 1 {n 2^{n - 1}} - \df 1{(n + 1)2^n}
$$

:::

例题 2.3.5 的 $a_n = \df{n + 2}{n(n + 1)2^{n - 2}}$ 也就是上面这个数列的 $4$ 倍，提出一个 $4$ 再裂项是同理的．

裂项的内容还不止于此，更多拓展会在[下一页](./extra.md#不常规裂项)介绍．

## 绝对值求和

:::info 例题 3

已知递增等差数列 $\{a_n\}$ 前三项和为 $-9$，前三项积为 $-15$，求 $\{\lv a_n \rv\}$ 的前缀和 $S_n$．

:::

:::tip 例题 3 解答

$$
a_1 + a_2 + a_3 = 9 \iff 3a_2 = 9 \iff a_2 = 3
$$

$$
a_1a_2a_3 = -15 \iff (a_2 - d)a_2(a_2 + d) = -15 \iff d^2 = 4 \iff d = \pm 2
$$

$\{a_n\}$ 递增，$d > 0$，有 $d = 2$．

因此 $a_n = a_2 + (n-2)d = 2n - 7$．

当 $n \le 3$ 时，$a_n < 0$，当 $n \ge 4$ 时，$a_n > 0$．

当 $n \le 3$ 时，$S_n = -(a_1 + a_2 + \cdots + a_n) = -[na_1 + \df{n(n - 1)}2d] = -n^2 + 6n$．

当 $n \ge 4$ 时，

$$
\bal
S_n &= -(a_1 + a_2 + a_3) + (a_4 + a_5 + \cdots + a_n) \\
& = (a_1 + a_2 + \cdots + a_n) - 2(a_1 + a_2 + a_3)\\
& = n^2 - 6n - 2 \times (-9)\\
& = n^2 - 6n + 18
\eal
$$

因此

$$
S_n = \bcs
-n^2 + 6n, & n \le 3 \\
n^2 - 6n + 18, & n \ge 4
\ecs
$$

:::

这里 $S_n$ 写过程必须要用 $na_1 + \df{n(n - 1)}2 d$，但结果可以直接用 $\df d 2 \cdot n^2 + (a_1 - \df d 2) n$ 速算，这些在等差数列页面提过的小细节不要忘记．

## 分组求和

内容很简单：如果 $\{a_n\}$ 的前缀和为 $\{S_n\}$，$\{b_n\}$ 的前缀和为 $\{T_n\}$，则 $\{a_n + b_n\}$ 的前缀和为 $\{S_n + T_n\}$．

这样以来，等差加等比，等差加（等差乘等比），等比加裂项，裂项加等差等数列都可以很方便地求和．如

$$
a_n = 2n + 3^{n - 1}
$$

$2n$ 求和为 $n^2 + n$，$3^{n - 1}$ 求和为 $\df{3^n - 1}2$，因此 $a_n$ 的前缀和就是 $n^2 + n + \df{3^n - 1} 2$．

小细节：常数 $\{c_n\}$ 构成的常数列求和是 $nc$，这个 $n$ 比较容易遗漏．如 $3^{n - 1} + 1$ 求和的结果应为 $\df{3^n - 1} 2 + \* n$．

:::info 例题 4

求 $a_n = \lv 3^{n - 1} - n - 2 \rv$ 的前缀和 $S_n$．

:::

:::tip 例题 4 解答

$a_1 = -2$，$a_2 = -1$，$a_3 = 4$．

由于 $a_{n + 1} - a_n = 2 \times 3^{n - 1} - 1 > 0$，因此 $\{a_n\}$ 递增，当 $n \ge 3$ 时，$a_n \ge a_3 > 0$．

因此当 $n \le 2$ 时，$a_n < 0$，当 $n \ge 3$ 时，$a_n > 0$．

由于 $n \le 2$ 的情况太少，直接暴力计算 $S_1 = 2$，$S_2 = 3$．

$n \ge 3$ 时，设 $b_n = 3^{n - 1} - n - 2$，前缀和为 $T_n$，有

$$
S_n = -(b_1 + b_2) + b_3 + b_4 + \cdots + b_n = (b_1 + b_2 + \cdots + b_n) - 2(b_1 + b_2) = T_n - 6
$$

$T_n$ 可分为三个部分：$3^{n - 1}$，$-n$，$-2$．

求和后分别为 $\df{3^n - 1}2$，$-\df{n(n + 1)}2$，$-2n$，因此

$$
T_n = \df{3^n - 1}2  -\df{n(n + 1)}2 - 2n = \df{3^n - n^2 - 5n - 1} 2
$$

$$
S_n = T_n + 6 = \df{3^n - n^2 - 5n + 11} 2
$$

检验一下 $S_1$，$S_2$ 是否可以合并．$S_1$ 不可，$S_2$ 可，因此答案为

$$
S_n = \bcs
2, & n = 1 \\[1em]
\df{3^n - n^2 - 5n + 11} 2, & n \ge 2
\ecs
$$

:::

## 奇偶项求和

奇偶项数列的定义是：通项公式表示为 **奇项** 与 **偶项** 分段的数列．

特别地，对于 $b_n = (-1)^n a_n$，一般处理为 $b_n = \bcs -a_n, & n 为奇数 \\ a_n, & n 为偶数\ecs$ 后再做，这类数列也称作 **奇偶项数列**．

本节的学习目标是：对于 **通项已知** 的 **奇偶项数列**，如何求它的 **前缀和**．至于 **已知递推式求奇偶项数列的通项** 的问题，会在[已知隔项递推求奇偶项数列通项](../general-formula/common.md#已知隔项递推求奇偶项数列通项)一节讲述，这里不做讨论．

> 给定一个数列 $\{a_n\}$ 和一个数列 $\{b_n\}$，设 $c_n = \bcs a_n, & n 为奇数 \\ b_n, & n 为偶数 \ecs$ 的前缀和为 $\{S_n\}$，求 $S_n$，$S_{2n}$，$S_{2n - 1}$．

$$
S_n = \bcs

a_1 + b_2 + a_3 + b_4 + \cdots + a_n, & n 为奇数 \\
a_1 + b_2 + a_3 + b_4 + \cdots + b_n, & n 为偶数

\ecs
$$

$$
S_{2n} = a_1 + b_2 + a_3 + b_4 + \cdots + b_{2n}
$$

$$
S_{2n - 1} = a_1 + b_2 + a_3 + b_4 + \cdots + a_{2n - 1}
$$

这类题目的 $S_n$ 通项通常是分段的，而 $S_{2n}$，$S_{2n - 1}$ 则不分段．

如果题目问 $S_n$，需要讨论 $n$ 的奇偶性，列出不同的式子，分开作答．

### 奇偶项求和 - 分开求

先求

$$
a_1 + a_3 + a_5 + \cdots
$$

再求

$$
b_2 + b_4 + b_6 + \cdots
$$

最后将两部分合并．

需要注意：第一部分并不是 $\{a_n\}$ 的前缀和，求和形态也与 $\{a_n\}$ 数列有差异．如 $\{a_n\}$ 若是一个公差为 $2$ 的等差数列，则第一部分中的求和中公差为 $4$．

:::info 例题 5.1

已知 $c_n = \bcs 2n - 1, & n 为奇数 \\ 3^{n - 1}, & n 为偶数 \ecs$ 的前缀和 $\{S_n\}$，求 $S_{2n}$．

:::

:::tip 例题 5.1 解答

令 $a_n = 2n - 1$，$b_n = 3^{n - 1}$．

$$
\bal
S_{2n} &= (a_1 + a_3 + \cdots + a_{2n - 1}) + (b_2 + b_4 + \cdots + b_{2n}) \\[1em]
&= (na_1 + \df{n(n - 1)}2 \cdot \red{2d}) + \df{\red{b_2} \cdot [1 - (\red{q^2})^n]}{1 - \red{q^2}} \\[1em]
&= 2n^2 - n + \df{3(1 - 9^n)}{1 - 9}\\[1em]
&= 2n^2 - n + \df 3 8 \cdot 9^n - \df 3 8
\eal
$$

:::

### 奇偶项求和 - 并项

即求 $(a_1 + b_2) + (a_3 + b_4) + \cdots$，两项两项地求和．

此时可以辅助地建立数列 $\{p_n\}$，令 $p_n = a_{2n - 1} + b_{2n}$，$\{p_n\}$ 前缀和为 $\{T_n\}$，则：

- $S_{2n} = T_n$．
- $S_{2n - 1} = T_n - b_{2n}$．
- $S_n$ 可以由上两者经过 **奇偶项变换**（下一节介绍）得到．

:::info 例题 5.2

已知数列 $\{a_n\}$ 满足 $a_{2n - 1} = 2 \cdot 6^{n - 1} - 1$，$a_{2n} = 4 \cdot 6^{n - 1} - 1$，求 $S_{2n}$．

:::

:::tip 例题 5.2 解答

令 $c_n = a_{2n - 1} + a_{2n} = 6^n - 2$，则

$$
S_{2n} = c_1 + c_2 + \cdots + c_n = \df{6(6^n - 1)}{6 - 1} - 2n = \df{6^{n + 1} - 6} 5 - 2n
$$

:::

### 奇偶项变换

对于一个奇偶项数列 $\{a_n\}$，两个概念较为重要：

- 摘出 **下标为奇数的项**，按顺序列出的数列称作 **奇项数列**．
- 摘出 **下标为偶数的项**，按顺序列出的数列称作 **偶项数列**．

不难看出，

- **奇项数列** 的第 $n$ 项应为 **原数列** 的第 $2n - 1$ 项，奇项数列可以表示为 $\{a_{2n - 1}\}$．
- **偶项数列** 的第 $n$ 项应为 **原数列** 的第 $2n$ 项，偶项数列可以表示为 $\{a_{2n}\}$．

要求解一个数列的 **奇项数列** 和 **偶项数列**，直接将 $2n - 1$ 与 $2n$ 分别代入通项中的 $n$ 即可．

:::info 例题 5.3.1

写出 $a_n = \bcs 2n - 1, & n 为奇数 \\ 3^{n - 1}, & n 为偶数 \ecs$ 的 **奇项数列通项** $a_{2n - 1}$ 与 **偶项数列通项** $a_{2n}$．

:::

:::tip 例题 5.3.1 解答

$a_{2n - 1} = 2(2n - 1) - 1 = 4n - 3$，$a_{2n} = 3^{2n - 1} = \df{9^n} 3$．

:::

反过来，

- **原数列** $\{a_n\}$ 的第 $n$ 项（$n$ 为偶数）对应 **偶项数列** $\{a_{2n}\}$ 的第 $\df n 2$ 项．
- **原数列** $\{a_n\}$ 的第 $n$ 项（$n$ 为奇数）对应 **奇项数列** $\{a_{2n - 1}\}$ 的第 $\df{n \red{+} 1} 2$ 项．

因此，知道一个数列的 **奇项数列** $a_{2n - 1} = f(n)$ 和 **偶项数列** $a_{2n} = g(n)$，可以拼凑出 **原数列**

$$
a_n = \bcs f(\df{n + 1} 2), & n 为奇数 \\[1em] g(\df n 2), & n 为偶数 \ecs
$$

该结论可以直接在大题中使用．

:::info 例题 5.3.2

已知数列 $\{a_n\}$ 满足 $a_{2n - 1} = 2 \cdot 6^{n - 1} - 1$，$a_{2n} = 4 \cdot 6^{n - 1} - 1$，求 $a_n$．

:::

:::tip 例题 5.3.2 解答

$n$ 为奇数时，$a_n = 2 \cdot 6^{\fr{n + 1} 2 - 1} - 1 = 2 \cdot 6^{\fr{n - 1} 2} - 1$．

$n$ 为偶数时，$a_n = 4 \cdot 6^{\fr n 2 - 1} - 1$．

因此

$$
a_n = \bcs
2 \cdot 6^{\fr{n - 1} 2} - 1, & n 为奇数 \\
4 \cdot 6^{\fr n 2 - 1} - 1, & n 为偶数
\ecs
$$

:::

## 求和常见结论

$$
1 + 3 + 5 + \cdots + (2n - 1) = n^2
$$

$$
\red{2^0} + 2^1 + 2^2 + \cdots + 2^{n - 1} = 2^n - 1
$$

$$
2^1 + 2^2 + 2^3 + \cdots + 2^{n - 1} = 2^n - 2
$$

$1 + 2 + 3 + \cdots$ 的前 $1 \sim 10$ 项和分别为：

$$
\* 1, 3, 6, 10, 15, 21, 28, 36, 45, 55
$$

上面这些求和使用等差、等比求和都十分容易，为什么要专门拉出来作为结论呢？因为 **出现频率实在太高了**，遇到这些求和的时候直接用结论写答案可以提升解题效率．

$$
1^2 + 2^2 + 3^2 + \cdots + n^2 = \df {n(n + 1)(2n + 1)}6
$$

这个公式称作 **自然数平方和** 公式，一个最容易想到的证明就是：令 $S_n = \df {n(n + 1)(2n + 1)}6$，证明 $n^2 = S_n - S_{n - 1}$．

如果想要正向推导，这里也给出一个证明：

$$
\bal
S_n &= 1 \times 1 + 2 \times 2 + 3 \times 3 + \cdots + n \times n \\
&= 1 \times (2 - 1) + 2 \times (3 - 1) + 3 \times (4 - 1) + \cdots + n \times (n + 1 - 1) \\
&= 1 \times 2 + 2 \times 3 + \cdots + n \times (n + 1) - \df {n(n + 1)}2 \\
\eal
$$

而 $n(n + 1)$ 可以裂项为 $\df 1 3 [n(n + 1)(n + 2) - (n - 1)n(n + 1)]$，因此

$$
S_n = \df 1 3[n(n + 1)(n + 2) - 0] - \df {n(n + 1)}2 = \df {n(n + 1)(2n + 1)}6
$$

这个公式常用来求 **等差数列的前缀和的前缀和**，因为等差数列的前缀和是一个二次函数 $An^2 + Bn$ 的形式，其前缀和可以分组计算 $An^2$ 和 $Bn$，前者使用自然数平方和公式计算．