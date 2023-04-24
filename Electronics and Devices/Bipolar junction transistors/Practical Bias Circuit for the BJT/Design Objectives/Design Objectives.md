>[!question]
>Design a four resistor bias circuit to give a Q-point of (750 $\micro$A, 5V) using a 15-V supply with an *npn* transistor having a minimum current gain of 100

==Unknown==:
$V_B, V_E, V_C, R_1, R_2, V_C, V_E$

==Assumption==:
The transistor is to operate in the forward-active region -> $V_{BE} = 0.7V$

==Analysis==:
Fist, to calculate the value of $V_C$ and $V_E$, divide the remaining power supply voltage ($V_{CC} - V{CE} = 10V$) equally between $R_E$ and $R_C$.
Thus, $V_E = 5V$ and $V_C = 5 + V{CE} = 10V$. The value of $R_C$ and $R_E$ are then given by:
$$R_C = \frac{V_{CC} - V_C}{I_C} = \frac{5V}{750\micro A} = 6.67k\ohm$$ and 
$$R_E = \frac{V_E}{I_E} = \frac{5V}{758\micro A} = 6.60 k\ohm$$

The base voltage is given by
$$V_B = V_E + V_{BE} = 5 + 0.7 = 5.7V$$
We know that $I_B = I_C/\beta_F = 7.5\micro A$
- Choose $I_2 = 10 I_B$, we have $I_2 = 75\micro A$
- $I_1 = 9I_B$ by KCL, we obtain $I_1 = 67.5\micro A$

$R_1$ and $R_2$ can be determined by:
$$R_1 = \frac{V_B}{9I_B} = \frac{5.7V}{67.5\micro A} = 84.4 k\ohm$$
$$R_2 = \frac{V_{CC} - V_B}{10 I_B} = \frac{15-5.7V}{75\micro A} = 124k\ohm$$

![[Pasted image 20230409150218.png]]
