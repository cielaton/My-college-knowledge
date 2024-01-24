**Monte Carlo analysis** uses randomly selected versions of a given circuit to predict its behavior from a statistical basis.

By using the function RAND() from Excel, the power supply resistors, and current gain are represented as:
$$V_{CC} = 12(1 + 0.1(RAND() - 0.5))$$
$$R_1 = 18,000(1+0.2(RAND() - 0.5))$$
$$R_2= 36,000(1 + 0.2 (RAND() - 0.5 ))$$
$$R_E = 16,000(1+0.2(RAND() - 0.5))$$
$$R_C = 22,000(1 + 0.2(RAND() - 0.5))$$
$$\beta_F = 75(1 + (RAND() - 0.5))$$

The above equations are used to evaluate
$$V_{EQ} = V_{CC} \frac{R_1}{R_1 + R_2}$$
$$R_{EQ} = \frac{R_1R_2}{R_1 + R_2}$$
$$I_B = \frac{V_{EQ} - V_{BE}}{R_{EQ} + (\beta_F + 1) R_E}$$
$$I_C = \beta_F I_B$$
$$I_E = \frac{I_C}{\alpha_F}$$
$$V_{CE} = V_{CC} - I_C R_C -I_E R_E$$

![[Pasted image 20230409155837.png]]
