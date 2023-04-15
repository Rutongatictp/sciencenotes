#cp2k #excited-state/原理

## Marcus theory

$$
\begin{equation}k=\frac{\left(\left|H_{a b}\right|^2\right\rangle_T}{\hbar} \sqrt{\frac{\pi}{\lambda R T}} \exp \left[\frac{-\left(\Delta G^0+\lambda\right)^2}{4 \lambda R T}\right]\end{equation}
$$
## 电荷转移积分

$$
\begin{equation}\left|H_{a b}\right|=\left|\left\langle\Psi_a|\hat{H}| \Psi_b\right\rangle\right|\end{equation}
$$

$\lambda$:重组自由能

$\Delta G^{\circ}$:电荷转移吉布斯自由能变 

${<>}_{\tau}$:几何结构动态heat平均
## 电子转移自由能垒

$$
\begin{equation}\Delta G^*=\frac{\left(\Delta G^0+\lambda\right)^2}{4 \lambda}\end{equation}
$$
### cDFT法原理:

$\begin{aligned}& H_{a b} \approx\left\langle\Phi_a\left|\bar{h}^{\mathrm{KS}}\right| \Phi_b\right\rangle=E_b S_{a b}-\sum_c \lambda_c^b W_c^{a b} \\& H_{b_a} \approx\left\langle\Phi_b\left|\bar{h}^{\mathrm{KS}}\right| \Phi_a\right\rangle=E_a S_{b a}-\sum_c \lambda_c^a W_c^{b a}\end{aligned}$

$S_{\mathrm{ab}}=\left\langle\Phi_a \mid \Phi_b\right\rangle \quad W_c^{a b}=\left\langle\Phi_a\left|w_c^b(\mathbf{r})\right| \Phi_b\right\rangle$
对$\bar{h}^{\mathrm{KS}}$ 的非对角元取平均,直接做Lowdin正交化,或者直接tensorial
- ### POD法原理:
  
  ^088395
  
  1. Lowdin orthogonalizaiton
  2. calculate coupling matrix element
  ![[Pasted image 20230323222306.png]]
  * [[巨正则系综的POD]] H跑了polaron动,U有变化,polaron的势垒 #Translation
### cDFT法计算流程:

1. step1: constraint-DFT计算完成的 xxx1-RESTART.wfn 和 xxx2-RESTART.wfn 保留,输出文件读取各自的$\lambda$值.

2. step2:cp2k 计算电子耦合

```bash
&MULTIPLE_FORCE_EVALS
 FORCE_EVAL_ORDER 2 3
 MULTIPLE_SUBSYS F
&END MULTIPLE_FORCE_EVALS

&FORCE_EVAL
 METHOD MIXED
 &MIXED
 MIXING_TYPE MIXED_CDFT
 NGROUPS 1. #solve each FORCE_EVAL
 &MIXED_CDFT
   LAMBDA 1.0  ##F=\lambdaF_1+(1-\lambda)F_2
   COUPLING 1  ##calculate coupling at each step
   LOWDIN T
 &END MIXED_CDFT
 &END MIXED
 &SUBSYS
xxxxxxx
xxxxxxx
......
 &END SUBSYS
&END FORCE_EVAL

&FORCE_EVAL
 ## The same to diabatic state 1
 &DFT
WFN_RESTART_FILE_NAME xxx1-RESTART.wfn
 ...
 &CDFT
 STRENGTH \lambda_1
 ## all the same
&END FORCE_EVAL

&FORCE_EVAL
 ## The same to diabatic state 2
 &DFT
WFN_RESTART_FILE_NAME xxx2-RESTART.wfn
 ...
 &CDFT
 STRENGTH \lambda_2
 ## all the same
&END FORCE_EVAL

```
### POD法计算流程:基于lowdin正交化的片段化方法

例如表面吸附物和体相之间的电荷转移:

cp2k输入文件中在&FORCE_EVAL 内加入如下内容

```bash
&PROPERTIES
 &ET_COUPLING
&PROJECTION
  &BLOCK
   ATOM 1 2 3 4 5 ... #donor part of atoms
   NELECTRON 50  #number of electrons at neutral
  &END BLOCK
  &BLOCK
   ATOM 10 11 12 13 14 ... #acceptor part of atoms
   NELECTRON 50  #number of electrons at neutral
  &END BLOCK
&END PROJECTION
 &END ET_COUPLING
&END PROPERTIES
```

> J. Phys. Chem. C, 121, 19677 (2017)