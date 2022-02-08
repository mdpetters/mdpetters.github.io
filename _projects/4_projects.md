---
layout: page
title: " "
description: T, RH, and composition dependence of SOA viscosity
img: /assets/img/doe.png
set: ["Open-hardware design and characterization of an electrostatic aerosol precipitator",
"Toward closure between predicted and observed particle viscosity over a wide range of temperatures and relative humidity", "Predicting the influence of particle size on the glass transition temperature and viscosity of secondary organic material", "Characterization of a dimer preparation method for nanoscale organic aerosol","Volatility and Viscosity Are Correlated in Terpene Secondary Organic Aerosol Formed in a Flow Reactor", "A language to simplify computation of differential mobility analyzer response functions"]
importance: 4

---

#### **Temperature, humidity, and composition dependence of secondary organic aerosol viscosity.**

- PIs (NC State): Markus Petters, Paul Ziemann (CU, Lead), Paul DeMott (CSU)
- Source: Department of Energy
- Years: 2017 -- 2022
- Graduate Students: Sabin Kasparoglu, Nicholas Rothfuss

The groups of Ziemann (CU Boulder), Petters (NC State University), and DeMott (Colorado State University) 
are funded by the DOE-ASR program to conduct laboratory measurements to link viscosity and ice nucleation. 
The overall objectives of that project are (1) measure the effects of molecular structure, temperature, and 
relative humidity on the viscosity of organic aerosol formed via controlled laboratory experiments, 
(2) assess the critical viscosity where semisolid SOA surfaces lose their heterogeneous 
ice nucleation properties as RH increases, and (3) develop computationally inexpensive expressions 
to demarcate regions where aerosols are liquid, semisolid, glassy, and/or ice nucleation active. 

#### Publications

<div class="publications">
{% for y in page.set %}
  {% bibliography -f papers -q @*[title={{y}}]* %}
{% endfor %}
</div>
