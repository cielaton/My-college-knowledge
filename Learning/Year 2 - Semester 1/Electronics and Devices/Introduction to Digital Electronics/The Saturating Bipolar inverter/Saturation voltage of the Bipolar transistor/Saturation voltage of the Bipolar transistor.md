An expression for **saturation voltage** of the BJT in terms of its base and collector current:
$$V_{CESAT} = V_T \; ln \left[\left(\frac{1}{\alpha_R}\right)\frac{1 + \frac{\beta_{FOR}}{\beta_R + 1}}{1 - \frac{\beta_{FOR}}{\beta_F}}\right] \hspace{20pt} \text{for} \hspace{20pt} i_B > \frac{i_C}{\beta_F}$$
and $\beta_{FOR} = \frac{i_C}{i_B}$

When $i_B$ becomes very large or $i_C$ becomes very small, $V_{CESAT}$ reaches the minimum value:

>[!note]
>$$V_{CESAT}^{MIN} = V_T \; ln\left(\frac{1}{\alpha_R}\right) = V_T \; ln\left(\frac{\beta_R + 1}{\beta_R}\right)$$
For  $i_B$, 
$$i_B \geq \frac{I_C}{\beta_F}\left[\frac{1 + \frac{\beta_F}{\beta_R\Gamma}}{1 + \frac{1}{\alpha_R\Gamma}}\right] \hspace{20pt} \text{where} \hspace{20pt} \Gamma = exp\left(\frac{V_{CESAT}}{V_T}\right)$$
