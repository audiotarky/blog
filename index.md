---
layout: landing
---

# Audiotarky Blog

## Posts
{% for post in site.posts %}
### [{{post.title}}]({{post.url}})

{{post.excerpt | strip_html | strip}}

<div class="post-info left">Posted by {{post.author}}, {{ post.date | date: "%b %-d, %Y" }}</div>
{% endfor %}