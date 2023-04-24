One common objective of diode circuit analysis is to find the **quiescent operating point (Q-point)**, or **bias point**.
- The Q-point consist of the dc current and voltage ( ${I_D}$, $V_D$ ) -> The point of operation on the diode's *i-v* characteristic.

![[Pasted image 20230307123001.png|center]]

Start by a loop equation:
$${V = I_DR + V_D}$$
## Load-line analysis (graphical):

![[Pasted image 20230307133743.png|center]]

## Mathematical model:
## The ideal diode model:
If diode is conducting:
- Forward-bias: The voltage across the diode is 0 (short circuit).
	$V_D = 0$ for $i_D > 0$
- Reverse-bias: The current through the diode is zero ($V_D$ < 0, open circuit).
	$i_D = 0$ for $v_D \leq 0$

![[Pasted image 20230307140355.png]]

![[Pasted image 20230307140232.png]]

#### The process:
1. Select a model for the diode
2. Identify the anode and cathode of the diode and label the diode voltage $V_D$ and current $i_D$
3. **Make an (educated) guess concerning the region of operation of the diode based on the circuit configuration**
4. Analyze the circuit using the diode model appropriate for the assumption in step 3
5. Check the results to see if they are consistent with the **assumptions**

![[Pasted image 20230307141803.png]]


|       Forward-bias assumption:       | Reverse-bias assumption:             |
|:------------------------------------:| ------------------------------------ |
| ![[Pasted image 20230307141818.png]] | ![[Pasted image 20230307141818.png]] |

## Constant voltage drop model:
This consist of an ideal diode with a constant voltage $V_{on}$ (adding this to improve the model).
**A reasonable choice for $V_{on}$ is 0.6 to 0.7**

![[Pasted image 20230307143930.png]]

![[Pasted image 20230307143947.png]]

<center><em>Circuit with ideal diode replaced by the piecewise linear model:</em></center>

![[Pasted image 20230307144501.png]]

We now have:
- $V_D = V_{on}$ for $i_D > 0$
- $i_D = 0$ for $V_D \leq V_{on}$

