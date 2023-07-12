<center><em>Audio amplifier channel from FM device</em></center>

![[Pasted image 20230420185747.png]]

In this case, the input to the stereo amplifier channel is represented by the Thévenin equivalent source $v_I$ and source resistor $R_1$. The speaker at the output is modeled by an 8-$\ohm$ resistor.

We will consider only the ith component of the signal, with frequency $\omega_i$ and amplitude $V_i$ 
$$v_i = V_i \sin \omega_it$$
The output will be different in amplitude $V_0$ and phase $\theta$:
$$v_o = V_o \sin(\omega_it + \theta)$$

1. [[Voltage gain]]
2. [[Current gain]]


The **power gain** $A_p$ is defined as the ratio of the output power $P_o$ delivered to the load, to the power $P_i$ delivered from the source:
$$A_P = \frac{P_o}{P_i} = \frac{V_o}{V_i}\frac{I_o}{I_i} = |A_v||A_{i|}$$

---

The various gain expressions often involve some rather large numbers, so it can be express in terms of the **decibel**, or **dB**:
- $A_{PdB} = 10 \log A_p$ 
- $A_{vdB} = 20 \log |A_v|$
- $A_{idB} = 20 log |A_i|$

![[Pasted image 20230420193523.png]]
