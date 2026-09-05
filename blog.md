---
layout: default
title: Blog
permalink: /blog/
---

# Blog

Welcome to the Statistically Savvy blog.

Here you'll find articles about statistics, machine learning, data science, and my projects.

{% for post in site.posts %}

<article>

<h2>
<a href="{{ post.url | relative_url }}">{{ post.title }}</a>
</h2>

<p class="post-date">
{{ post.date | date: "%B %d, %Y" }}
</p>

{{ post.excerpt }}

<p>
<a href="{{ post.url | relative_url }}">Read more →</a>
</p>

</article>

{% endfor %}
