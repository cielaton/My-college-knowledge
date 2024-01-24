In saturation region, the *dc* value of $v_{CE}$ is called the **saturation voltage** of the transistor:
- $v_{CESAT}$ for the *npn* transistor
- $v_{ECSAT}$ for the *pnp* transistor

<center><em>Relationship between the terminal voltages of the transistor</em></center>

![[Pasted image 20230331153724.png]]

We assume that both junctions are forward-biased, so that $i_C$ and $i_B$ can be approximated as
$$i_C = I_S\;exp\left(\frac{v_{BE}}{V_T}\right) - \frac{I_S}{\alpha_R}exp\left(\frac{v_{BC}}{V_T}\right)$$
$$i_B = \frac{I_S}{\beta_F}exp\left(\frac{v_{BE}}{V_T}\right) + \frac{I_S}{\beta_R}exp\left(\frac{v_{BC}}{V_T}\right)$$

using $\beta_R = \alpha_R/(1 - \alpha_R)$  yield:
$$v_{BE} = V_T\;ln\frac{i_B + (1 - \alpha_R) i_C}{I_S\left[\frac{1}{\beta_F} + (1 - \alpha_R\right]} $$
$$v_{BC} = V_T \;ln \frac{i_B - \frac{i_C}{\beta_F}}{I_S \left[\frac{1}{\alpha_R}\right]\left[\frac{1}{\beta_F} + (1 - \alpha_R) \right]}$$
From $v_{CE} = v_{BE} - v_{BC}$, web obtain an expression for the saturation voltage of the *npn* transistor:

>[!note]
>$$v_{CESAT} = V_T\;ln\left[\left(\frac{1}{\alpha_R}\right) \frac{1 + \frac{i_c}{(\beta_R + 1)i_B}}{1-\frac{i_C}{\beta_Fi_B}}\right]$$

<center><em>Simplified model for the npn transistor in saturation</em></center>

![[Pasted image 20230331155607.png]]