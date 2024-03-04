---
name: Deepak Mangal
image: images/headshots/deepak.jpg
role: postdoc
group: current
aliases:
description: Postdoctoral Fellow
links:
  email: d.mangal@northeastern.edu
  google-scholar: AoYKLW4AAAAJ&hl
  twitter: DeepakM52648497
---
<br>
**Education**
<br>
- Ph.D. (2021), University of Houston (Advisors: Dr. Jeremy C. Palmer and Dr. Jacinta C. Conrad)
- B.Tech. (2012), Indian Institute of Technology Kharagpur, India (Advisor: Dr. Sudarsan Neogi)
<br>
<hr>

**Research Interests**
<br>
Deepak Mangal is a postdoctoral research associate with a broad research interest in the transport in porous media, rheology of colloidal systems, and scientific machine learning.
<br>
His research focuses on:
1. Investigating the structural underpinnings of various rheological phenomena in colloidal systems using simulation and network science tools.
2. Utilizing deep learning frameworks such as PINN and DeepONet to tackle complex constitutive equations.
3. Investigating the effect of hydrodynamic interactions on dispersion of finite-sized particles through fibrous media
<br>

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