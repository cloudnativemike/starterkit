---
layout: default
title: Browse by Tags
permalink: /tags/
---

# Browse Articles by Tags

Explore our articles organized by topic tags:

{% assign sorted_tags = site.tags | sort %}
{% for tag in sorted_tags %}
## {{ tag[0] | capitalize }}

{% for post in tag[1] %}
- [{{ post.title }}]({{ post.url | relative_url }}) - *{{ post.date | date: "%B %d, %Y" }}*
{% endfor %}

---
{% endfor %}

## All Tags

<div style="margin: 20px 0;">
{% for tag in sorted_tags %}
  <span style="display: inline-block; background: #f0f0f0; padding: 4px 8px; margin: 2px; border-radius: 3px; font-size: 0.9em;">
    <a href="#{{ tag[0] }}" style="text-decoration: none; color: #333;">{{ tag[0] }}</a>
    <small>({{ tag[1].size }})</small>
  </span>
{% endfor %}
</div>