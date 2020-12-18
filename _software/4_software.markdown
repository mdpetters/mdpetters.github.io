---
layout: page
title: Kappa
description: Code related to the hygroscopicity parameter kappa.
img: /assets/img/kafga1.png
set: ["A single parameter representation of hygroscopic growth and cloud condensation nucleus activity","A single parameter representation of hygroscopic growth and cloud condensation nucleus activity – Part 2: Including solubility","A single parameter representation of hygroscopic growth and cloud condensation nucleus activity &ndash; Part 3: Including surfactant partitioning","Prediction of cloud condensation nuclei activity for organic compounds using functional group contribution methods"]

importance: 5
---

#### Problem Description
Water condenses on particles that are suspended in the atmosphere. Once the size of these
particles reaches a critical threshold, the particles growth rapidly into cloud droplets. 
These particles are called cloud condensation nuclei (CCN). The ability of particles to 
serve as CCN depends on their size and their chemical composition. [Köhler theory](https://en.wikipedia.org/wiki/K%C3%B6hler_theory)
describes this process.

The hygroscopicity parameter kappa is one way to paramaterize a particle's ability to serve
as CCN in the atmosphere. Detailes are given in the cited references below. Several GitHub 
repositories are available with code related to calculating kappa. **The headers
are links to individual repositories.**

#### [kappa](https://github.com/mdpetters/kappa)

This repository contains code in various languages to relate the hygroscopicity parameter 
kappa with hygroscopic growth factor or critical supersaturation. 

- ```Excel/``` The spreadsheet is self explanatory and includes a number of forward and inverse calculations related to Petters and Kreidenweis (2007,2008).
- ```txt/``` The text file kappalines.txt can by used to overlay lines of constant kappa onto a critical supersaturation/dry diameter plot.
- ```IDL_GDL``` The IDL (Interactive Data Language) or GDL directory includes code to replicate Petters and Kreidenweis (2007,2008, and 2013)
- ```Python``` The Python directory includes code to replicate Petters and Kreidenweis (2008)
- ```MATLAB_OCTAVE``` The MATLAB/Octave directory includes code to replicate Petters and Kreidenweis (2008) and Petters and Kreidenweis (2013)


#### [Database with kappa values](https://mdpetters.github.io/kappa/index.html)

<img src="/assets/img/SampleDB.png" alt="drawing" width="750"/>

The repository contains a summary of experimentally derived values for kappa from hygroscopic 
growth and cloud droplet activation data. The database includes relevant information regarding 
molecular structure, experimental methods, and original data sources.



#### [KAppa Functional Group Analysis (KAFGA)](https://github.com/mdpetters/KAFGA)

Organic particles suspended in air serve as nucleation seeds for droplets in atmospheric clouds. Over time their chemical composition changes towards more functionalized compounds. This work presents a model that can predict an organic compounds' ability promote the nucleation of cloud drops from its functional group composition. Hydroxyl, carboxyl, aldehyde, hydroperoxide, carbonyl, and ether moieties promote droplet nucleation. Methylene and nitrate moieties inhibit droplet nucleation.

KAFGA is MATLAB/GNU Octave code to predict the hygroscopicity parameter kappa for organic compounds from functional group composition.

#### References
<div class="publications">
{% for y in page.set %}
  {% bibliography -f papers -q @*[title={{y}}]* %}
{% endfor %}
</div>
