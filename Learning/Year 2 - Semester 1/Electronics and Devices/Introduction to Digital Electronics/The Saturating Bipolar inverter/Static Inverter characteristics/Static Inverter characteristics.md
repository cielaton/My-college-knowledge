For the output voltage of the inverter:
$$v_o = V_{CC} - i_CR_C$$
>[!note]
>If $v_{BE} = v_I$ is several hundred milivolts less than $V_{on}$, then $Q_2$ is nearly cut off ($i_C \cong 0$)
>$$v_o = V_H \cong V_{CC}$$

In this particular circuit:
- $V_H$ is set by the power supply voltage: $V_H = 5V$
- The low-state output level is set by the saturation voltage $V_L = V_{CESAT}$

To ensure saturation
$$i_B > \frac{i_{CMAX}}{\beta-F} \hspace{20pt}\text{and} \hspace{20pt} i_{CMAX} = \frac{v_{CC} - V_{CESAT}}{R_C} \cong \frac{V_{CC}}{R_C}$$




