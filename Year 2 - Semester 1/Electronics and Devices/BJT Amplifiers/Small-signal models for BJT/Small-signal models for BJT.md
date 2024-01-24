<center><em>Two-port representation of the npn transistor</em></center>

![[Pasted image 20230422195022.png]]

<center><em>Hybird-pi small-signal model for the intrinsic bipolar transistor</em></center>

![[Pasted image 20230422195454.png]]

Where
**Transconductance**:
$$g_m = \frac{I_C}{V_T} \cong 40I_C$$
**Input resistance**
$$r_\pi = \frac{\beta_o}{g_m}$$
**Output resistance**
$$r_o = \frac{V_A + V_{CE}}{I_C} \cong \frac{V_A}{I_C}$$
$\beta_o$ represents the **small-signal common-emitter gain** of the BJT.

---

### Equivalent forms of the small-signal model
The voltage-controlled source can be rewritten as:
$$g_mv_{be} = g_mr_\pi i_b = \beta_o = g_m r_\pi$$

<center><em>Current-controlled current source model</em></center>

![[Pasted image 20230422202147.png]]

We see that
$$i_C = \beta_oi_b + \frac{v_{ce}}{r_o} \cong \beta_oi_b$$
Basic relationship $i_C = \beta i_b$ is useful in both DC and AC analysis when the BJT is in the forward-active region.

