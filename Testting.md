![[Pasted image 20230426153610.png]]

Please find $i_1(t)$ and $i_2(t)$ of the above circuit using Laplace transform circuit analysis



We can use Kirchhoff's laws to write the following equations for the circuit:

$$\begin{aligned} &sL_1 I_1(s) + R_1 I_1(s) + L_2 (sI_1(s) - sI_2(s)) = V(s) \\ &L_2 (sI_2(s) - sI_1(s)) + R_2 I_2(s) = 0 \end{aligned}$$

where $V(s)$ is the Laplace transform of the input voltage $v(t)$.

Solving for $I_1(s)$ and $I_2(s)$, we get:

$$I_1(s) &= \frac{V(s)}{(sL_1 + R_1)(s^2 L_2 + R_2 L_2 + s(R_1+R_2)} \ I_2(s) &= \frac{sV(s)L_2}{(s^2 L^2 + R_2 L^2 + s(R^+R^+)(sL^+_R^-)}$$

Taking the inverse Laplace transform of these expressions, we get:

$$\begin{aligned} i_1(t) &= \mathcal{L}^{-1}\left\{\frac{V(s)}{(sL^+_R+R^+_R)(s^2 L^-_{L^{}} + R^-_{L^{}} L^-_{L^{}} + s(R^+_R+R^-_{L^{}}))}\right\}(t) \\ i_{  22}(t)&=\mathcal{L}^{-1}\left\{\frac{sV_(s)L^-_{C^{}}}{(s^3 L^\- _C L^+_R+ s^2(L^\- _C R^+_R + L^\- _C R^-_{L^{}} + L^+_R R^-_{L^{}})+ s(R^+_R R^-_{L^{}}))}\right\}(t) \end{aligned}$$

where $\mathcal{L}^{-1}$ denotes the inverse Laplace transform.