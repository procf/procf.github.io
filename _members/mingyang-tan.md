---
name: Mingyang Tan
image: images/headshots/mingyang_tan.jpg
role: postdoc
group: current
aliases:
description: Postdoctoral Fellow
links:
  email: mi.tan@northeastern.edu
  google-scholar: SaJJDwUAAAAJ
  linkedin: mingyang-tan-ph-d-aa2b78a5
topics:
  - sim
  - ml
---

{% assign topics = page.topics | default: empty_array %}
{%- if topics.size > 0 -%}
  <div class="tags">
    {%- for tag in topics -%}
    {% case tag %}
      {% when "blood" %}
        {%- assign topic_tag = "Hemorheology" -%}
      {% when "sim" %}
        {%- assign topic_tag = "Colloid Systems" -%}
      {% when "net" %}
        {%- assign topic_tag = "Network Science" -%}
      {% when "ml" %}
        {%- assign topic_tag = "Machine Learning" -%}
      {% else %}
        {%- assign topic_tag = "Other" -%}
    {% endcase %}
      {%- assign topic_link = "https://rheoinformatic.com/research/" -%}
      {%- assign topic_link = topic_link | append: tag %}
      <a href="{{ topic_link }}" class="tag" data-tooltip='View research area'>{{- topic_tag -}}</a>
    {%- endfor -%}
      </div>
{%- endif -%}
<hr>

<br>

**Education**
- PhD, Oregon State University, 2018
- MS, University of Southern California, 2013
- BE, Jilin University, China, 2011
<hr>
Mingyang is a postdoctoral research associate who the group in 2024. He is interested in simulating the dynamics and physical properties of colloidal suspensions under different flow conditions and interactions among constituents. He is also interested in applying machine-learning techniques to accelerate the identification the relationship between macroscopic physical properties of soft matters and microscopic signatures of particles.
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
