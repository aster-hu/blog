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
      {% if post.tags.size > 0 %}
        {% for tag in post.tags %}
          {% capture tag_name %}{{ tag }}{% endcapture %}
          <a href="/tag/{{ tag_name }}"><code class="highligher-rouge"><nobr>{{ tag_name }}</nobr></code>&nbsp;</a>
        {% endfor %}
      {% endif %}
      </li>
    {% endfor %}</ul>

{% endfor %}

{% include tagscloud.html %}

</body>
