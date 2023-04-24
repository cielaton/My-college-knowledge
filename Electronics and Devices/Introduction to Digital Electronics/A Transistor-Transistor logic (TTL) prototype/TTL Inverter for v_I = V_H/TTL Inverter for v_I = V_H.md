<center><em>TTL gate with input v_I = V_H</em></center>

![[Pasted image 20230413191235.png]]

Because the base emitter of $Q_1$ is at 5V, base current $i_{B1}$ cannot enter the base-emitter diode; it instead forward-biases the base-collector diode

$Q_1$ enter the reverse-active region with the base-collector junction forward-biased and the base-emitter junction reverse-biased.

Base current $i_{B1}$ causes a current $(\beta_R + 1)i_{B1}$ exit the collector terminal, become the base current of $Q_2$

A current $\beta_Ri_{B1}$ enters the emitter terminal, and this current represents the input current $i_{IH}$.
>A small value of $\beta_R$ is desired to keep $i_{IH}$ low.

The voltage $v_{B1} = v_{BC1} + V_{BESAT2} = 0.7 + 0.8 = 1.5V$