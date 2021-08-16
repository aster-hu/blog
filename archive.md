---
layout: page
title: Archive
spacing: double
---
<body>
{% assign postsByYearMonth = site.posts | group_by_exp: "post", "post.date | date: '%B %Y'" %}
{% for yearMonth in postsByYearMonth %}
  <!-- {{ yearMonth.name }} -->
<p style="margin: -1px;">{{ yearMonth.name }}</p>
  <ul>
    {% for post in yearMonth.items %}
      <li><a href="{{ post.url | relative_url }}">{{ post.title }}</a>
      </li>
    {% endfor %}</ul>

{% endfor %}

{% include tagscloud.html %}
</body>
