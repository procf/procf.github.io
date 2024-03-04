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

## Publications

{% assign author_name = page.name %}

{% if author_name == "Elahe Javadi" %}
  {{ author_name }}
{% endif %}

{% comment %}
{% assign author_citations = site.data.citations | where_exp: "item", "item.authors != nil and item.authors contains author_name" %}

{% for citation in author_citations %}
  <p><strong>{{ citation.title }}</strong></p>
  <p><em>{{ citation.authors | join: ", " }}</em></p>
  <p>{{ citation.publisher }}, {{ citation.date | date: "%B %d, %Y" }}</p>
  <p>Tags: {{ citation.tags | join: ", " }}</p>
  <p><a href="{{ citation.link }}" target="_blank">Read more</a></p>
  <img src="{{ citation.image }}" alt="{{ citation.publisher }}" style="max-width: 200px; max-height: 200px;">
  <hr>
{% endfor %}
{% endcomment %}