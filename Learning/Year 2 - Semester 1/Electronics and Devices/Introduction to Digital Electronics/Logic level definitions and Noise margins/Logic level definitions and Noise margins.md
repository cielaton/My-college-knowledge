<center><em>Inverter operating with power supplies of 0V and  V+</em></center>

![[Pasted image 20230412185241.png]]

<center><em>Simple inverter circuit comprising a load resistor and switch</em></center>

![[Pasted image 20230412185503.png]]

- When closed, the switch forces $v_o$ to $V_L$
- When open, the resistor sets the output to $V_H$

>For example, $V_L = 0V$ and $V_H = V_+$

<center><em>Inverter with NMOS switch (left) and inverter with BJT switch (right)</em></center>

![[Pasted image 20230412185710.png]]


The transistor switch between two states:
- Nonconducting or *off*
- Conducting or *on*

Load resistor sets the output voltage to $V_H = V_+$ when switching transistor is off
If the input voltage exceeds the threshold voltage of $M_S$ or the turn-on voltage of the base-emitter junction of $Q_S$, the transistor conduct a current that cause the output voltage to drop to $V_L$.

<center><em>Voltage levels and logic state relationships for positive logic</em></center>

![[Pasted image 20230412192343.png]]

When the input $v_I$ is below the **input low-logic-level $V_{IL}$**, the output is defined to be in the high output or 1 state.
As the input voltage increases, the output voltage $v_o$ falls until it reaches the low output or 0 state as $v_I$ exceeds the voltage of the **input high-logic-level $V_{IH}$**.

Voltages below $V_{IL}$ are reliably recognized as logic 0s at the input of a logic gate, and voltages above $V_{IH}$ are recognized reliably as logic 1s at the input.

>[!note]
>Voltages corresponding to the region between $V_{IL}$ and $V_{IH}$ do not represent valid logic input levels

1. [[Logic Voltage level]]
2. [[Noise margins]]
3. [[Logic gate design goal]]

