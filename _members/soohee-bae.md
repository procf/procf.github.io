---
name: Soohee Bae
image: images/headshots/soohee.jpg
role: grad
group: alumni
description: MSc Graduate
aliases: 
links:
  email: clarabae0909@gmail.com
  github: soohee-bae
  google-scholar: VlwRTZwAAAAJ&hl
---
<br>
**Education**
<br>
- M.Sc. in Mechanical Engineering (2023), Northeastern University
- B.Sc. in Aerospace Engineering (2021), Texas A&M-College Station
- B.A. in Mathematics (2021), Texas A&M-College Station
<br>
<hr>

Soohee Bae is a alumni of the PRO-CF lab. Her project was about structural deformation of colloidal gel under Poiseuille flow. She has achieved this through dissipative particle dynamics.

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

        {% if citation.tags.size > 0 %}
          <div class="tags" style="margin: 0; padding: 0; text-align: left;">
          {%- for tag in citation.tags -%}
            <a class="tag" style="display: inline-block; margin: 0; padding: 5px 15px; border-radius: 999px; color: $black; background: #D4D4D4; text-decoration: none; overflow: hidden; text-overflow: ellipsis; white-space: nowrap; transition: background $fast;">{{- tag -}}</a>
          {%- endfor -%}
          </div>
        {% else %}
          <div class="tags" style="margin: 0; padding: 0;">
            <a class="tag" style="display: inline-block; margin: 0; padding: 5px 15px; border-radius: 999px; color: $black; background: #D4D4D4; text-decoration: none; overflow: hidden; text-overflow: ellipsis; white-space: nowrap; transition: background $fast;">Other</a>
          </div>
        {% endif %}
      </div>
      <br>
    {% endfor %}
  </div>
{% endif %}