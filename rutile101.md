#project 
*RG 描述 polaron behavior的验证*
phonon assisted polaron hoping is divided into two parts:
1. self-trapping part (nearly-fixed mode)
2. polaron transfer after vibrational relaxation (phonon assisted mode)
> Further explanation, to classify polarons, Large Frohlich polaron, Small Holstein polaron Dopant/Defect polaron are included. We need an unified term to describe the e-p grouped effect.

Thus, we need the characteristical viberation mode to describe the behavior of polaron

Special: spin polaron need spin non-collinear description #Translation  

*Solution*
> non-adiabatic phonon-assisted jump rate is 
> $R_{g, g^{\prime}}=\left(\frac{t_{g, g^{\prime}}}{\hbar}\right)^2 e^{-\Delta_{g, g^{\prime}} / 2 \kappa T} e^{-2 S_{g, g^{\prime}}} \int_{-\infty}^{\infty} d \tau e^{F_{g, g^{\prime}}(\tau)} \cos \left(\Delta_{g, g^{\prime}} \tau / \hbar\right)$
> $2 S_{g, g^{\prime}} \equiv N^{-1} \sum_{\boldsymbol{q}} \Gamma_{g, g^{\prime}}(\boldsymbol{q}) \gamma(\boldsymbol{q}) \operatorname{coth}\left(\hbar \omega_{\boldsymbol{q}} / 2 \kappa T\right)$
> $F_{\boldsymbol{g}, g^{\prime}}(\tau) \equiv N^{-1} \sum_{\boldsymbol{q}} \Gamma_{g, g^{\prime}}(\boldsymbol{q}) \gamma(\boldsymbol{q}) \operatorname{csch}\left(\hbar \omega_{\boldsymbol{q}} / 2 \kappa T\right) \cos \left(\omega_{\boldsymbol{q}} \tau\right)$
> Where atoms are presumed to vibrate harmonically among N modes of frequency ωq and wavevector q. The spatial correlation factor
> $\Gamma_{g, g^{\prime}}(\boldsymbol{q}) \equiv f_{\boldsymbol{g}}^2+f_{g^{\prime}}^2-2 f_g f_{g^{\prime}} \cos \left[\boldsymbol{q} \cdot\left(\boldsymbol{g}-\boldsymbol{g}^{\prime}\right)\right]$
> indicates that vibrations whose wavelengths exceed the inter-site separation tend to be ineffective in producing a hop since they do not alter the energy difference between the two sites. Moreover, the form factor
> $f_{\boldsymbol{g}}(\boldsymbol{q}) \equiv\left\langle\phi_{\boldsymbol{g}}\left|e^{i \boldsymbol{q} \cdot(\boldsymbol{r}-\boldsymbol{g})}\right| \phi_{\boldsymbol{g}}\right\rangle$

**Thus, above indicates that a localized electronic state interacts most effectively with phonons whose wavelengths exceed its spatial extent.**

Let's make it simple,
$\Gamma_g (\boldsymbol{q}) \equiv (f_{\boldsymbol{g}}-f_{\boldsymbol{g^{\prime}}})^2$
Do FT:
$F_{real_space}=e^{i\vec{k}r} t^{\prime} (\tau_{x,y,z})^2$

Now, if we capture the viberation relaxation mode around polaron, we can capture all the things belong to polaron.
