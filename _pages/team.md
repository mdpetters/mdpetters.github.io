---
layout: page
permalink: /team/
title: team
description: Undergraduate Students, Graduate Students, and Postdocs Contributing to the Group.
nav: true
---

### Current Team Members

<div class="projects grid">

  {% assign sorted_teamss = site.team | sort: "importance" %}

  {% for team in sorted_teamss %}
  <div class="grid-item">
    {% if team.redirect %}
    <a href="{{ team.redirect }}" target="_blank">
    {% else %}
    <a href="{{ team.url | relative_url }}">
    {% endif %}
      <div class="card hoverable">
        {% if team.img %}
        <img src="{{ team.img | relative_url }}" alt="project thumbnail">
        {% endif %}
        <div class="card-body">
          <h2 class="card-title text">{{ team.title }}</h2>
          <p class="card-text">{{ team.description }}</p>
          <div class="row ml-1 mr-1 p-0">
            {% if team.github %}
            <div class="github-icon">
              <div class="icon" data-toggle="tooltip" title="Code Repository">
                <a href="{{ team.github }}" target="_blank"><i class="fab fa-github gh-icon"></i></a>
              </div>
              {% if project.github_stars %}
              <span class="stars" data-toggle="tooltip" title="GitHub Stars">
                <i class="fas fa-star"></i>
                <span id="{{ team.github_stars }}-stars"></span>
              </span>
              {% endif %}
            </div>
            {% endif %}
          </div>
        </div>
      </div>
    </a>
  </div>
{% endfor %}

</div>

<br> 

### Group Alumni
- [Shweta Yadav](https://scholar.google.com/citations?user=PJjLMpQAAAAJ&hl=en) (Postdoctoral Fellow)
- [Ankit Tandon](https://scholar.google.com/citations?user=sMMJZmEAAAAJ&hl=en) (Postdoctoral Fellow)
- [Timothy Wright](https://scholar.google.com/citations?user=T4dPYAEAAAAJ&hl=en) (Postdoctoral Fellow)
- [Juan James-Correa](https://orcid.org/0000-0002-5665-3575) (Postdoctoral Fellow)
- [Nicholas Rothfuss](https://orcid.org/0000-0002-1495-1902) (PhD Student)
- [Kyle Dawson](https://scholar.google.com/citations?user=FO_knmIAAAAJ&hl=en) (PhD Student)
- [Timothy Wright](https://scholar.google.com/citations?user=T4dPYAEAAAAJ&hl=en) (PhD Student)
- Alyssa Zimmerman (MS Student)
- [Taylor Royalty](https://scholar.google.com/citations?user=cgJwfFwAAAAJ&hl=en) (MS Student)
- Brittany Phillips (MS Student)
- Hans Taylor (MS Student)
- Sara Christensen (MS Student)
- Sarah Suda (MS Student)
- Aleksandra Marsh (Visiting Student)
- [Khoi Nguyen](https://scholar.google.com/citations?user=mwnOdRsAAAAJ&hl=en) (Visiting Student)

### Undergraduate Alumni
- Emily Morris
- Travis Morton
- [John Hader](https://scholar.google.com/citations?user=kC5e0l4AAAAJ&hl=en)
- Danielle Dillane
- Hanahmariam Tekleab
- Mark Wu
- Mary Hester
- Tyler Rohrbach
- Rachel Wilkinson
- Margaret Scott
- Kylie Hoffmann
- Seth Goodnight