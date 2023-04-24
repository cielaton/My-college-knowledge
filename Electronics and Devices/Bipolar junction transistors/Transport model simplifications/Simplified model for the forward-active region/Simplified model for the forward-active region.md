The forward-active region of a *npn* transistor corresponds to $v_{BE}\geq0$ and $v_{BC} \leq 0$. In most cases, the forward-active region will have:
$$v_{BE} > 4\frac{kT}{q} = 0.1V \hspace{25pt} and \hspace{25pt}  v_{BC} < -4\frac{kT}{q}= -0.1V $$
Assume that $exp(-v_{BC}/V_T \ll1$ :
$$i_C = I_S \;exp\left(\frac{v_{BE}}{V_T}\right) + \frac{I_S}{\beta_R}$$
$$i_E = \frac{I_S}{\alpha_F} exp\left(\frac{v_{BE}}{V_T}\right) + \frac{I_S}{\beta_F}$$
$$i_B = \frac{I_S}{\beta_F} exp\left(\frac{v_{BE}}{V_T}\right) - \frac{I_S}{\beta_F} - \frac{I_S}{\beta_R}$$
By neglecting the small terms, we find the most useful simplifications:
>[!note]
>$$i_C = I_S\;exp\left(\frac{v_{BE}}{V_T}\right) \hspace{25pt} i_E=\frac{I_S}{\alpha_F}exp\left(\frac{v_{BE}}{V_T}\right) \hspace{25pt} i_B = \frac{I_S}{\beta_F} exp\left(\frac{v_{BE}}{V_T}\right)$$

By taking rations of the terminal currents:
>[!note]
>$$i_C=\alpha_Fi_E \hspace{25pt} and \hspace{25pt} i_C = \beta_Fi_B$$

From $i_E = i_C + i_B$:

>[!note]
>$$i_E = (\beta_F + 1)i_B$$

<center><em>Simplified model for the forward-active region</em></center>

![[Pasted image 20230330212041.png]]

<center><em>Further simplication for the forward-active region using the CVD (constant voltage drop)  model for the diode.</em></center>

![[Pasted image 20230330212218.png]]