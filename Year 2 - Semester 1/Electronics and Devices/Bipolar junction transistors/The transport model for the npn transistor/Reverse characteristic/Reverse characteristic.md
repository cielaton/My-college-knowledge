![[Pasted image 20230316172722.png]]


- $v_{BC}$ is applied to the base-collector junction.
- Base-emitter junction is in zero-biased. 

The $v_{BC}$ establishes $i_C$, now crossing the base-collector junction. The largest portion of the collector current, the reverse-transport current $i_R$, enter s the emitter, travels completely across the narrow base region, and exits the collector terminal.

>[!note]
>The current $i_R$ has a form identical to $i_F$:
>$$i_R =I_S \left[\left(\exp\frac{v_{BC}}{V_T}\right) -1\right]$$
>and
>$$i_E = -i_R$$

In this case, a fraction of the current $i_R$ must also be supplied as base current through the base terminal: 

>[!note]
>$$iB = \frac{i_R}{\beta_R}=\frac{I_S}{\beta_R}\left[\exp\left(\frac{v_{BC}}{V_T}\right) - 1\right]$$

The parameter $\bf{\beta_R}$ is called the **reverse common-emitter current gain**.
$$0<\beta_R\le 10 \ \ \ whereas \ \ \ 10 \le \beta_F \le 500$$

Similarly to the *forward bias*, apply KCL for the imaginary node of the transistor:
$$i_C =-\frac{I_S}{\alpha_R}\left[\exp\left(\frac{v_{BC}}{V_T}\right) - 1\right]$$
> The minus symbol is because $i_E = -i_R$

>[!note]
>Where
>$$\alpha_F = \frac{\beta_F}{\beta_F + 1}$$
>or 
>$$\beta_F = \frac{\alpha_F}{1 - \alpha_F}$$

The parameter $\bf{\alpha_F}$ is called **forward common-base current gain**.
$$0.95 \leq \alpha_F\leq1.0$$

