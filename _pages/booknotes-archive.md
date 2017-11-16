---
layout: archive
permalink: /book-notes/
---

{% include base_path %}

{% capture written_date %}'None'{% endcapture %}

**Previously, from @alspur's bookshelf**

{% for post in site.posts %}
  
  
  {% if post.link contains "amazon" %}
  
  
  {% capture date %}{{ post.date | date: '%B %Y' }}{% endcapture %}
  
  <div>
  
  {% if date != written_date %}
  
    <h2 class="nav__sub-title">{{ date }}</h2>
    
    {% capture written_date %}{{ date }}{% endcapture %}
    
  {% endif %}
  
  {% include archive-single.html %}
  
  <br>
  
  </div>
  
  {% else %}
  
  
  {% endif %}
  
  

{% endfor %}
