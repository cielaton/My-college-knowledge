The excess base current that drives the transistor into saturation causes additional charge storage in the base region of the transistor.
→ This charge must be removed before the transistor can *turn off*
→ An extra delay time (**storage time $t_S$**), appears in the switching characteristic.

<center><em>Bipolar inverter with current source drive</em></center>

![[Pasted image 20230413181826.png]]

<center><em>Switching behavior for the BJT inverter for three values of reverse base current</em></center>

![[Pasted image 20230413182203.png]]

The storage time $t_S$ can be calculated by:
$$t_S = \tau_S \; ln \left(\frac{I_{BF - I_{BR}}}{\frac{i_{CMAX}}{\beta_F} - I_{BR}}\right) \hspace{20pt} \text{with} \hspace{20pt} \tau_S = \frac{\alpha_F(\tau_F + \alpha_R\tau_R)}{1 - \alpha_F\alpha_R}$$
$\tau_S$ is called the **storage time constant**