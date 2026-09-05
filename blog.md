---
layout: default
title: Blog
permalink: /blog/
---

# Blog

Welcome to the Statistically Savvy blog.

Here you'll find articles about statistics, machine learning, data science, and my projects.

{% for post in site.posts %}

## [{{ post.title }}]({{ post.url | relative_url }})

<p class="post-date">
{{ post.date | date: "%B %d, %Y" }}
</p>

{{ post.excerpt }}

[Read more →]({{ post.url | relative_url }})

---

{% endfor %}
