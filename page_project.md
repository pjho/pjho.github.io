---
layout: default
tag: project
permalink: /tag/project/
---

<h1><span>Posts Tagged:</span> {{ page.tag }}</h1>

Below are few fairly recent projects I've completed. Some of the websites are recent commercial/client projects and there's a few toy apps I've built for learning certain technologies.

<ul class="post-list">
  {% for post in site.tags[page.tag] %}
  {% include post-list-item.html %}
  {% endfor %}
</ul>
