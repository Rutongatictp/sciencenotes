- #基础知识 
  
  * >http://sobereva.com/543
  
  | name            | defination                     | extended defination                  |
  | --------------- | ------------------------------ | :------------------------------------: |
  | HOMO-LUMO gap   | $E(LUMO)-E(HOMO)$              | ------                                  |
  | Optical gap     | $E_{vert}(S_0\rightarrow S_1)$ | ------      |
  | Fundamental gap | $VIP-VEA$                      | $VIP=E(N-1)-E(N)$, $VEA=E(N)-E(N+1)$ |
  
  Koopmans定理下,$VIP\approx-E(HOMO)$,$VEA\approx-E(LUMO)$, 因此$fundamental gap\approx E(LUMO)-E(HOMO)$,但是在DFT里面描述极差
  * 一个电子态到一个电子态的跃迁不等于一个轨道到一个轨道的跃迁
  $$
  E_i^a-E=\underbrace{\varepsilon_a-\varepsilon_i}_{\text {gap }}-\underbrace{[(i i \mid a a)-(i a \mid a i)}_{\text {激子结合能(exciton binding energy) }}]
  $$
  [softness](http://bbs.keinsci.com/thread-384-1-1.html) 与化学硬度的关系 #Translation 
  * 实验测到的不是分子轨道,而是Dyson轨道$\varphi^{\text {Dyson }}\left(\mathbf{x}_N\right)=\sqrt{N} \int \Psi_N\left(\mathbf{x}_1 \ldots \mathbf{x}_N\right) \Psi_{N-1}\left(\mathbf{x}_1 \ldots \mathbf{x}_{N-1}\right) \mathrm{d} \mathbf{x}_1 \ldots \mathrm{d} \mathbf{x}_{N-1}$ ,其模方反映的是电离过程的密度变化 
  原先的波函数 电离后的波函数