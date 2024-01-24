Consider the voltage amplifier with the two-port is a Thévenin equivalent representation of the input source, and the output is connected to a load represented by resistor $R_L$

![[Pasted image 20230421170849.png]]

To find the voltage gain, voltage division is applied to each loop:
$$v_o = Av_1\frac{R_L}{R_{out} + R_L} \hspace{20pt} and \hspace{20pt} v_1 = v_i \frac{R_{in}}{R_1 + R_{in}}$$
For the magnitude of the voltage gain $A_v$
$$|A_v| = \frac{V_o}{V_i} = A \frac{R_{in}}{R_I + R_{in}} \frac{R_L}{R_{out} + R_L}$$
For the case when $R_{in} \gg R_I$ and $R_{out} \ll R_L$ (maximum voltage gain)
$$|A_v| \cong A$$
>[!note]
>An **ideal voltage amplifier** satisfies $R_{in} = \infty$ and $R_{out} = 0$

