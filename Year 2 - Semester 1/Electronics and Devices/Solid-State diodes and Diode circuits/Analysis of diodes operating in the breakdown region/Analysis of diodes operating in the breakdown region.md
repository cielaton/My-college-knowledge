## Analysis with the piecewise linear model
Since the diode current $I_D < 0$ → The Zener current $I_Z = -I_D > 0$

<center><em>Load line for Zener diode</em></center>

![[Pasted image 20230307154048.png]]

| Circuit containing a Zener diode     | Corresponding piecewise linear model |
| ------------------------------------ | ------------------------------------ |
| ![[Pasted image 20230307154358.png]] | ![[Pasted image 20230307154429.png]] |


The loop equation in terms of $I_Z$ gives: $I_Z = 2.94mA$
Because $I_Z$ must greater than 0 ( $I_D < 0$ ) -> **Valid** 

## Voltage regulation

<center><em>Zener diode voltage regulator circuit</em></center>
![[Pasted image 20230307155417.png]]

The function of the Zener diode is to maintain a constant voltage across load resistor $R_L$. As long as the diode is operating in reverse breakdown, a voltage of approximately $V_Z$ will appear across $R_L$

**We must have $I_Z > 0$** (To ensure the diode is operating in the Zener breakdown region)
$$I_S=\frac{V_S-V_Z}{R} = \frac{20 - 5V}{5k\Omega} = 3mA$$
$$I_L=\frac{V_Z}{R_L}=\frac{5V}{5k\Omega}=1mA$$
Resulting the Zener current $I_Z= I_S = I_L=2mA$ -> **Valid when $I_Z > 0$**
The diode will continue to act as a voltage regulator when:
$$R_L>\frac{R}{(\frac{V_S}{V_Z}-1)}=R_{min}$$


## Analysis with the piecewise linear model
The output voltage is now a function of the current $I_Z$ through the Zener diode

<center><em>Zener diode regulator circuit, including Zener resistance</em></center>
![[Pasted image 20230307165958.png]]

Apply node-voltage method yields: 
$$\frac{V_L-20V}{5000\Omega} + \frac{V_L-5V}{100\Omega} + \frac{V_L}{5000\Omega} = 0$$
-> $V_L=5.19V$
The Zener diode $$I_Z = \frac{V_L - 5V}{100} = \frac{5.19V - 5V}{100\Omega} = 1.90mA > 0$$-> **Valid**

## Line and load regulation
- **Line regulation:** How sensitive the output voltage is to input voltage changes
	$$\frac{dV_L}{dV_S}$$
- **Load regulation:** How sensitive the output voltage is expressed.
$$\frac{dV_L}{dI_L}$$
