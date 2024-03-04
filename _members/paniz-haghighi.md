---
name: Paniz Haghighi
image: images/headshots/paniz.jpg
description: PhD Student
role: grad
group: current
aliases:

links:
  email: haghighi.p@northeastern.edu
  twitter: panizhaghighi94
  github: PanizHaghighi
  google-scholar: LSuqU6YAAAAJ&hl
---
<br>
**Education**
<br>
- M.Sc. in Mechanical Engineering - Energy Conversion (2019), Sharif University of Technology
- B.Sc. in Mechanical Engineering (2016), Amirkabir University of Technology
<br>
<hr>

**Research Interests**
<br>
- Colloidal Gels
- Rheology
- Machine Learning
<br>

Paniz Haghighi, a Ph.D. student, is dedicated to unraveling the complexities of colloidal gels. Her research specifically explores the formation and evolution of colloidal networks during gelation and coarsening, with the purpose of optimizing gel properties. Emphasizing the crucial role of the critical percolation point in the second-order phase transition, Paniz's work contributes to advancing our understanding of these intricate processes.

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