---
layout: default
title: "Professor Elena Rodriguez"
author_id: elena_rodriguez
---

# {{ site.data.authors[page.author_id].name }}

**{{ site.data.authors[page.author_id].role }}**

{{ site.data.authors[page.author_id].bio }}

## Recent Articles

{% assign author_posts = site.posts | where: "author", site.data.authors[page.author_id].name %}
{% for post in author_posts %}
- [{{ post.title }}]({{ post.url }}) - {{ post.date | date: "%B %d, %Y" }}
{% endfor %}

## Connect

{% if site.data.authors[page.author_id].twitter %}
- [Twitter](https://twitter.com/{{ site.data.authors[page.author_id].twitter }})
{% endif %}
{% if site.data.authors[page.author_id].github %}
- [GitHub](https://github.com/{{ site.data.authors[page.author_id].github }})
{% endif %}
{% if site.data.authors[page.author_id].linkedin %}
- [LinkedIn](https://linkedin.com/in/{{ site.data.authors[page.author_id].linkedin }})
{% endif %}