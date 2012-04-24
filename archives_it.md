---
layout: default
title: Archivi in italiano
---

<div id="home">
  <h1>Archivi in italiano <img src="{{site.url}}/images/it.png" height="30px" style="padding-left:20px" alt="archivi in italiano" /></h1>
    {% for post in site.tags.italiano %}
      {% capture this_year %}{{ post.date | date: "%Y" }}{% endcapture %}
    {% capture this_month %}{{ post.date | date: "%B" }}{% endcapture %}
    {% capture next_year %}{{ post.previous.date | date: "%Y" }}{% endcapture %}
    {% capture next_month %}{{ post.previous.date | date: "%B" }}{% endcapture %}
  
    {% if forloop.first %}
      <h2>{{this_year}}</h2>
      <h3>{{this_month}}</h3>
      <ul>
    {% endif %}
  
    <li><span>{{ post.date | date: "%B %e, %Y" }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  
    {% if forloop.last %}
      </ul>
    {% else %}
      {% if this_year != next_year %}
        </ul>
        <h2>{{next_year}}</h2>
        <h3>{{next_month}}</h3>
        <ul>
      {% else %}    
        {% if this_month != next_month %}
          </ul>
          <h3>{{next_month}}</h3>
          <ul>
        {% endif %}
      {% endif %}
    {% endif %}
      {% endfor %}
</div>
