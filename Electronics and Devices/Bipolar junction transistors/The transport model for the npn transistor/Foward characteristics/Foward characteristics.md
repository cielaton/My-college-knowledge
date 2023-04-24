![[Pasted image 20230315131019.png]]

The base-emitter voltage ($v_{BE}$) establishes emitter current $i_E$ which equal to the total current crossing the base-emitter junction.  This current is composed of two components:
- The **foward-transport current $i_F$**, enter the collector, travels completely the base region, and exits the emitter.
- The **collector current** $i_C = i_F$, which has the form of an ideal diode current:

>[!note] 
>$$i_C=i_F=I_S\left[\exp\left(\frac{v_{BE}}{V_T}\right)\right]$$

$i_F$ is a much smaller component of current crosses the base-emitter junction. This forms the base current $i_B$ of the transistor:

>[!note]
>$$i_B = \frac{i_F}{\beta_F} = \frac{I_S}{\beta_F}\left[\left(\frac{v_{BE}}{V_T}\right)-1\right]$$

The parameter $\bf{\beta_F}$  is called **forward common-emitter current gain**.
$$10 \leq \beta_F\leq500$$

>[!note]
>We can obtain $i_E$ by treating the transistor as a super node and apply KCL:
>$$i_E = i_B + i_C$$

Which can be expressed as:
$$i_E = \left(I_S + \frac{I_S}{\beta_F}\right)\left[\exp\left(\frac{v_{BE}}{V_T}\right )- 1\right]= \frac{I_S}{\alpha_F}\left[\exp\left(\frac{v_{BE}}{V_T}\right) - 1\right]$$

>[!note]
>Where
>$$\alpha_F = \frac{\beta_F}{\beta_F + 1}$$
>or 
>$$\beta_F = \frac{\alpha_F}{1 - \alpha_F}$$

The parameter $\bf{\alpha_F}$ is called **forward common-base current gain**.
$$0.95 \leq \alpha_F\leq1.0$$

There are three extremely useful auxiliary relationships are

$$\frac{i_C}{i_B} = \beta_F $$
$$i_E=(\beta_F+1) i_B $$
$$\frac{i_C}{i_E}=\alpha_F$$

Because the current gain $\beta_F \gg  1$, injection of a small current into the base can produces a much larger $i_C$ and $i_E$

The value $\alpha_F \cong 1$ also tell us that the collector and emiter current are almost identical.