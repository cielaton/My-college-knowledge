We already obtain the simplified circuit for the previous example:

![[Pasted image 20230422203537.png]]

Replace the transistor by its small-signal model:

![[Pasted image 20230422203657.png]]

<center><em>Final equivalent circuit for ac analysis of the ommon-emitter amplifier</em></center>

![[Pasted image 20230422204510.png]]

Where
$$R_L = r_o || R_C || R_3$$
>The Emitter is *common* from to both input and output signals → Common-Emitter (C-E) amplifier

The voltage gain can be written as:

$$A_v^{CE} = \frac{v_o}{v_i} = \frac{v_o}{v_b}\frac{v_b}{v_i} = A_{vt}^{CE}\frac{v_b}{v_i}$$
Where
$$A_{vt}^{CE} = \frac{v_o}{v_b} = -g_mR_L$$
**Terminal gain** ($A_{vt}^{CE}$): The gain from the base terminal B to the collector terminal C
