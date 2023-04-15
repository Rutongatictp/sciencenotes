#计算原理 
传统定义:物体绕旋转轴的回转半径或回转半径定义为到某个点的径向距离，如果物体的总质量集中在那里，该点的 惯性矩与物体的实际质量分布相同。推广到电子束缚在受限环境中的描述符或者展现方式 
## 定义

^7c4309

$$
\mathbf{r}_{\mathrm{c}}=\frac{\int \mathbf{r} \times f(\mathbf{r}) \mathrm{d} \mathbf{r}}{\int f(\mathbf{r}) \mathrm{d} \mathbf{r}}
$$
$$
\boldsymbol{\Theta}=\left[\begin{array}{lll}
\Theta_{x x} & \Theta_{x y} & \Theta_{x z} \\
\Theta_{y x} & \Theta_{y y} & \Theta_{y z} \\
\Theta_{z x} & \Theta_{z y} & \Theta_{z z}
\end{array}\right]=\int\left[\begin{array}{lll}
x^2 & x y & x z \\
y x & y^2 & y z \\
z x & z y & z^2
\end{array}\right] f(\mathbf{r}) \mathrm{d} \mathbf{r}
$$
$$
\sqrt{\frac{\varepsilon_1+\varepsilon_2+\varepsilon_3}{\int f(\mathbf{r}) \mathrm{d} \mathbf{r}}}
$$

Multiwfn的主功能200的子功能11就能算任意函数的回转半径。详见手册3.200.11节  
如果你有Multiwfn可以认的波函数文件，诸如wfn、molden、fch等，建议以此作为输入文件让Multiwfn直接计算自旋密度，这样精度最好  
如果只有cube文件，把Multiwfn的settings.ini设为-1（让用户自定义函数对应于cube文件插值得到的函数），然后用Multiwfn载入cube文件，进入上述功能，选择"3 Select the function to be studied"并选择100 User-defined function作为被计算的函数。然后选1开始计算。

启动Multiwfn，然后输入  
file\H8O4-.fchk  
200  //主功能200  
11   //计算函数中心、一阶、二阶矩和回转半径。此功能使用的是Becke多中心格点积分方法，默认设置下精度就已经很高了  
3   //选择被考察的函数  
5   //自旋密度  
2   //计算函数中心  
从屏幕上可看到函数的积分值和中心位置。  
Integral of the function:  9.99842011E-01 a.u.

Center of the function:  
X=     -0.09360685 Y=      0.03381961 Z=     -0.47523227 Angstrom

然后输入y，将这个中心当做之后算各种量所用的参考中心位置。之后选1计算各种量，从屏幕上可见回转半径的数值：  
Radius of gyration:  4.29967591E+00 Bohr   2.27529051E+00 Angstrom