#project
*问题出发点*
做改性提高极化子活性->极化子活性-? 有关
*Idea*
极化子的运动的本质是透热态转变
可以理解为e-p coupling下,“回转半径”变化的过程,最后会回到本征回转半径,“本征回转半径“决定了本征的极化子寿命 [[radius of gyration#^7c4309]]
*Research Target*
1. 计算极化子趋势的方式
2. 什么宏观量和活性有关
*To Do*
* 加入一个charge,局域各种极化子构型 by cDFT
* 按照电子耦合$H_{ab}$ 大小排序

- [ ] 在具有不同”回转半径“的不同透热态之间,计算Hab  
  id:: 642ecb00-4136-4836-ad44-395a50881838
  * 计算1st-excited state和不同“回转半径”的透热态之间的Hab
  
  *Idea思想来源*
  cite Giustino,极化子概括为振动模式的组合和匹配,从计算Hab的方向提取振动模式,确定振动模式的组分,判断极化子贡献的组分
  ![[Pasted image 20230323222732.png]]
  ![[Pasted image 20230323223642.png]]
  ![[Pasted image 20230323223019.png]]
  | Polaron Transfer group | $\Delta E$ (eV) | $\Lambda_0$ (eV) | relative radius of gyration |
  |:----------------------:|:---------------:|:-------------:|:------------------:|
  |         1-> 2          |      0.22       |     0.34      |        1.9        |
  |         1-> 6          |      0.01       |     2.31      |        6.5        |
  |         1-> 10         |      3.24       |     3.94      |        8.8        |
  note:
  $RRG=RG/RG_0$ 
  各种各样的极化子构型是各种各样的透热态
  *初步的关键结论*
  1. RRG max可以用来描述极化子,maxRRG越大,polaron可以弛豫的时间越长,活性越高
  2. 思考引入破坏对称性程度最大的(片段RG小)的成分或缺陷,可以增强极化子活性
  3. RRG有物理意义! 相对振动模的频率
  
  
  *Further Topic*
  1. 变U polaron-transfer问题 [[Marcus理论 in cp2k#^088395]]
  2. 振动选择分析结合cp2k
  3. 极化子构型->结构(cDFT very easy),结构->极化子构型(all phonon basis tb model)
  4. 计算polaron下的columb screening potential(U和quasiparticle coupling)