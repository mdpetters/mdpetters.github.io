---
layout: page
permalink: /teaching/
title: teaching
description: Courses taught.
nav: true
---

### Current Rotation

I currently teach MEA 217 (fall semester), MEA 412 (spring semester), and MEA 703 (spring semester).

<div class="projects grid">

  {% assign sorted_teachings = site.teaching1 | sort: "importance" %}

  {% for teaching in sorted_teachings %}
  <div class="grid-item">
    {% if teaching.redirect %}
    <a href="{{ teaching.redirect }}" target="_blank">
    {% else %}
    <a href="{{ teaching.url | relative_url }}">
    {% endif %}
      <div class="card hoverable">
        {% if teaching.img %}
        <img src="{{ teaching.img | relative_url }}" alt="project thumbnail">
        {% endif %}
        <div class="card-body">
          <h2 class="card-title text-lowercase">{{ teaching.title }}</h2>
          <p class="card-text">{{ teaching.description }}</p>
          <div class="row ml-1 mr-1 p-0">
            {% if teaching.github %}
            <div class="github-icon">
              <div class="icon" data-toggle="tooltip" title="Code Repository">
                <a href="{{ teaching.github }}" target="_blank"><i class="fab fa-github gh-icon"></i></a>
              </div>
              {% if project.github_stars %}
              <span class="stars" data-toggle="tooltip" title="GitHub Stars">
                <i class="fas fa-star"></i>
                <span id="{{ teaching.github_stars }}-stars"></span>
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

### Previously Taught Classes

These are courses in the Atmospheric Science major I taught in previous years. 

<div class="projects grid">

  {% assign sorted_teachings = site.teaching2 | sort: "importance" %}

  {% for teaching in sorted_teachings %}
  <div class="grid-item">
    {% if teaching.redirect %}
    <a href="{{ teaching.redirect }}" target="_blank">
    {% else %}
    <a href="{{ teaching.url | relative_url }}">
    {% endif %}
      <div class="card hoverable">
        {% if teaching.img %}
        <img src="{{ teaching.img | relative_url }}" alt="project thumbnail">
        {% endif %}
        <div class="card-body">
          <h2 class="card-title text-lowercase">{{ teaching.title }}</h2>
          <p class="card-text">{{ teaching.description }}</p>
          <div class="row ml-1 mr-1 p-0">
            {% if teaching.github %}
            <div class="github-icon">
              <div class="icon" data-toggle="tooltip" title="Code Repository">
                <a href="{{ teaching.github }}" target="_blank"><i class="fab fa-github gh-icon"></i></a>
              </div>
              {% if project.github_stars %}
              <span class="stars" data-toggle="tooltip" title="GitHub Stars">
                <i class="fas fa-star"></i>
                <span id="{{ teaching.github_stars }}-stars"></span>
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

### Other Classes

These are one-time offerings I taught in the more distant past, including classes taught
at previous institutions.

- MEA 601/801: Graduate Seminar (NC State, 2016)
- MEA 493: Measurements and Data Analysis (NC State, 2010)
- ATS 620: Thermodynamics and Cloud Physics (Colorado State University, 2006)
- ATSC5320:  Ocean Environment (University of Wyoming, 2003)