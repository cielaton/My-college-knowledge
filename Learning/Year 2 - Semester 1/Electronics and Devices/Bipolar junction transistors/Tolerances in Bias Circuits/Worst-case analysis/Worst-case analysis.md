**Worst-case analysis** is often used to ensure that a design will function under an expected set of component variations.

![[Pasted image 20230409150924.png]]

>[!question]
>Find the worst-case values of $I_C$ and $V_{CE}$ for the transistor. Assume that the 12V power supply has a 5 percent tolerance and the resistors have 10 percent tolerances. 
>Also, the transistor current gain has a nominal value of 75 with a 50 percent tolerance.

==Simplified analysis==:
$$I_C \cong i_E = \frac{V_{EQ} - V_{BE}}{R_E}$$
(assume $V_{BE}$ is fixed at 0.7V)
The extreme value of $V_{EQ}$:
$$V_{EQ} = V_{CC} \frac{R_1}{R_1 + R_2} = \frac{V_{CC}}{1 + \frac{R_2}{R_1}}$$

Thus, 
$$V_{EQ}^{max} = \frac{12V (1.05)}{1 + \frac{36k\ohm(0.9)}{18k\ohm(1.1)}} = 4.78V$$
$$V_{EQ}^{min} = \frac{12V(0.95)}{1 + \frac{36k\ohm(1.1)}{18k\ohm (0.9)}} = 3.31V$$
For $I_C$:
$$I_C^{max} = \frac{4.78V - 0.7V}{14,400\ohm} = 283\micro A$$
$$I_C^{min} = \frac{3.31V - 0.7V}{17,600 \ohm} = 148\micro A$$

For $V_{CE}$,
$$V_{CE} \cong V_{CC} - I_CR_C - V_{EQ} + V_{BE}$$
The extreme of $V_{CE}$ are:
$$V_{CE}^{max} \cong 12V(1.05) - (148\micro A)(22k\ohm \times 0.9) - 3.31V + 0.7V = 7.06V$$
$$V_{CE}^{min} \cong 12V(0.95) - (283\micro A)(22k\ohm \times 1.1) - 4.78V+ 0.7V = 0.471V \; \rightarrow \; \text{Saturated !}$$