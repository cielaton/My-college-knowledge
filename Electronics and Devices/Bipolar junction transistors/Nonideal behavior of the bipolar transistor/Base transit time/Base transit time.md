To turn on the bipolar transistor, minority-carrier charge must be introduced into the base to establish the carrier gradient.
The **forward transit time** $\tau_F$ represents the time constant associated with storing the required charge Q in the base region and is defined by
>[!note]
>$$\tau_F = \frac{Q}{I_T}$$

The following figures depict the situation in the neutral base region of an *npn* transistor operating in the foward-active region with $v_{BE} > 0$ and $v_{BC} = 0$.

<center><em>Excess minority charge Q stored in the bipolar base region</em></center>

![[Pasted image 20230331171711.png]]

<center><em>Stored charge Q changes as $v_{BE}$ changes</em></center>

![[Pasted image 20230331172020.png]]

The area under the triangle represents the excess minority charge Q that must be stored in the base to support the diffusion current.

>[!note]
>$$Q = qA[n(0) - n_{bo}] \frac{W_B}{2} = qAn_{bo}\left[exp\left(\frac{v_{BE}}{V_T}\right)-1\right]\frac{W_B}{2}$$

For the conditions in the first figure:

>[!note]
>$$i_T = \frac{qAD_n}{W_B}n_{bo}\left[exp\left(\frac{v_{BE}}{V_T}\right) - 1\right]$$

Doing substitution, we obtain the transit time for *npn*:

>[!note]
>$$\tau_F = \frac{W_B^2}{2D_n} = \frac{W_B^2}{2V_T\mu_n} $$
> Same with *pnp* transistor, just replace $D_p$ and $\mu_p$

The operating frequency $f$ of the transistor

>[!note]
>$$f \leq \frac{1}{2\pi\tau_F}$$