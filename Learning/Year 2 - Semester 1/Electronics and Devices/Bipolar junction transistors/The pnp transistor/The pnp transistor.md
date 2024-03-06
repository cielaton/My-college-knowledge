The *pnp* transistor is fabricated by reversing the layers of the transistor.

![[Pasted image 20230316184712.png]]

- The emitter now is at the top of the diagram.
- The arrows again indicate the normal directions of positive current.
- The voltage applied to the two *pn* junctions are the emitter-base voltage $v_{EB}$ and the collector-base voltage $v_{CB}$.
- These voltages are again positive when they forward-bias their respective *pn* junctions.
<center><em>circuit symbol for the pnp transistor</em></center>

![[Pasted image 20230316185336.png]]

The arrow identifies the **emitter** of the *pnp* transistor and points in the **direction of normal positive-emitter current**.

## Forward characteristic
![[Pasted image 20230316190541.png]]

The voltage $v_{EB}$ is applied to the emitter-base junction, and $v_{CB} = 0$ .
The $v_{EB}$ establishes forward-transport current $i_F$ that traverses the narrow base region and base current $i_B$ that crosses the emitter-base junction of the transistor:
$$i_C = i_F = I_S\left[\exp\left(\frac{v_{EB}}{V_T}\right) -1\right]$$
$$i_B = \frac{i_F}{\beta_F} = \frac{I_S}{\beta_G}\left[\exp\left(\frac{v_{EB}}{V_T}\right) - 1\right]$$
$$i_E = i_C + i_B$$

## Reverse characteristic
![[Pasted image 20230316191404.png]]

The $v_{CB}$ now establishes the reverse-transport current $i_R$ and base current $i_B$:
$$i_E=-i_R = -I_S\left[\exp\left(\frac{v_{CB}}{V_T}\right) - 1\right]$$
$$i_B = \frac{i_R}{\beta_R} = \frac{I_S}{\beta_R}\left[\exp\left(\frac{v_{CB}}{V_T}\right)-1\right]$$
$$i_C = -I_S\left(1 + \frac{1}{\beta_R}\right)\left[\exp\left(\frac{v_{CB}}{V_T}\right) - 1\right]$$

## For general-bias situation:

$$i_C = I_S\left[\exp\left(\frac{v_{EB}}{V_T}\right) -\exp\left(\frac{v_{CB}}{V_T}\right)\right] - \frac{I_S}{\beta_R}\left[\exp\left(\frac{v_{CB}}{V_T}\right) - 1\right]$$
$$i_E = I_S\left[\exp\left(\frac{v_{EB}}{V_T}\right) -\exp\left(\frac{v_{CB}}{V_T}\right)\right] + \frac{I_S}{\beta_F}\left[\exp\left(\frac{v_{CB}}{V_T}\right) - 1\right]$$
$$i_B=\frac{I_S}{\beta_F}\left[\exp\left(\frac{v_{EB}}{V_T}\right) - 1\right] + \frac{I_S}{\beta_R}\left[\exp\left(\frac{v_{CB}}{V_T}\right) - 1\right]$$
