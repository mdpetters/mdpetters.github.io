# The Simple Thermodenuder 

Aerosol enters the tube. For laminar flow a parabolic flow profile is established. The tube is heated heated to facilitate evaporation. 


![](../assets/schematic.png)
**Figure 1.** Schematic of processes affecting sample when entering a denuder tube. 

To understand these processes requires solving for the flow profile, the heat transfer, and mass transfer in $z$ and $r$ direction, as well as the heat and mass transfer to and from each particle as the sample flows through the system. Mass and heat transfer through the tube is given by the advection-diffusion equation:

$$
{\frac {\partial c}{\partial t}}-\nabla \cdot \left(D\nabla c\right) + \nabla \cdot (\vec{u} c) = S
$$

where  $c(x,y,z,t)$ is the concentration of a scalar, $D$  is the diffusion coefficient of the scalar in a medium material, $\vec{u}$ is the velocity field that the quantity is moving with. It is a function of time and space, and $S$ describes sources or sinks of the quantity $c$. 

For incompressible flow and constant $D$ in three dimensions and no sources ($S = 0$):

$$
{\frac {\partial c}{\partial t}} + u_x \frac{\partial c}{\partial x} + u_y \frac{\partial c}{\partial y} + u_z \frac{\partial c}{\partial z} = D \left ( \frac{\partial^2 c}{\partial x^2} + \frac{\partial^2 c}{\partial y^2} + \frac{\partial^2 c}{\partial z^2} \right ) 
$$

In cylindrical coordinates this equation is

$$
{\frac {\partial c}{\partial t}} + u_r \frac{\partial c}{\partial r} + \frac{u_\theta}{r} \frac{\partial c}{\partial \theta} + u_z \frac{\partial c}{\partial z} = D \left ( \frac{1}{r} \frac{\partial }{\partial r} \left ( r \frac{\partial c}{\partial r} \right ) + \frac{1}{r^2} \frac{\partial^2 c}{\partial \theta^2} + \frac{\partial^2 c}{\partial z^2} \right ) 
$$

where $u_r$, $u_\theta$, and $u_z$ are the velocity components in the $r$, $\theta$ and $z$ directions. For laminar flow in the pipe $u_r = 0$ and $u_\theta = 0$ components. Furthermore, we assume that advection dominates in the $z$ direction (hence no diffusion in $z$). Therefore

$$
{\frac {\partial c}{\partial t}} =  \frac{D}{r} \frac{\partial }{\partial r} \left ( r \frac{\partial c}{\partial r} \right ) - u_z(r) \frac{\partial c}{\partial z}
$$

is a good approximation for modeling mass and heat transfer through the denuder tube. Note that $u_z$ varies with the radial coordinate due to the parabolic flow profile. Of course $D$ is replaced with the thermal diffusivity $\alpha$ and $c$ with $T$ for heat transfer problems. 

# Denuder Model

A flow of air with flow rate $Q = 0.15\; L\; min^{-1}$ enters a pipe with inner diameter $D_{tube} =⅜″$. The is fully established laminar flow with a parabolic flow profile. The initial temperature of the air is $20°C$. After 5 cm distance, the wall of the tube is heated to $60°C$ for a length of 10 cm. Then the wall tube is abruptly cooled back down to $20°C$.

![](../assets/problem.png)

The coordinate system is such that $z$ is the streamwise direction (flow direction). The velocity profile for fully developed viscous laminar flow is

$$
u_z(r) = 2\bar{u} \left ( 1- \left [ \frac{r}{R} \right ] ^2 \right )
$$

where $u_z(r)$ is the variation of velocity as a function of radial coordinate $r$, $\bar{u} = \frac{Q}{\pi D_{tube}^2}$ is the average flow velocity, and $R$ is the pipe radius.

The system is assumed to be at steady-state, i.e. $\frac{\partial T}{\partial t} = 0$. The temperature field is a scalar function $T(r,z)$. The governing equation for the problem is:

$$
{\frac {\partial T}{\partial z}} =  \frac{\alpha}{r u_z(r)} \frac{\partial }{\partial r} \left ( r \frac{\partial T}{\partial r} \right ) 
$$

where $\alpha$ is the thermal diffusivity. This equation is readily solved using the methods of lines and an ODE solver.

![](../assets/solution.png)
**Figure 2.** Solution of the temperature distribution inside the denuder tube.

Figure 2 shows the evolution of the temperature distribution inside the tube. The centerline temperature increase gradually in the entrance region until it reaches the same temperature than the wall. The problem is reversed in the exit region, where the temperature gradually re-equilibrates with the colder wall.

# Evaporation

## Evaporation Equation

The evaporation rate of a particle is given by

$$
\frac{dD_p}{dt} = \frac{4DM}{R^*\rho_pD_p} \left ( \frac{p_\infty}{T_\infty} - \frac{p_a}{T_a} \right ) \phi
$$

where $D_p$ is the particle diameter, $M$ is the molecular weight, $D$ is the diffusion coefficient of the evaporating compound, $R^*$ is the universal gas constant, $\rho_p$ is the particle density, $D_p$ is the particle diameter, $p_\infty$ is the  vapor pressure far from the particle, $T_\infty$ is the temperature of the carrier gas far from the particle, $p_a$ is vapor pressure over the particle, $T_a$ is the temperature at the surface of the particle, and $\phi$ is the Fuchs correction factor. For slow evaporation $T_a \approx T_\infty$. 

### Diffusion Coefficient
The diffusion coefficient is generally unknown and must be estimated

$$
D = 0.0018583 \frac{\sqrt{T^3  \left (\frac{1}{M_1} + \frac{1}{M_2} \right) }}{p \sigma_{1,2}^2 \Omega} 
$$

where $p$ [atm] is the absolute pressure in, $T$ is the temperature, $M_1$ [g/mol] is the molecular weight of the evaporating compound, $M_2$ [g/mol] is the molecular weight of the carrier gas, $\Omega$ is a parameterization of the collision integral:

$$
\Omega = \frac{1.06036}{(T^{s})^{0.1561}} + \frac{0.193}{\exp(0.47635 T^s)} + \frac{1.03587}{\exp(1.52996  T^s)} + \frac{1.76474}{\exp(3.89411 T^s)}
$$

Furthermore, 

$$
\sigma_{1,2} = \frac{1}{2} (\sigma_1 + \sigma_2)
$$

$$
\epsilon_{1,2} = \sqrt{\epsilon_1 + \epsilon_2}
$$

$$
T^s = \frac{T}{\epsilon_{1,2}}
$$

The collision cross-section $\sigma_1 = 0.841 V_c^{1/3}$ where $V_c$ is the critical volume. The collision cross-section for air can be taken $\sigma_2 = 3.617 \r{A}$. The parameter $\epsilon_1 = 1.92 T_m$ where $T_m$ is the melting point temperature and $\epsilon_2 = 97\; K$ for air. Finally, the critical volume can be estimated from functional group composition:

$$
V_c = 40 + \sum{G_i}
$$

where $G_i$ are the group specific volumes. Eqs. (8)-(13) allow for evaluation
of $D$ as a function of temperature and total pressure.

## Vapor Pressure

The vapor pressure above the particle is elevated due to particle curvature

$$
p_a = p^{sat}_{flat}(T) \exp \left ( \frac{4\gamma M}{R^*TD_p} \right )
$$

where $p^{sat}_{flat}$ is the saturation vapor pressure over a flat surface at temperature $T$, and $\gamma$ is the solid/vapor or liquid/vapor interfacial tension. For particles $D_p > 100 nm$, $p_a \approx p^{sat}_{flat}$.

The saturation vapor pressure over a flat surface is a strong function of temperature described through the Clausius-Clapeyron equation, e.g: 

$$
\log_{10} (p^{sat}_{flat}) = -\frac{\Delta H_{vap}}{2.302R^*T} + C 
$$

where $\Delta H_{vap}$ is the enthalpy of vaporization and $C$ is a constant
that subsumes the saturation vapor pressure at a reference state. 

The saturation ratio of the gas is given by

$$
S = \frac{p_\infty}{p_a}
$$

Particles if interest are generally sufficiently non-volatile that $\frac{dD_p}{dt} \approx 0$ at room temperature. Furthermore, passage through a differential mobility analyzer to size-select particles generally removes all vapors from the gas phase. Thus in the entrance region of the denuder (0-5 cm in Figure 2), the vapor pressure $p_\infty = 0$ and $S = 0$.

The temperature is raised in in the middle section of the denuder (5-15 cm in
Figure 2) to facilitate evaporation on the time scale of the residence time (5-15 s) in the heated section. During evaporation the gas phase becomes enriched and $p_\infty > 0$. The number density of gas phase molecules is given by mass balance:

$$
n_0 = \frac{\pi(D_{p,initial}^3 - D_{p,final})^3 N N_A \rho}{6M} 
$$

where $D_{p,initial}$ is the particle diameter entering the tube, $D_{p,final}$ is the particle diameter exiting the tube (after evaporation), $N$ is the particle number concentration in the flow, $\rho$ is the density of the evaporating material, $N_A$ is Avogadro's number, and $M$ is the molecular weight. The expression assumes that the number concentration in the gas phase prior to evaporation is zero and that the distribution of vapor molecules in the tube is uniform.

The corresponding vapor pressure is given by the ideal gas law:

$$
p_\infty = n_0 k_B T
$$

where $k_B$ is Boltzmann's constant.

As $p_\infty > 0$ and $S > 0$, evaporation may be slowed proportionally,
according to Eq. (7).

# Condensation

## Walls

It is assumed that walls act as a sink for semi-volatile vapors. The time scale for heat and mass transfer is

$$
\tau_{diff} = \sqrt{\frac{L^2}{D}} 
$$

where $L$ is the distance traveled and $D$ is the diffusion coefficient (or $\alpha$ the thermal diffusivity for heat transfer problems). The maximum radial distance traversed is from the centerline of the tube to the wall, thus the time scale is

$$
\tau_{diff} = \sqrt{\frac{R^2}{D}} 
$$

Consider a vapor molecule located at the centerline. It will diffuse toward the wall at time scale $\tau_{diff}$. 

## Particle Surfaces

Condensation on particle surfaces will occur only of $p_\infty > p_a$ or $S >
1$. By definition this cannot happen in the heated section (5-15 cm in Figure
2). However, it is possible to create a supersaturation in the cooled section (15-20 cm in
Figure 2). 

If a supersaturation occurs there is competition between a molecule colliding
with the wall and a molecule colliding with a particle. The average time between of molecular collisions of gas molecules and a particle with diameter $D_p$ is given by kinetic theory and can be evaluated as

$$
\tau_{coll} = \frac{4}{n_0 \sqrt{\frac{8R^*T}{\pi M}} D_p^2}
$$

where $n_0$ is the number density of the gas-phase species, $R^*$ is the universal gas constant, $M$ is the molecular weight, $T$ is the temperature, and $D_p$ is the particle diameter. The square root expression is the average molecular velocity. 

If $\tau_{diff} << \tau_{coll}$ the vapor will condense onto the wall. Therefore, the dimensionless critical number 

$$
Y = \frac{\tau_{diff}}{\tau_{coll}} = \frac{\pi(D_{p,initial}^3 - D_{p,final})^3 N N_A \rho \sqrt{\frac{8R^*TR^2}{\pi M D}} D_{p,final}^2}{24M}
$$

can be used. For $Y < 1$, $\tau_{diff} << \tau_{coll}$ and the vapor flux will be dominated by transport to the wall.

# Performance Evaluation

Performance of the uncoated denuder obviously depends on the physico-chemical properties of the compound and the operating conditions of the denuder. The spreadsheet below provides a tool to assess performance characteristics for a specific setup. 

[Link to Spreadsheet](https://docs.google.com/spreadsheets/d/1HCO4aC8X_p6qUkF5YIm1_wUkV5SiAQ5PokcJVYpmSPM/edit?usp=sharing)

**Table 1**. Example setup of an experiment.

| $D_{initial}\; (nm)$ | $ D_{final}\; (nm)$ | $N\;(cm-3)$ | $T_{cold}\; (^\circ C)$ | $T_{warm}\; (^\circ C)$ | $D_{tube}\; (inch)$ |  
| --------------|--------------|------|----|----|-----|
| 200           |  50          | 100  | 20 | 50 | 3/8 |

Table 1 gives an example setup for an experiment. The spreadsheet is used to
evaluate the diffusion coefficient, $Y$ and the saturation ratios $S$ in the warm and cold section.

**Table 2**. Example model output for succinic acid and the conditions in Table
1

| $Y$  | $S_{cold} $ | $S_{warm}$ | $\tau_{diff}\;(s)$ |
|------|-------------|------------|---------------|
| 866  | 0.78        | 4e-3       | 1.91          |

For this example, the results show that evaporation leads to negligible vapor
buildup in the warm section ($S_{warm} = 4\times10^{-3}$). Thus vapor buildup would not slow evaporation. The characteristic time for wall loss is $\approx 2s$. This implies that some vapor is likely lost to the wall in the hot section. Upon cooling the saturation ratio increases at maximum to $S = 0.78$. Furthermore collisions of vapor occur with particles *before* they hit the wall ($Y = 866$). However, since $S < 1$, these collisions should not result in net condensation. At low accomodation coefficient, loss to the wall would be competitive with collisions with particles. 

As a general rule, the simple thermodenuder should work if (a) $N$ is
sufficiently low and (b) the temperature differential between warm and cold
section is sufficiently large. The spreadsheet can be used for quick estimates
for safe operating conditions. A detailed model tracking vapor buildup and loss
to the wall coupling the $T(z,r)$ field and evaporation model is
straightforward. 

