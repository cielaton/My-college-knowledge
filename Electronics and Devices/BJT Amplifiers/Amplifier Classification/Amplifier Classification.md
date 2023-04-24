In the forward active region:
$$i_C = I_S \exp \left(\frac{v_{BE}}{V_T}\right)\hspace{10pt} i_E = \frac{I_S}{\alpha_F}\exp \left(\frac{v_{BE}}{V_T}\right) \hspace{10pt} i_B = \frac{I_S}{\beta_F}\exp \left(\frac{v_{BE}}{V_T}\right)$$
<center><em>Four-resistor bias circuits for the BJT</em></center>

![[Pasted image 20230423140447.png]]

To cause $i_C, i_E$, and $i_B$ to vary significantly, we need to change $v_{BE} = v_B - v_E$

- An input signal can be injected into the circuit to vary the voltage at either the base or the emitter of the transistor.
	Even if the Early voltage is considered, collector voltage has negligible effect on terminal currents.
- Substantial changes in collector or emitter currents can create large voltage drops across the collector and emitter resistors ⇾ The collector or emitter can be used to extract an output.

>[!note]
>Since $i_B$ is a factor of $\beta$ smaller than $i_c \text{ or } i_E$ currents, the base terminal is not used as an output.

These constraints yield 3 families of amplifiers:
- [[Common-Emitter (C-E)]]
- [[Common-Collector (C-C)]]
- [[Common-Base (C-B)]]

All circuit example use the *4 resistor bias circuits* to establish the Q-point of the various amplifiers.

**Coupling and bypass** capacitors are used to change the dc and ac equivalent circuits.