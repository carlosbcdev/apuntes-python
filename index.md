---
layout: default
title: "Inicio"
---

# Python para zafiro

## Temas:

{% for post in site.posts %}
- [{{ post.title }}]({{ post.url }})
{% endfor %}


