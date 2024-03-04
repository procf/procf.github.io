---
name: Donya Dabiri
image: images/headshots/donya.jpg
description: PhD Student
role: grad
group: current
aliases:
links:
  email: saadat.m@northeastern.edu
  twitter: Villeneuvesci
  github: villesci
  google-scholar: BJlkwh0AAAAJ&hl
---

Andrew (Drew) Villeneuve (he/him/his) is a global change marine ecologist interested in working with data across scales of biological organization to better understand the effects of climate change on marine ecosystems and the people that depend on them. He specifically seeks to combine empirical data of organismal physiology and distribution, environmental and extreme event data, and fisheries data into models of ecosystem dynamics under climate change. 

Andrew earned his bachelor’s in Biology from Bowdoin College in 2016 and his master’s in Environmental Conservation from the University of Massachusetts Amherst in 2021. At UMass Amherst, he worked in the Marine Global Change Ecology lab with Dr. Brian Cheng understanding the role of local adaptation in driving intraspecific trait variation and climate sensitivity of the marine predatory gastropod Urosalpinx cinerea. He was a 2021 Knauss Marine Policy Fellow with NOAA Fisheries, where he supported efforts to incorporate traditional ecological knowledge from Inuit groups into an international agreement to prevent unregulated fishing in the Central Arctic Ocean, and developed communication materials about NOAA Fisheries surveys for the public and Congress. 

When not working on his research, Andrew likes to spend his time outdoors hiking, biking, kayaking, diving, getting lost, and [taking nature walks](https://www.inaturalist.org/people/1160923). 

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