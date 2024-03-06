---
name: Elahe Javadi
image: images/headshots/elahe.jpg
description: PhD Graduate
role: grad
group: alumni
aliases:
  - Ela
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

{%- assign custom_tags = "Hemorheology" | split: "," -%}
{%- assign tags = custom_tags | default: emptyarray -%}
{%- if tags.size > 0 or repo or repo_link -%}
  <div class="tags">
    {%- for tag in tags -%}
      <a href="https://rheoinformatic.com/research/blood/" class="tag" data-tooltip='View research area'>{{- tag -}}</a>
    {%- endfor -%}
      </div>
{%- endif -%}

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
      </div>
      <br>
    {% endfor %}
  </div>
{% endif %}