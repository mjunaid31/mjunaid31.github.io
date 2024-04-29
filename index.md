


## Table of contents
- [abstract](#abstract)
- [Introduction](#introduction)





## abstract

Investigating galactic mean-field dynamos stems from a quest to comprehend the emergence and progression of magnetic fields within galaxies. Studying this dynamo is significant because it offers a framework to understand how galactic motions and turbulence are converted into magnetic fields. This knowledge sheds light on star formation, cosmic ray containment within the galaxy, and potentially even galactic evolution. Our research aims to elucidate the effects of vertical outflows in these systems, given their significant influence on gas and magnetic field distributions within galaxies. These outflows play a pivotal role in determining star formation rates and facilitating matter-energy transport processes.  In this study, our goal was to progressively increase $V_z$ over time, thereby leading to the quenching of the dynamo.



## Introduction

Induction equation given by Galactic mean field theory is

$$\frac{\partial \overline B_r}{\partial t} = - \frac{\overline V_r}{r} \frac{\partial}{\partial r}(r\overline B_r) -  \frac{\partial}{\partial z}(\overline V_z \overline B_r) -  \frac{\partial}{\partial z}(\alpha \overline B_{\phi}) + \eta_t \left[  \frac{\partial}{\partial r} \left( \frac{1}{r}  \frac{\partial}{\partial r}(r \overline B_r)\right) +  \frac{\partial ^2 \overline B_r}{\partial z^2} \right]$$

$$\frac{\partial \overline B_{\phi}}{\partial t} = - q\Omega \overline B_{r} -  \frac{\partial}{\partial r}(\overline V_r \overline B_{\phi}) -  \frac{\partial}{\partial z}(\overline V_z \overline B_{\phi}) +  \frac{\partial}{\partial z}(\alpha \overline B_{r}) + \eta_t \left[  \frac{\partial}{\partial r} \left( \frac{1}{r}  \frac{\partial}{\partial r}(r \overline B_{\phi})\right) +  \frac{\partial ^2 \overline B_{\phi}}{\partial z^2} \right]$$

where $\overline B_r$ and  $\overline B_{\phi}$ are the components of the magnetic field, $\overline V_r$, and $\overline V_z$ are the components of the velocity field, $\alpha$ is the dynamo alpha effect, $\Omega$ is the angular velocity of the galaxy, $q$ is the shear parameter, and $\eta_t$ is the turbulent magnetic diffusivity.

Unlke Task2 where we discarded velocity terms, here, we include terms with $\overline V_z$, to study impact of vertical outflows on the evolution of galactic magnetic fields. In particular $\overline V_z$ is increased with time to show quencing of the dynamo. Then the unitless induction equation is given by 
$$\frac{\partial B_r'}{\partial t'} = \frac{\partial}{\partial z'}(V_z'B_r') - \frac{\partial}{\partial z'}(\alpha'B_{\phi}') + \frac{\partial^2 B_r'}{\partial z'^2}$$


$$\frac{\partial B_{\phi}'}{\partial t'}=-q\Omega' B_r'+\frac{\partial }{\partial z'}(V_z' B_{\phi}')-\frac{\partial }{\partial z}(\alpha' B_r')+\frac{\partial^2 B_{\phi}'}{\partial z'^2}$$

## Computational methods


The spatial derivatives are calculated using the finite difference method. 2nd order finite difference method is given by: 
$$
f'_{i} = \frac{{-f_{i-1} + f_{i+1}}}{2\delta x}
$$

$$
f"_{i} = \frac{{f_{i-1} - 2f_i + f_{i+1}}}{\delta x^2}
$$

and for boundary meshes: 
$$
f'_{i} = \frac{-3f_i + 4f_{i+1} - f_{i+2}}{2\delta x}, \quad f"_{i} = \frac{2f_i - 5f_{i+1} + 4f_{i+2} - f_{i+3}}{\delta x^2},
$$

and

$$
f'_{i} = \frac{3f_i - 4f_{i-1} + f_{i-2}}{2\delta x}, \quad f"_{i} = \frac{2f_i - 5f_{i-1} + 4f_{i-2} - f_{i-3}}{\delta x^2}.
$$

As we are not comsidering z to be changing with time, partial differential equations are approximated to ordianry differential equations and use RK4 Time stepping for time evolution. The evolution function is:

$\frac{\partial \overline B}{\partial t} = f(\overline B)$

The algorithm is given by:

$$K1=dt(f(\overline{B}))$$
$$K2=dt(f(\overline{B}+K1/2))$$
$$K3=dt(f(\overline{B}+K2/2))$$
$$K4=dt(f(\overline{B}+K3))$$

$$\overline{B}(t+dt)=\overline{B}(t)+\frac{1}{6}(K1+2K2+3K3+K4)$$

Antisymmetric ghost zones are used to maintain boundary condition

!["A cute cat"](plot.png)

- Task 1  given [here](https://mjunaid31.github.io/Task1/)
- Task 2 is given [here](https://mjunaid31.github.io/Task2/)
- Task 3 code is given [here](https://mjunaid31.github.io/Task3/)



