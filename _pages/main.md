---
permalink: /main/
---


{% include base_path %}

{% capture counter %}'first'{% endcapture %}

{% for post in site.posts %}

{% capture written_date %}'None'{% endcapture %}

{% for post in site.posts %}

  {% capture date %}{{ post.date | date: '%A, %e %B %Y' }}{% endcapture %}
  
  
{% if post.id %}
  {% assign title = post.title | markdownify | remove: "<p>" | remove: "</p>" %}
{% else %}
  {% assign title = post.title %}
{% endif %}
  
  {% if date != written_date and counter != 'first' %}
  
  <br>
  
  <h3 id="{{ date | slugify }}" class="nav__sub-title">{{ date }}</h3>
    
    {% capture written_date %}{{ date }}{% endcapture %}
    
    {% capture counter %}'older'{% endcapture %}
    
  {% endif %}
    
  <h2><a href="{{ post.url }}">{{ post.title }}</a></h2>
    
  <div class="post">
   
    {{ post.content }}

  </div>
  
{% endfor %}

{% endfor %}
