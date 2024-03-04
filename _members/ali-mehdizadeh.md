---
name: Ali Mehdizadeh
image: images/headshots/ali.jpg
role: grad
group: alumni
aliases:
  - Ali Mehdizadeh Rahimi
description: PhD Graduate
links:
    email: mehdizadehrahimi.a@husky.neu.edu
    linkedin: alimehdizadehrahimi
---

<br>
**Education**
<br>
- Ph.D. in Mechanical Engineering (2020), Northeastern University
- M.Sc. in Mechanical Engineering - Bioengineering and Biomedical Engineering (2012), Amirkabir University of Technology - Tehran Polytechnic
- B.E. in Mechanical Engineering (2009), Sharif University of Technology
<br>
<hr>

Ali’s a PhD graduate in Mechanical Engineering. His main research area for his thesis was molecular electrostatics, focusing on the application of the SLIC (Solvation-Layer Interface Condition) electrostatics model to the bilayer membrane-nano particle interaction problem. He also worked on the simulation of flow response of hair beds in Couette flow using OpenFOAM.

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