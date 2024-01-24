The four-resistor bias network is much preferred for establishing a stable Q-point for the transistor.

To inject an input signal and extract an output signal without disturbing the Q-point, one method is to use **ac coupling** through capacitors.
The values of these capacitors are chosen to have negligible impedance in the frequency range of interest, but at the same time, the capacitors provide open circuits at dc so the Q-point is not distributed.

![[Pasted image 20230422115608.png]]

Input signal $v_i$ is *coupled* onto the base node of the transistor through capacitor $C_1$, and the signal developed at the collector is coupled to load resistor $R_3$ through capacitor $C_2$, $C_1$ and $C_2$ are referred to as **coupling capacitors** or **dc blocking capacitors**.

> $C \rightarrow \infty$ indicate the values of the capacitor is very large →the reactance will be negligible

The third capacitor $C_3$ is called **bypass capacitor**. This capacitor provides a low impedance path for ac current to *bypass* emitter resistor $R_4$ → $R_4$ can be removed.




