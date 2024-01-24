>[!info]
>The basic **rectifier circuit** converts an **ac voltage** to a pulsating **dc voltage**. A **filter** is then added to eliminate the ac components of the waveform and produce a nearly constant dc voltage output.

## Half-wave rectifier with resistor load

<center><em>Half-wave rectifier circuit</em></center>

![[Pasted image 20230307172815.png|center]]


- For which $V_I > 0$ (first half), the source forces a current through diode $D_1$ -> $D_1$ is on
- For which $V_I < 0$ (second half), the negative current cannot exist, unless the diode is in breakdown, it will turn off.

| Diode is on                          | Diode is off                         |
| ------------------------------------ | ------------------------------------ |
| ![[Pasted image 20230307173532.png]] | ![[Pasted image 20230307173516.png]] |

| Input voltage | Output voltage |
| ------------- | -------------- |
| ![[Pasted image 20230307173847.png]]              |  ![[Pasted image 20230307173905.png]]              |

<center><em>CVD model for the rectifier on state</em></center>

![[Pasted image 20230307174401.png]]

For this case, the output voltage is one diode-drop smaller than the input voltage during the conduction interval:
$$V_O=(V_P\sin\omega t) - V_{on}$$

>[!info]
>In many applications, a **transformer** is used to convert from the 120-V ac, 60-Hz voltage available from the power line to the desired ac voltage level.
>
>![[Pasted image 20230307180414.png|center]]


## Rectifier filter capacitor

<center><bold>(Peak detector)</bold><em> Rectifier with capacitor load</em></center>

![[Pasted image 20230307175943.png]]

This circuit is similar to the above, except that the resistor is replaced with a **capacitor C** that is initially discharged $V_O(0) = 0$ 

| $0 \leq t \leq T/2$ | $t \geq T/2$ |
| ------------------- | ------------ |
| ![[Pasted image 20230307190912.png]]                    |        ![[Pasted image 20230307190947.png]]      |


<center><em> Input and output waveforms for the peak-detector circuit</em></center>

![[Pasted image 20230307191148.png]]

At the peak of the input voltage waveform, the current through diode $$i_D=C[d(v_1-V_{on})/dt < 0$$
-> The diode if off and the capacitor is disconnected from the rest.

>[!note]
>-> The capacitor charges up to a voltage one diode-drop below the peak of the input waveform and then remains constant, there by producing a dc output voltage:
$$V_{dc}=V_P-V_{on}$$

## Half-wave rectifier with RC load

<center><em>Half-wave rectifier circuit with filter capacitor</em></center>

![[Pasted image 20230307192606.png]]

| Diode on                             | Diode off |
| ------------------------------------ | --------- |
| ![[Pasted image 20230307193024.png]] | ![[Pasted image 20230307192953.png]]          |

<center><em>Input and output voltage waveforms for the half-wave rectifier circuit</em></center>

![[Pasted image 20230307193417.png]]


> The capacitor is again assumed to be initially discharged.
1. During the first quarter cycle, the diode conducts, and the capacitor is rapidly charged toward the peak value of the input voltage source.
2. The diode cuts off at the peak of $v_I$, and the capacitor voltage then discharges exponentially through R.
3. The discharge continue until the $v_O$ exceeds again (near the peak of the next cycle).

## Ripple voltage and conduction interval

- $V_r$ (**Ripple voltage**): residual periodic variation
- $\triangle T$ (**conduction interval**): A short time for the diode to conduct during each cycle.
- $\theta _c$ (**conduction angle**): The angular equivalent of $\triangle T$, where $\theta _c = \omega\triangle T$  

During the discharge period, the voltage across the capacitor is described by
$$v_o(t') = (V_P-V_{on})exp\left(-\frac{t'}{RC}\right) \hspace{1cm} \mathrm{for}\hspace{1cm} t'=\left(t-\frac{T}{4}\right) \geq 0$$

>[!note]
>Average value of the rectifier output voltage:
>$$V_{dc} = \frac{1}{T} \int_0^T v(t)dt = (V_P-V_{on}) - \frac{V_r}{2} $$
2

We have referenced the t' time axis to t = T/4 to simplify the equation. The ripple voltage $V_r$ is given by 
$$V_r = (V_P-V_{on}) - v_o(t')=(V_P-V_{on})\left[ 1-exp\left(-\frac{T - \triangle T}{RC}\right) \right]$$

>A small value of $V_r$ is desired in most power supply design

Using $exp(-x) \cong 1-x$ for small x result: 
$$V_r \cong (V_P-V_{on})\frac{T}{RC}\left(1 - \frac{\triangle T}{T}\right)$$
>[!note]
>A small ripple voltage means $\triangle T \ll T$, and the above expression becomes:
$$V_r \cong \frac{(V_P-V_{on})}{R}\frac{T}{C}$$

When the capacitor is discharged by a constant current, the discharge waveform is a straight line -> $V_r$ can be determined by an equivalent dc current:
>[!note]
>$$I_{dc}=\frac{V_P-V_{on}}{R}$$


>Discharging C for a time period T mean: $$\triangle V = \left(\frac{I_{dc}}{C}\right)T$$

>[!note]
>The conduction angle can be obtained by:
>$$\theta_c=\sqrt{\frac{2V_r}{V_P}}$$
>and the conduction interval:
>$$\triangle T = \frac{\theta_C}{\omega}=\frac{1}{\omega}\sqrt{\frac{2V_r}{V_P}}$$

## Diode current
There is a current present in the diode for only a very small fraction of T -> An almost constant dc current is flowing out of the filter to the load.
**The total charge lost each cycle must be replenished by the current through the diode during $\triangle T$** -> **High peak diode currents**. 

| Voltage waveforms | Diode current |
| ----------------- | ------------- |
| ![[Pasted image 20230309192630.png]]                  |      ![[Pasted image 20230309192659.png]]         |

<center><em>Triangular approximation to diode current pulse</em></center>

![[Pasted image 20230309193353.png]]

Equating the charge supplied through the diode during the conduction interval to the charge lost from the filter capacitor during the complete period:
$$Q = I_P\frac{\triangle T}{2}=I_{dc}T$$
>[!note]
> or 
>$$I_P=I_{dc}\frac{2T}{\triangle T}$$

## Surge current
When the power supply is first turned on, the capacitor is completely discharged, and there will be an even larger current through the diode and is given by:
$$i_d(t) = i_c(t)\cong C\left[\frac{d}{dt}V_P \sin{\omega t}\right] = \omega C V_P \cos{\omega t}$$
Since this initial **surge current** occurs at $t=0^+$:
>[!note]
>$$I_{SC}=\omega CV_P$$

>In most practical circuits, the surge current will be large, but cannot actually reach the values predicted by the equation above.

## Peak-inverse-voltage (PIV) rating
**PIV**: The breakdown voltage can occur when $V_r$ is very small.
When the diode is off, the reverse bias across the diode is equal to $V_{dc} - v_I$, when $v_I$ reaches its negative peak of $-V_P$. 
>[!note]
The diode must be able to withstand at least
$$\mathrm{PIV} \geq V_{dc} - v_I^{min} = V_P - V_{on} - (-V_P)=2V_P - V_{on} \cong 2V_P$$

## Diode power dissipation
The average power dissipation in the diode is defined by:
$$P_D= \frac{1}{T}\int_0^Tv_D(t)i_D(t)dt$$
Assume that the voltage across the diode is approximately constant at $v_D(t)  = V_{on}$ combined with the expression of $I_{dc}$:
$$P_D = \frac{1}{T}\int_0^TV_{on}i_D(t)dt =\frac{V_{on}}{T}\int_{T-\triangle T}^T i_D(t)dt = V_{on}\frac{I_P}{2}\frac{\triangle T}{T}$$
Thus 
$$P_D=V_{on}I_{dc}$$
Diode has a small internal series resistance $R_s$, and the average power dissipation in this resistance can be calculated using
$$P_D=\frac{1}{T}\int_0^T i_D^2(t)R_sdt$$

## Half-wave rectifier with negative output voltage
<center><em>Half-wave rectifier circuits that develop negative output voltages</em></center>

| First way to draw | Second way to draw |
| ---------------- | ------------------ |
| ![[Pasted image 20230310150057.png]]                 |                ![[Pasted image 20230310150116.png]]    |

These two cycle are equivalent.
The dc output voltage is
$$V_{dc} = -(V_P-V_{on})$$