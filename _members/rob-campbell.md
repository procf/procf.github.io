---
name: Rob Campbell
image: images/headshots/rob.jpg
description: PhD Student
role: grad
group: current
aliases:
  - Robert Campbell
  - Robert A Campbell
  - Rob
  - R.A. Campbell
links:
  email: campbell.r@northeastern.edu
  github: rob10campbell
  linkedin: rob10campbell
  google-scholar: i8S54zYAAAAJ&hl
  orcid: 0000-0002-5561-8671
---

<br>
**Education**
<br>
- Research Assistant, 4yrs (2020), Okinawa Institute of Science and Technology (OIST)
- B.A. in Physics (2010), Skidmore College
<br>
<hr>

Rob Campbell is a PhD student interested in the microscale origins of material mechanics. Their thesis focuses on the effects of particle size and gravity in colloidal gel assembly and rheology.

Rob is the "Future Investigator" leading a 3-year FINESST grant from NASA to build open-source simulation tools that interface with exisiting data from colloid experiments on the International Space Station (ISS). Alongside this work, Rob collaborates on a project that will launch new bimodal colloid experiments to the ISS in 2024, and is developing machine learning tools to better match simulation parameters with experimental conditions.

Outside research, Rob runs Rheology Comics, a short outreach series funded by the Society of Rheology and designed to share the joys of rheological concepts with ages 10+ (available in English and 7+ other languages). You can [read Rheology Comics here!](https://rheologycomics.github.io/)

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