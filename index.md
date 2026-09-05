---
layout: default
title: Home
---

# Welcome to Statistically Savvy

Welcome to my corner of the internet.

I'm interested in statistics, machine learning, data science, and interesting projects involving data.

## Latest Blog Posts

{% for post in site.posts limit:5 %}

### [{{ post.title }}]({{ post.url | relative_url }})

{{ post.excerpt }}

[Read more →]({{ post.url | relative_url }})

{% endfor %}
