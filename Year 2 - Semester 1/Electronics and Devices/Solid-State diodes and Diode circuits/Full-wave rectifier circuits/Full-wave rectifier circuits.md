Full-wave rectifier circuit cut the capacitor **discharge time** in **half** and offer the advantage of requiring only **one-half the filter capacitance** to achieve a given ripple voltage.
<center><em>Full-wave rectifier circuit using two diodes and a center-tapped transformer.  This produces a positive output voltage.</em></center>


![[Pasted image 20230310150918.png]]


- For $v_I>0$, $D_1$ will be functioning as a half-wave rectifiers, $D_2$ will be off.
![[Pasted image 20230310152917.png]]

- For $v_I<0$, $D_1$ will be off, and $D_2$ will be functioning.
![[Pasted image 20230310152940.png]]

<center><em>Voltage waveforms for the full-wave rectifier</em></center>

![[Pasted image 20230310153339.png]]


## Full-wave rectifier equations:
The discharge interval is **T/2** rather than T.
>[!note]
$$V_{dc} = V_P - V_{on}$$
$$V_r=\frac{(V_P-V_{on})}{R}\frac{T}{2C}$$
$$\triangle T=\frac{1}{T}\sqrt{\frac{T}{RC}\frac{(V_P-V_{on})}{V_P}}=\frac{1}{\omega}\sqrt{\frac{2V_r}{V_P}}$$
$$\theta_c = \omega\triangle T = \sqrt{\frac{2V_r}{V_P}}$$
$$I_P=I_{dc}\frac{T}{\triangle T}$$
$$PIV=2V_P$$

## Full-wave rectifier with negative output voltage
You can obtain this by reversing the diode polarity:

![[Pasted image 20230310154344.png]]
