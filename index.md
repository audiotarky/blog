---
layout: landing
---

# Audiotarky Blog

## Posts
{% for post in site.posts %}
### [{{post.title}}]({{post.url}})

<div class="post-info post-info-landing left">Posted by {{post.author}}, {{ post.date | date: "%b %-d, %Y" }}</div>
{{post.excerpt | strip_html | strip}}

{% endfor %}