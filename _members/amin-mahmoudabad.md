---
name: Amin Mahmoudabad
image: images/headshots/amin.jpg
description: PhD Graduate
role: grad
group: alumni
aliases:
  - Mohammadamin Mahmoudabadbozchelou
  - Amin Mahmoudabadbozchelou
links:
  email: mahmoudabadbozch.m@northeastern.edu
  google-scholar: C57oydEAAAAJ&hl
---

<br>
**Education**
<br>
- Ph.D. in Mechanical Engineering (2022), Northeastern University
- M.Eng. in Mechanical Engineering (2019), Rutgers University
- M.Sc. in Mechanical Engineering (2018), Sharif University of Technology
- B.Sc. in Mechanical Engineering (2016), K. N. Toosi University of Technology
<br>
<hr>

Dr. Mohammadamin Mahmoudabadbozchelou holds a Ph.D. in applied machine learning with a strong foundation in solving intricate mechanical engineering problems through innovative data-driven methodologies. His academic journey was dedicated to pioneering research that harnessed machine learning algorithms to address various problems in mechanical engineering.

During his doctoral studies, Mohammadamin specialized in leveraging physics-based machine learning techniques to tackle complex rheological problems. His impactful research culminated in the publication of seven papers in prestigious journals, establishing him as a trailblazer in the development of rheology-informed Neural Networks.

Having graduated in December 2022, Mohammadamin now serves as a Senior Engineer in software and machine learning at Aspen Technology. In this role, he focuses on the advancement of machine learning models that adhere to mechanical and chemical constraints within Aspen's software, contributing significantly to the evolution of cutting-edge technologies in this domain.

{% assign author_name = page.name %}
{% assign author_aliases = page.aliases | default: empty_array %}
{% assign author_aliases = author_aliases | push: author_name %}
{% assign author_publications = "" %}

{% for citation in site.data.citations %}
  {% assign authors = citation.authors %}
  {% if authors contains author_name or authors contains author_aliases %}
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
            {% if author == author_name or author_aliases contains author %}
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


