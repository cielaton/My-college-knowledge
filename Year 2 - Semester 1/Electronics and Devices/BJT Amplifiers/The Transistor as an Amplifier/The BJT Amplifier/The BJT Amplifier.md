<center><em>BJT biased in the active resion by the voltage source $V_{BE}$. A small sinusoidal signal voltage $v_{be}$ is applied in series with $V_{BE}$ and generates a similar but larger  amplitude waveform at the colllector. </em></center>

![[Pasted image 20230421175339.png]]

<center><em>Load line, Q-point and signals for the above circuit</em></center>

![[Pasted image 20230421175505.png]]

The fixed base-emitter voltage of 0.700 V sets the Q-point to be $(I_C, V_{CE}) = (1.5 mA, 5V)$ with $I_B = 15 \micro A$

Both $I_B$ and $V_{BE}$ have been shown as parameters on the output characteristics (usually only $i_B$ is given).

>To provide amplification, a signal must be injected into the circuit in a manager that causes the transistor voltages and currents to vary with the applied signal

Total base-emitter voltage becomes:
$$v_{BE} = V_{BE} + v_{be}$$
The collector-emitter voltage of the BJT can be expressed as:
$$v_{CE} = 10 - i_CR_C = 10 - 3300i_C$$
A small voltage change at the base causes a large voltage change at the collector:
$$A_v = \frac{V_{ce}}{V_{be}} = \frac{1.65\angle 180^\circ}{0.008 \angle 0^\circ} = 206 \angle 180^\circ = -206$$
>[!note]
>The minus sign indicates $180^\circ$ phase shift between the input and output signals.