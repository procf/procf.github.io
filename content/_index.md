---
# Leave the homepage title empty to use the site title
title:
date: 2022-10-24
type: landing

sections:
  - block: hero
    content:
      title: |
        Physics and Rheology of Complex Fluids (PRO-CF)
      image:
        filename: welcome.jpg
      text: |
        <br>
        
        Lab intro goes here

  - block: markdown
    content:
      title: on X:
      subtitle:
      text: |
        <div style="display: flex; justify-content: center; align-items: center; height: 100vh; margin-bottom: -20px;">
          <div style="text-align: center;">
            <a class="twitter-timeline" href="https://twitter.com/PROCF_NU?ref_src=twsrc%5Etfw" data-width="400" data-height="600">Tweets by PROCF_NU</a>
            <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>
          </div>
        </div>
    design:
      columns: '1'

  - block: collection
    content:
      title: News and Events
      subtitle:
      text:
      count: 5
      filters:
        author: ''
        category: ''
        exclude_featured: false
        publication_type: ''
        tag: ''
      offset: 0
      order: desc
      page_type: post
    design:
      view: card
      columns: '1'
  
  - block: markdown
    content:
      title:
      subtitle: ''
      text:
    design:
      columns: '1'
      background:
        image: 
          filename: neu.jpg
          filters:
            brightness: 1
          parallax: false
          position: center
          size: cover
          text_color_light: true
      spacing:
        padding: ['20px', '0', '20px', '0']
      css_class: fullscreen
  
  - block: markdown
    content:
      title:
      subtitle:
      text: |
        {{% cta cta_link="./people/" cta_text="Meet the team →" %}}
    design:
      columns: '1'
---

