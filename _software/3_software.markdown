---
layout: page
title: Notebooks
description: Applets for students in an inquiry-based course in Atmospheric Physics.
img: /assets/img/notebook.png
years: [Interactive Worksheets for Teaching Atmospheric Aerosols and Cloud Physics]
importance: 3
---

#### Learning is Hard
Learning new material takes a lot of mental effort. Textbooks deliver static visualizations.
On the other hand, interactive materials allow learners to playfully engage with complicated
models. Interactive notebooks are becoming a popular tool to deliver interactive material. 
However, content creation takes time and reliable delivery has some challenges. This
project includes some examples for Atmospheric Physics instruction.  In addition to focusing 
on discipline-based learning objectives, the worksheets emphasize interacting with real-world 
data and practicing graph comprehension.

#### Example
Students log onto a JupyterHub cloud server and load a noteboook. Jupyter notebooks can 
execute code from languages such as Julia, Python, R and many more. Output of the program 
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

#### I Want To Learn More

Check out the BAMS paper, read <a href = "https://mdpetters.github.io/Atmospheric-Physics-Notebooks/v2008/" target="_blank" rel="noopener noreferrer">  the documentation </a> or the <a href ="https://github.com/mdpetters/Atmospheric-Physics-Notebooks" target="_blank" rel="noopener noreferrer"> source code</a>. 

<div class="publications">

{% for y in page.years %}
  {% bibliography -f papers -q @*[title={{y}}]* %}
{% endfor %}

</div>
