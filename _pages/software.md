---
layout: page
title: software
permalink: /software/
description: Free software maintained by our group.
nav: true
---

<i> <b> Free software is software that gives you the user the freedom to share, study and modify it. 
We call this free software because the user is free. </b> </i>

<i> To use free software is to make a political and ethical choice asserting the right to learn,
and share what we learn with others. Free software has become the foundation of a learning 
society where we share our knowledge in a way that others can build upon and enjoy. </i> 

--- <i>[Free Software Foundation](https://www.fsf.org/about/what-is-free-software)</i> 

<br>

<div class="projects grid">

  {% assign sorted_softwares = site.software | sort: "importance" %}
  {% for software in sorted_softwares %}
  <div class="grid-item">
    {% if software.redirect %}
    <a href="{{ project.redirect }}" target="_blank">
    {% else %}
    <a href="{{ software.url | relative_url }}">
    {% endif %}
      <div class="card hoverable">
        {% if software.img %}
        <img src="{{ software.img | relative_url }}" alt="project thumbnail">
        {% endif %}
        <div class="card-body">
          <h2 class="card-title text-lowercase">{{ project.title }}</h2>
          <p class="card-text">{{ software.description }}</p>
          <div class="row ml-1 mr-1 p-0">
            {% if software.github %}
            <div class="github-icon">
              <div class="icon" data-toggle="tooltip" title="Code Repository">
                <a href="{{ software.github }}" target="_blank"><i class="fab fa-github gh-icon"></i></a>
              </div>
              {% if software.github_stars %}
              <span class="stars" data-toggle="tooltip" title="GitHub Stars">
                <i class="fas fa-star"></i>
                <span id="{{ software.github_stars }}-stars"></span>
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
