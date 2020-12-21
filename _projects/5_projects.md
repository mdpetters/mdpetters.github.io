---
layout: page
title: " "
description: EAGER - Studying Sources of New Particle Formation
img: /assets/img/nucleation.png
set: ["https://doi.org/10.1016/j.atmosenv.2020.117835"]
importance: 5
---

#### **EAGER: Exploring the Ground-level and Elevated Sources of New Particle Formation Using Aerosol Size-and Hygroscopicity-resolved Turbulent Flux Measurement Technique.**

- PI: Nicholas Meskhidze
- Co-PI: Markus Petters
- Source: National Science Foundation
- Years: 2019 -- 2021
- Graduate Student: Alyssa Zimmerman

This EAGER project is an effort to evaluate a new method for assessing new particle formation 
events in the atmosphere. A method has been developed to distinguish between ground-based and 
elevated sources of ultrafine particles by measuring the vertical fluxes of size-resolved particles 
and their ability to absorb water. Understanding new particle formation is critical to estimating 
ground level particle concentrations and designing effective air quality control strategies in 
urban areas. Measurements will be made of vertical turbulent aerosol fluxes during at the 
Department of Energy's Southern Great Plains site in Oklahoma, where a wealth of ancillary 
data are available, including long-term statistics of the diurnal boundary layer dynamics and 
diurnal profiles of aerosol number and hygroscopicity.

#### Publications

<div class="publications">
{% for y in page.set %}
  {% bibliography -f papers -q @*[doi={{y}}]* %}
{% endfor %}
</div>

