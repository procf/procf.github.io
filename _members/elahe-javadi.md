---
name: Elahe Javadi
image: images/headshots/elahe.jpg
description: PhD Graduate
role: grad
group: alumni
links:
  email: elahe.jvd@gmail.com
  google-scholar: vLviwfgAAAAJ&hl
---

<br>
**Education**
<br>
- Ph.D. in Mechanical Engineering (2022), Northeastern University
- M.Sc. in Aerospace Engineering (2016), Sharif University of Technology
- B.Sc. in Aerospace Engineering (2014), K. N. Toosi University of Technology
<br>
<hr>

As a seasoned Modeling and Simulation Consultant with Dassault Systemes, my expertise is rooted in a strong academic foundation, underscored by a PhD from Northeastern University. My doctoral research delved into blood rheology and its applications in medical simulations, laying the groundwork for my current role where I leverage advanced simulation to solve complex problems and drive efficiency for clients. This synergy of academic excellence and practical consultancy defines my professional journey and underscores the robust analytical skills I offer in the field.

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