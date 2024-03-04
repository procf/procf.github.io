---
name: Linghao Du
image: images/headshots/linghao.jpg
role: grad
group: alumni
aliases:
description: MSc Graduate
links:
  email: du.li@husky.neu.edu
  linkedin: linghao-du-466299138/
---

<br>
**Education**
<br>
- M.Sc. in Information Systems (2021), Northeastern University
- M.Sc. in Mechanical Engineering (2018), Northeastern University
- B.Sc. in Mechanical Engineering (2015), Beihang University
<br>
<hr>

Linghao Du is a M.Sc. graduate with a previous background on aerospace engineering and combustion. His master's thesis employed LAMMPS and Dissipative Particle Dynamics to look at the physics and dynamics of dense suspensions relevant to flowable electrodes and energy storage technologies.

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