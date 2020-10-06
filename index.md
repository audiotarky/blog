---
layout: landing
---

# Audiotarky Blog

## Posts
{% for post in site.posts %}
### [{{post.title}}]({{post.url}})

"{{post.excerpt | strip_html | strip}}"

Posted {{ post.date | date: "%b %-d, %Y" }}
{% endfor %}