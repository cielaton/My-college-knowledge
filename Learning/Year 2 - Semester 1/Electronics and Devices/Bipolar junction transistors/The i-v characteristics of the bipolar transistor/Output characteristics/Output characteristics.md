<center><em>Circuit for measuring or simulating the common-emitter output characteristics</em></center>

![[Pasted image 20230330184232.png]]

The base of the transistor is driven by a constant current source, and the output characteristic represent a graph of $i_C$ vs $v_{CE}$ for the *npn* transistor (or $i_C$ vs $v_{EC}$ for the *pnp*)  with base current $i_B$ as a parameter.

<center><em>The npn transistor operating</em></center>

![[Pasted image 20230330185524.png]]

Consider when $v_{CE} \geq 0$:
- For $i_B = 0$ the transistor is non-conducting or cut off. As $i_B$ increase above 0, $i_C$ also increases.
- For $v_{CE} \geq v_{BE}$, the *npn* transistor is in the **foward-active region**, and collector current is **independent** of $v_{CE}$ and equal to $\beta_Fi_B$.
- For $v_{CE} \leq v_{BE}$, the transistor enters the **saturation region** of operation in which the total voltage between the collector and emitter terminals of the transistor is small.

Consider when $v_{CE} \leq 0$:
- For $v_{BE} \leq v_{CE} \leq 0$, the transistor remains in saturation.
- For $v_{CE}\leq v_{BE}$, the transistor enters the **reverse-active** region, in which the i-v characteristics again become independent of $v_{CE}$, and now $i_C \cong -(\beta_R + 1) i_B$.

>[!note]
>For the *pnp* transistor, the output characteristics will appear exactly the same, except that the horizontal axis will be the voltage $v_{EC}$ rather than $v_{CE}$
