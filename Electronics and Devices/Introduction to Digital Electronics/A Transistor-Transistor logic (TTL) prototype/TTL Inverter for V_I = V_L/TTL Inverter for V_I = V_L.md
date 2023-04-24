<center><em>TTL gate with input v_I = V_L</em></center>

![[Pasted image 20230413184653.png]]

The input voltage is set to $V_L = V_{ECSAT} = 0.15$

The $+5 V$ supply tends to force the current $i_{B1}$ down the $4 k\ohm$ resistor and into the base of $Q_1$, turn on the base-emitter diode of $Q_1$

Transistor $Q_1$ attempts to pull a collector current $i_{C1} = \beta_F i_{B1}$ out of $Q_2$, but only leakage current can flow out of the base → $i_C \cong 0$

Because $Q_1$ is operating with $\beta_F i_B > i_C$, it saturates (short circuit), with both junctions being forward-biased. The voltage at the base of $Q_2$ is given by:
$$v_{BE2} = v_I + V_{CESAT1} = 0.15 + 0.04 = 0.19V$$ 
Since $v_{BE2}$ is only 0.19V and $Q_2$ does not conduct any substantial collector current → The output will be $v_o = V_{CC} = 5V$