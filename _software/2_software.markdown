---
layout: page
title: DMA
description: A Julia package for working with data from differential mobility analyzers.
img: /assets/img/dmalogo.png
importance: 1
---

#### Differential Mobility Analyzer
Differential mobility analyzers are widely used in aerosol science and one of the main
tools used in our group. The cylindrical DMA passes a polydisperse 
aerosol flow through an annulus gap. An electric potential is applied between the inner and outer column. 
The electric potential drags charged particles through a viscous sheath flow. 
Particles whose mobility coincide with the electric and flow field forces will be steered 
to the sample slit. All other particles exit with the excess flow.

<img src="/assets/img/overview.png" alt="drawing" width="350"/>

**Figure.** Schematic of a differential mobility analyzer. The cylindrical differential mobility analyzer 
is an annular capacitor. The column's properties are defined by the radii 
$$r_1$$, $$r_2$$, the length of the column, $$l$$. Operation conditions are defined by the
the electric potential $$v$$ applied across the annulus and the four flow rates: 
sheath flow, $$q_{sh}$$, polydisperse aerosol flow $$q_a$$, excess flow, $$q_{ex}$$, and 
monodisperse sample flow, $$q_{sa}$$. 

#### Package Description
DifferentialMobilityAnalyzers.jl bundles a set of abstractions to write concise forward and 
inverse models of experimental setups that involve differential mobility analyzers. 
Abstractions include specialized data types, operators, functions, and conventions. 
Conventions include rules for typesetting font and sub- and superscripting variables. Check out <a href ="https://mdpetters.github.io/DifferentialMobilityAnalyzers.jl/stable/" target="_blank" rel="noopener noreferrer">  the documentation </a> and the <a href ="https://github.com/mdpetters/DifferentialMobilityAnalyzers.jl" target="_blank" rel="noopener noreferrer"> source code</a>. 


#### Forward Model Example
The code below models forward transmission through a differential mobility analyzer
at a single voltage. The code example gives a flavor for language. 

{% highlight julia linos %}
using DifferentialMobilityAnalyzers

# Create a DMA config
qsa,qsh = 1.66e-5, 8.33e-5                       # Qsample [m3 s-1], Qsheath [m3 s-1]
t,p = 295.15, 1e5                                # Temperature [K], Pressure [Pa]
r₁,r₂,l = 9.37e-3,1.961e-2,0.44369               # DMA geometry [m]
Λ = DMAconfig(t,p,qsa,qsh,r₁,r₂,l,0.0,:-,6,:cylindrical)

# Create a DMA grid
z₁,z₂ = vtoz(Λ,10000), vtoz(Λ,10)    # bins, upper, lower mobility limit
δ = setupDMA(Λ, z₁, z₂, 512);

# Compute the transmission through the DMA
T(zˢ,k,Λ,δ) = δ.Ω(Λ,δ.Z,zˢ/k).*δ.Tc(k,δ.Dp).*δ.Tl(Λ,δ.Dp)
zˢ = dtoz(Λ, 100*1e-9)
𝕟ᶜⁿ = DMALognormalDistribution([[900., 40., 1.5], [500., 180., 1.4]], δ)
ℕ = map(k -> T(zˢ,k,Λ,δ)*𝕟ᶜⁿ,1:3)
𝕄 = map(k -> (ztod(Λ,1,zˢ)/ztod(Λ,k,zˢ))⋅(T(zˢ,k,Λ,δ)*𝕟ᶜⁿ),1:3)
𝕟ₜ, 𝕞ₜ = sum(ℕ), sum(𝕄)
{% endhighlight %}

<img src="/assets/img/dmas.png" alt="drawing" width="750"/>

**Figure.** Left: assumed bimodal lognormal size distribution. Middle: monodisperse mobility size 
distribution plotted against the apparent +1 mobility diameter, defined as the apparent 
setpoint diameter of the DMA. Dashed line is total number concentration. 
Right: same as middle panel but plotted versus the mobility diameter.

