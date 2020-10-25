---
layout: page
title: Archive
spacing: double
---
<body>
{% assign postsByYearMonth = site.posts | group_by_exp: "post", "post.date | date: '%B %Y'" %}
{% for yearMonth in postsByYearMonth %}
  <!-- {{ yearMonth.name }} -->

  <ul style="margin: -15px;">

    {% for post in yearMonth.items %}
      <li><a href="{{ post.url | relative_url }}">{{ post.title }}</a>
      </li>
    {% endfor %}</ul><p align="right">{{ yearMonth.name }}</p>

{% endfor %}

</body>
