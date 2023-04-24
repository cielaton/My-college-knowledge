One of the best circuits for stabilizing the Q-point of a transistor is the four-resistor bias network:

![[Pasted image 20230406205449.png]]

- $R_1 \text{ and } R_2$ form a resistive voltage divider across the power supplies (12V and 0V) and attempt to establish a fixed voltage at the base of transistor $Q_1$.
- $R_E \text{ and } R_C$ are used to define $i_E \text{ and } V_{BE}$ of the transistor.

The first steps in analysis are to split the power supply into two equal voltages:

![[Pasted image 20230406210331.png]]

Then simplify the circuit by replacing the *base-bias* network by its Thévenin equivalent circuit, $V_{EQ} \text{ and } R_{EQ}$ are given by
$$V_{EQ} = V_{CC} \frac{R_1}{R_1 + R_2} \hspace{30pt} R_{EQ} = \frac{R_1 R_2}{R_1 + R_2}$$
> For the above value, $V_{EQ} = 4$ and $R_{EQ} = 12 k\ohm$

![[Pasted image 20230406210939.png]]
<center><em>Thévenin simplification of the four-resistor bias network</em></center>

![[Pasted image 20230406211050.png]]
<center><em>Load line for the four-resistor bias circuit</em></center>

---

Using KVL for loop 1:
$$V_{EQ} = I_BR_{EQ} + V_{BE} + I_ER_E = I_BR_{EQ}  + V_{BE} + (\beta_F + 1) I_BR_E$$
Solving for $I_B$ yields:
>[!note]
>$$I_B = \frac{V_{EQ} - V_{BE}}{R_{EQ} + (\beta_F + 1) R_E} \hspace{20pt} \text{where} \hspace{20pt} V_{BE} = V_T \ln\left(\frac{I_B}{I_S/ \beta_F + 1}\right)$$
Assume that $V_{BE} = 0.6 \text{ to } 0.7$, we can obtain $I_B$ and $I_C = \beta_FI_B$ and $I_E = (\beta_F + 1)I_B$

We continue by using apply KCL for loop 2:
$$V_{CE} = V_{CC} - I_CR_C - I_ER_E = V_{CC} - I_C\left(R_C +\frac{R_E}{\alpha_F }\right)$$
>[!note]
>Since $I_E \cong I_C$, the above equation can be simplified to
$$V_{CE} \cong V_{CC} - I_C(R_C + R_E)$$


