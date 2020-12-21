---
layout: page
title: MEA 412
description: " "
img: /assets/img/Physics.png
years: [Interactive Worksheets for Teaching Atmospheric Aerosols and Cloud Physics]
importance: 2
---


#### **Atmospheric Physics**

The course includes physical and analytical descriptions of atmospheric aerosols, 
clouds/fogs, and precipitation processes, including size distribution and sources of 
atmospheric aerosols, cloud droplets, rain droplets and ice crystals. 

#### MEA 412 Course Level Learning Outcomes 

- recognize the various sources of atmospheric aerosols
- explain and quantify the critical processes (droplet formation, droplet growth, precipitation formation)
of the cloud cycle
- use the theory to infer how changes in cloud condensation nuclei and ice nuclei change cloud micro-
physical properties
- explain how aerosols and clouds interact with solar and terrestrial radiation
- compute and diagram radiative uxes of the atmosphere in radiative equilibrium
- write computer programs in MATLAB that solve the key equations to compute various aerosol or cloud
properties and radiation uxes
- combine the theory and computer programs to formulate estimates of the impact of aerosols on climate

#### Learning Style
This course employs and inquiry-style approach to learning. Students use interactive applets 
to interact with the material. Students log onto a JupyterHub cloud server and load a 
noteboook. Jupyter notebooks can execute code from languages such as Julia, Python, R and many more. Output of the program 
can be placed in a cell and can consist of text or graphics. Using reactive programming one 
can create content that allows users to interact with the program through intuitive web 
elements such as range-sliders, toggle-buttons, switches, and input boxes. 

The figure below shows an example. The applet simulates the supersaturation profile as 
function of height during the early stage of cloud formation using an adiabatic parcel 
model. A parcel model solves the supersaturation balance equation in an updraft for a 
given aerosol. The applet takes inputs of updraft velocity and aerosol number concentration. 
Other inputs needed to initialize a parcel model simulation, the aerosol size distribution, 
aerosol hygroscopicity parameter, thermodynamic state, and accommodation coefficient are assumed. 
This information is irrelevant for the exercise and hidden to the students. 

<img src="/assets/img/parcel.png" alt="drawing" width="750"/>

**Figure.** Applet showing the supersaturation profile (left) and cloud droplet number 
concentration (CDNC, right) simulated from an adiabatic parcel model. The range-sliders can 
be used to vary updraft velocity and aerosol number concentration. The model lines adjust
near instantaneously. 

#### Further Details

Check out the BAMS paper, read <a href = "https://mdpetters.github.io/Atmospheric-Physics-Notebooks/v2008/" target="_blank" rel="noopener noreferrer">  the documentation </a> or the <a href ="https://github.com/mdpetters/Atmospheric-Physics-Notebooks" target="_blank" rel="noopener noreferrer"> source code</a>. 

<div class="publications">

{% for y in page.years %}
  {% bibliography -f papers -q @*[title={{y}}]* %}
{% endfor %}

</div>



