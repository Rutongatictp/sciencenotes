- #基础知识
- ## 开放系统的时间演化
  * 一个封闭量子系统随时间幺正演化(which means 概率和信息的守恒):$|\psi\rangle \rightarrow U|\psi\rangle$
  * 考虑包含环境的系统: A(关心的) B(环境),因为信息存在交换.所以一定不是幺正演化
  > 解决策略:AB考虑为复合系统,环境最初处于假设环境最初处于 $\left|e_0\right\rangle$ 态, 而我们关心的系统最初处于 $|\psi\rangle$ 态, 两者没有纠缠。由于 整个复合系统是封闭的, 所以复合系统将满足么正演化,
  $$
  \left|e_0\right\rangle|\psi\rangle \rightarrow U\left(\left|e_0\right\rangle|\psi\rangle\right) 
  $$
  > 下面我们取环境希尔伯特空间的一组正交归一矢量基 $\left\{\left|e_s\right\rangle\right\}$, 然后将复合系统的量子态 $U\left(\left|e_0\right\rangle|\psi\rangle\right)$ 按这组基展开成
  $$
  U\left(\left|e_0\right\rangle|\psi\rangle\right)=\sum_s\left|e_s\right\rangle\left|\psi_s\right\rangle
  $$
  注意, 我们并没有说 $\left|\psi_s\right\rangle$ 正交归一。下面我们引人一组作用在 $A$ 系统上的算符 $E_s$, 定义 为 $\left|\psi_s\right\rangle=E_s|\psi\rangle$, 则
  $$
  \left|e_0\right\rangle|\psi\rangle \rightarrow U\left(\left|e_0\right\rangle|\psi\rangle\right)=\sum_s\left|e_s\right\rangle E_s|\psi\rangle .
  $$
  利用 $U$ 的幺正性, 我们可以得到
  $$
  \sum_s E_s^{\dagger} E_s=1 .
  $$
  所以开放系统从初态到 $t$ 时刻态的映射完全由这组算符 $E_s$ 决定。 ^93c2d8
  
  上面的推导可以直接拿到到密度算符中.
  假设系统初始的密度算符为 $\rho$, following below,环境初始的密度算符为 $\left|e_0\right\rangle\left\langle e_0\right|$, 则整个复合系统初始的密度算符为这两者的乘积, 不过, 为了强调 $\rho$ 只作用在系统的希尔伯特空间, 而 $\left|e_0\right\rangle\left\langle e_0\right|$ 只作用在环境的希尔伯特空间, 我们常常将这个乘积 写成 $\left|e_0\right\rangle\left\langle e_0\right| \otimes \rho$, 并简记为 $\hat{\rho}$ 。则类似于上面的推导我们将有
  $$
  \widehat{\rho} \rightarrow \widehat{\rho}^{\prime}=U \widehat{\rho} U^{\dagger}=\sum_{s, s^{\prime}}\left|e_s\right\rangle\left\langle e_{s^{\prime}}\right| \otimes E_s \rho E_{s^{\prime}}^{\dagger}
  $$
  由于我们并不关心环境, 所以我们忽略它, 即对环境的希尔伯特空间求迹, 从而得到
  $$
  \rho \rightarrow \operatorname{Tr}_B\left(\hat{\rho}^{\prime}\right)=\sum_s E_s \rho E_s^{\dagger} \text {. }
  $$
  我们常常把这个方程写作
  $$
  \rho \rightarrow \mathscr{E}(\rho)=\sum_s E_s \rho E_s^{\dagger}, \quad \sum_s E_s^{\dagger} E_s=1 .
  $$
  这里的映射$\mathscr{E}$会让密度算符的trace保持,只需要满足一些条件,线性算符一定可以表示成上述形式(ref:kraus 算符)
  **新的问题出现了,如何表示任意t时刻的密度算符的演化** [[DMPT和关联系统#^93c2d8]] 因为最开始的假设是系统和环境没有关联,但是实际情况是在t时刻系统和环境一定有纠缠,所以需要
- ## 刘维尔方程和Lindblad方程
  前提:环境巨大,无限热源-> *可以微扰* 
  极小的时间尺度$\tau$ 下系统和环境丧失关联,我们关注远大于$\tau$ 的$\delta t$上密度算符的演化
  对任意时刻$t$观测$E_s$ 的演化:
  $$\rho(t+\delta t)=\sum_s E_s(t+\delta t, t) \rho(t) E_s^{\dagger}(t+\delta t, t)$$
  $$
  E_0(t+\delta t, t)=U(t+\delta t, t)=1-i H \delta t / \hbar+\ldots
  $$
  代人映射方程式, 即得到标准的刘维尔方程
  $$
  \hbar \frac{d \rho}{d t}=-i[H, \rho]
  $$
  对于与环境相互作用的开放系统, 这时候就可能有许多非零 Kraus 算符。但是可以 设想, 对于一个无穷小的 $\delta t, E_0(t+\delta t, t)$ 将依然是主要的, 按照 $\delta t$ 进行泰勒展开依然有 $E_0(t+\delta t, t)=1+O(\delta t)$, 不过当然, $E_0(t+\delta t, t)$ 不再幺正, 从而我们应该假设
  $$
  E_0(t+\delta t, t)=1-i\left(H-i \frac{\Gamma}{2}\right) \delta t / \hbar+\ldots
  $$
  式中 $\Gamma$ 也是一个厄密算符。
  我们假设
  $$
  E_m(t+\delta t, t)=L_m \sqrt{\delta t} / \sqrt{\hbar}+\ldots, m=1,2,3 \ldots
  $$
  由于 Kraus 算符要满足 $\sum_s E_s^{\dagger} E_s=1$, 从而我们有
  $$
  -\Gamma+\sum_{m=1} L_m^{\dagger} L_m=0 \Rightarrow \Gamma=\sum_{m=1} L_m^{\dagger} L_m
  $$
  将 Kraus 算符的这些展开形式代人时间演化方程就有
  $$
  \hbar \frac{d \rho}{d t}=-i[H, \rho]-\frac{1}{2}(\Gamma \rho(t)+\rho(t) \Gamma)+\sum_{m=1} L_m \rho(t) L_m^{\dagger} .
  $$
  这就是开放系统密度算符的时间演化方程, 称作 Lindblad 方程, 它可以看作是量子版本 的 Fokker-Planck 方程, 其中的算符 $L_m$ 称作 Lindblad 算符, 它描写系统与环境的相互作用。

