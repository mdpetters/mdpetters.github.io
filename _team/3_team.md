---
layout: page
title: Sundandan Mahant
description: " "
img: /assets/img/mahant.jpg
importance: 3
set: [""]
---

- Graduate Student: PhD Degree Program
- Project: Laboratory Studies Investigating the Influence of Particle Diameter on Viscosit 
- [Website](https://meas.sciences.ncsu.edu/people/smahant2/)

#### Group Publications

<div class="publications">
{% for y in page.set %}
  {% bibliography -f papers -q @*[title={{y}}]* %}
{% endfor %}
</div>


