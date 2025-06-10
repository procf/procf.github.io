---
name: Deepak Mangal
image: images/headshots/deepak.jpg
role: postdoc
group: alumni
aliases:
  - Deepak
description: Postdoctoral Fellow
links:
  email: d.mangal@northeastern.edu
  google-scholar: AoYKLW4AAAAJ&hl
  twitter: DeepakM52648497
topics: # must be "sim" "net" "ml" or "blood"
  - sim
  - net
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
<br>
- Ph.D. (2021), University of Houston (Advisors: Dr. Jeremy C. Palmer and Dr. Jacinta C. Conrad)
- B.Tech. (2012), Indian Institute of Technology Kharagpur, India (Advisor: Dr. Sudarsan Neogi)
<br>
<hr>

**Research Interests**
<br>
Deepak Mangal is a postdoctoral research associate with a broad research interest in the transport in porous media, rheology of colloidal systems, and scientific machine learning.
<br>
His research at the group focused on:
1. Investigating the structural underpinnings of various rheological phenomena in colloidal systems using simulation and network science tools.
2. Utilizing deep learning frameworks such as PINN and DeepONet to tackle complex constitutive equations.
3. Investigating the effect of hydrodynamic interactions on dispersion of finite-sized particles through fibrous media
<br>

{% assign author_name = page.name %}
{% assign author_publications = site.data.citations | where: "authors", author_name | sort: "date" | reverse %}

{% if author_publications.size > 0 %}
  <hr>
  <div class="publications">
    <p><strong>Publications</strong></p>
    {% for citation in author_publications %}
      <div class="publication">
        <p style="margin: 0;"><a href="{{ citation.link }}" style="text-decoration: none;">{{ citation.title }}</a></p>
        <p style="margin: 0;">
          {% assign author_list = citation.authors %}
          {% for author in author_list %}
            {% if author == author_name %}
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
