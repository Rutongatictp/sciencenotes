#计算原理
# 概述
|  常规DFT | CDFT |
| :---: | :----: |
| 能量泛函对应的能量最小化| 人为约束寻找能量最低|

约束对象:原子或片段的population;spin-population;population difference
应用:电荷转移作用能;离域化能;电荷转移激发能
# 算法
拉格朗日乘子法要求KS-DFT求解中满足约束条件
$$
E_{\text {CDFT }}[\{\varphi\}, \lambda]=E_{\mathrm{kS}}[\{\varphi\}]+\sum_c \lambda_c\left[\sum_{\sigma=\alpha, \beta} \int_c^\sigma(\mathbf{r}) \rho^\sigma(\mathbf{r}) \mathrm{d} \mathbf{r}-N_c\right]
$$

其中,第$c$个约束条件需要满足$\sum_{\sigma=\alpha, \beta} \int w_c^\sigma(\mathbf{r}) \rho^\sigma(\mathbf{r}) \mathrm{d} \mathbf{r}=N_c$
第$c$个约束的$\sigma$ 自旋的权重函数为$w_c^\sigma(\mathbf{r})=\sum_{A \in c} d_A^\sigma w_A(\mathbf{r})$,$w_A$是$A$原子的权重函数,由Hirshfeld或者Becke方式定义
$\mathrm{CDFT}$ 要求 $E_{\mathrm{CDFT}}$ 相对于 $\{\varphi\}$ 和 $\lambda$ 的驻点
令 $E_{\mathrm{CDFF}}$ 相对于 $\{\varphi\}$ 㪚极小化并约束轨道的正 交归一条件, 可得形式上等同于加入了额外 外势的KS-DFT方程
$$
[-\frac{1}{2} \nabla^2+v_{\text {nuc }}(\mathbf{r})+\int \frac{\rho\left(\mathbf{r}^{\prime}\right)}{\left|\mathbf{r}-\mathbf{r}^{\prime}\right|} \mathrm{d} \mathbf{r}^{\prime}+v_{\mathrm{xc}}^\sigma(\mathbf{r})+\underbrace{\lambda_c w_c^\sigma(\mathbf{r})}_{c约束条件带来的外势}] \varphi_i^\sigma(\mathbf{r})=\varepsilon_i^\sigma \varphi_i^\sigma(\mathbf{r})
$$
按上式求解出 $\{\varphi\}$ 后, 可以证明 $E_{\mathrm{CDFT}}$ 是 $\lambda$ 的凹 函数 (有一个极大点) 。使用极大点处的 $\lambda$ 对 对上式做SCF解出来的 $\{\varphi\}$ 才能同时满足各个 约束条件。在一套特定 $\{\varphi\}$ 下, 可以通过 (准 牛顿法搜素令 $E_{\mathrm{CDFT}}$ 取大化的 $\lambda$.

CDFT与加约束计算的电子结构状态偏离无约束时越显著, 收敛后的$\lambda$ 越大.

每个CDFT约束条件都对原子受力引入额外的项$\mathbf{F}_{c, A}=-\lambda_c \int \frac{\partial w_c(\mathbf{r})}{\partial \mathbf{R}_A} \rho(\mathbf{r}) \mathrm{d} \mathbf{r}$,使得原子的实际受力为$\mathbf{F}_{\mathrm{tot}, A}=\mathbf{F}_A+\sum_c \mathbf{F}_{c, A}$

1.Ahart, C. S., Rosso, K. M., & Blumberger, J. (2022). Implementation and Validation of Constrained Density Functional Theory Forces in the CP2K Package. _Journal of Chemical Theory and Computation_, _18_(7), 4438–4446. [https://doi.org/10.1021/acs.jctc.2c00284](https://doi.org/10.1021/acs.jctc.2c00284)
2.Holmberg, N., & Laasonen, K. (2017). Efficient Constrained Density Functional Theory Implementation for Simulation of Condensed Phase Electron Transfer Reactions. _Journal of Chemical Theory and Computation_, _13_(2), 587–601. [https://doi.org/10.1021/acs.jctc.6b01085](https://doi.org/10.1021/acs.jctc.6b01085)
3.Kaduk, B., Kowalczyk, T., & Van Voorhis, T. (2012). Constrained Density Functional Theory. _Chemical Reviews_, _112_(1), 321–370. [https://doi.org/10.1021/cr200148b](https://doi.org/10.1021/cr200148b)
4.Wu, Q., & Van Voorhis, T. (2005). Direct optimization method to study constrained systems within density-functional theory. _Physical Review A_, _72_(2), 024502. [https://doi.org/10.1103/PhysRevA.72.024502](https://doi.org/10.1103/PhysRevA.72.024502)