---
name: Josh DaRosa
image: images/headshots/josh.jpg
description: PhD Student
role: grad
group: current
aliases:
  - J. DaRosa
links:
  email: darosa.jo@northeastern.edu
  github: joshdarosa
---

<br>
**Education**
<br>
- B.Sc. in Mechanical Engineering (2022), Union College
<br>
<hr>

Joshua DaRosa is a PhD student with extensive experience within thermofluid sciences whose current research involves both computational rheology and machine learning.

Josh is currently working on:
* Studying the development of computational methods to create colloidal crystals through pressure-driven flow within converging-diverging nozzle geometry.
* Solving Fractional PDE's using Physics Informed Neural Networks
* Modelling 3-D printing of ceramic hexagonal particles using HOOMD-Blue

{% assign author_names = page.aliases | default: empty_array | push: page.name %}
{% assign author_publications = "" | split: "" %}

{% for citation in site.data.citations %}
  {% assign authors = citation.authors %}
  {% assign match_found = false %}
  
  {% for author_name in author_names %}
    {% if authors contains author_name %}
      {% assign match_found = true %}
      {% break %}
    {% endif %}
  {% endfor %}
  
  {% if match_found %}
    {% assign author_publications = author_publications | push: citation %}
  {% endif %}
{% endfor %}

{% if author_publications.size > 0 %}
  <hr>
  <div class="publications">
    <p><strong>Publications</strong></p>
    {% for citation in author_publications | sort: "date" | reverse %}
      <div class="publication">
        <p style="margin: 0;"><a href="{{ citation.link }}" style="text-decoration: none;">{{ citation.title }}</a></p>
        <p style="margin: 0;">
          {% assign author_list = citation.authors %}
          {% for author in author_list %}
            {% if author == page.name or author_names contains author %}
              <u>{{ author }}</u>{% unless forloop.last %}, {% endunless %}
            {% else %}
              {{ author }}{% unless forloop.last %}, {% endunless %}
            {% endif %}
          {% endfor %}
        </p>
        <p style="margin: 0;">{{ citation.publisher }} · {{ citation.date | date: "%Y" }}</p>
      </div>
      <br>
    {% endfor %}
  </div>
{% endif %}