---
layout: page
title: Drop Freeze Detection
description: Automated detection of droplets freezing.
img: /assets/img/ice.png
set: ["Characterization of Ice-Nucleating Particles Over Northern India","A comprehensive characterization of ice nucleation by three different types of cellulose particles immersed in water", "The Fifth International Workshop on Ice Nucleation phase 2 (FIN-02): laboratory intercomparison of ice nucleation measurements", "Revisiting ice nucleation from precipitation samples","High Relative Humidity as a Trigger for Widespread Release of Ice Nuclei","Contribution of pollen to atmospheric ice nuclei concentrations", "Minimal cooling rate dependence of ice nuclei activity in the immersion mode","The role of time in heterogeneous freezing nucleation"]
importance: 6
---

#### Problem Description
In the absence of a nucleus, water does not freeze at temperatures below zero Celsius. Substances
that cause supercooled water to freeze play a central role in cloud physics. Our group 
measures the concentration of freezing nuclei in the atmosphere using a cold-stage technique.
The experiment is performed by placing droplets on surface which is observed by a camera.

<img src="/assets/img/dropsize.png" alt="drawing" width="780"/>

**Figure.** Drop volumes used by the NC State CS. (a) A section of the field of view for an 
experiment using ~0.25 nL immersed in oil. The small images to the right depict enlarged 
examples of individual drops prior to freezing (left column) and after freezing (right column), 
(b) same as (a) but for ~150 nL immerserd in oil, (c) 1 muL placed on four hydrophobic 
glass slides. Drops are placed using an electronic pipette. Images in (a) and (b) are 
obtained using a stereo microscope, the images in (c) with a macro lens.

The surface is cooled at a constant rate. Time lapse photography is used to record images 
of the drops every few s. When the droplets freeze, they turn opaque. The change in brightness 
is detected using an automated image detection code. 

#### Software

The code in this repository is used for analysis for 1 ul volume drops shown in the right
part of the figure above. Each image is compared to the next colder image with a darkening of the 
drop indicating a freeze event. Detection occurs in three steps. First, drop locations are 
identified in the first image in the sequence using a Hough transform for circles. After 
the location of the drops is identified, each drop location is compared to the same location 
in the next image by taking a subset of the image including the drop and then 
performing the following steps: convert the two tiles to grayscale equivalents, subtract the 
two tiles from each other, convert the grayscale result to a binary image based on a 
threshold value, and finally perform cleanup. 

Check out the [source code](https://github.com/mdpetters/Drop-Freezing-Detection) for more
information.

#### Selected References Using the NC State Cold-Stage

<div class="publications">
{% for y in page.set %}
  {% bibliography -f papers -q @*[title={{y}}]* %}
{% endfor %}
</div>
