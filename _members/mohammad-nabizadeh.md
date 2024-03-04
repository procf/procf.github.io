---
name: Mohammad Nabizadeh
image: images/headshots/nabi.jpg
description: PhD Graduate
role: grad
group: alumni
aliases:
  - Nabi
links:
  email: nabizadehmashhadto.m@northeastern.edu
  google-scholar: VlwRTZwAAAAJ&hl
---

<br>
**Education**
<br>
- Ph.D. in Mechanical Engineering (2022), Northeastern University
- M.Sc. in Mechanical Engineering (2018), Koç University
- B.Sc. in Mechanical Engineering (2015), University of Tehran
<br>
<hr>

Mohammad is a PhD Graduate in Mechanical Engineering. His main research are was the computational study of the colloidal gels. In particular, he focused on the application of network science techniques in the study of meso-scale particulate matter.

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
