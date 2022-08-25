---
layout: page
title: Sabin Kasparoglu
description: " "
img: /assets/img/Sabin.jpg
set: ["Experimental Determination of the Relationship Between Organic Aerosol Viscosity and Ice Nucleation at Upper Free Tropospheric Conditions","Open-hardware design and characterization of an electrostatic aerosol precipitator","Toward closure between predicted and observed particle viscosity over a wide range of temperatures and relative humidity", "Predicting the influence of particle size on the glass transition temperature and viscosity of secondary organic material"]
importance: 1
---

- Graduate Student: PhD Degree Program
- Project: Temperature, humidity, and composition dependence of secondary organic aerosol viscosity
- [Website](https://meas.sciences.ncsu.edu/people/skaspar)
- [Google Scholar](https://scholar.google.com/citations?user=z63GvKAAAAAJ&hl=en)

#### Group Publications

<div class="publications">
{% for y in page.set %}
  {% bibliography -f papers -q @*[title={{y}}]* %}
{% endfor %}
</div>
