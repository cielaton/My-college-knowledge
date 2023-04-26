
                                 8.4H              10H                  
                        _/       ___               ___                  
               .------o/  o------UUU-------o-------UUU------.           
               |                 L1        |       L2       |           
               |                           |                |           
              /+\                         .-.              .-.          
             (   )336V                    | |              | |          
              \-/                       R1| |42          R2| |48        
               |                          '-'              '-'          
               |                           |                |           
               |                           |                |           
               .---------------------------o----------------.           

The switch is off at t=0, calculate $i_1(t)$ and $i_2(t)$ using Laplace transform in circuit analysis.



To solve for $i_1(t)$ and $i_2(t)$ using Laplace transform, we first need to determine the equivalent circuit for the switch position at t=0. 

When the switch is off, we can simplify the circuit as follows:

                                 8.4H              10H                  
                        _/       ___               ___                  
               .------o/  o------UUU-------o-------UUU------.           
               |                 L1        |       L2       |           
               |                           |                |           
              /+\                         .-.              .-.          
             (   )336V                    | |              | |          
              \-/                          |                |
               |                          R1|                |
               |                             \              /  
               |                             R2\            /   
               .-------------------------------o----------o---

Notice that L1 and L2 are in series with each other, so they can be combined into a single inductor with a value of: 

$$L_{eq} = L_1 + L_2 = 8.4H + 10H = 18.4H$$

Using Kirchhoff's voltage law (KVL), we can write an equation for the voltage across the equivalent inductor:

$$V_{in} - R_1 i_{eq}(t) - R_2 i_{eq}(t) - L_{eq} \frac{di_{eq}(t)}{dt} = 0$$

Taking the Laplace transform of this equation yields:

$$\mathcal{L}\{V_{in}\} - R_1 \mathcal{L}\{i_{eq}(t)\} - R_2 \mathcal{L}\{i_{eq}(t)\} - L_{eq} s I_{eq}(s) = 0$$

Solving for $I_{eq}(s)$, we get: 

$$I_{eq}(s) = \frac{\mathcal{L}\{V_{in}\}}{sL_{eq} + R_1 + R_2}$$

Now we can use this expression for $I_{eq}(s)$ to find the Laplace transforms of $i_1(t)$ and $i_2(t)$. 

Using KVL around the left loop, we can write:

$$V_{in} - L_1 \frac{di_1(t)}$$
