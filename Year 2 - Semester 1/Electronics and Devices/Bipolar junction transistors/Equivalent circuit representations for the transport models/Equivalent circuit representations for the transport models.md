For circuit simulation, as well as hand analysis purpose, the transport model equations for the *npn* and *pnp* transistors can be represented by the equivalent circuits:

<center><em>npn transistor</em></center>

![[Pasted image 20230328182925.png]]

<center><em>pnp transistor</em></center>

![[Pasted image 20230328183035.png]]


$i_T$ : The current traversing the base.
We have:

$$i_T = i_F - i_R = I_S \left[exp\left(\frac{v_{BE}}{V_T}\right) - expt\left(\frac{v_{BC}}{V_T}\right)\right]$$

The diode currents correspond directly to the two components of the base current: 

$$i_B = \frac{I_S}{\beta_F}\left[exp\left(\frac{v_{BE}}{V_T} - 1\right) - exp\left(\frac{v_{BC}}{V_T}\right)\right]$$
