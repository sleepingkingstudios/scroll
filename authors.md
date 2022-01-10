---
title: All Authors
---

# All Authors

{% for author in site.authors %}
  {% assign stories = site.stories | where: "author", author.slug %}
  <div>
    <h2>
      <a href="{{site.baseurl}}/authors/{{author.slug}}">
        {{ author.name }}
      </a>
    </h2>
    <h3>Stories ({{ stories | size }})</h3>
    <ul>
      {% for story in stories limit:5 %}
        <li>
          <a href="{{site.baseurl}}/stories/{{ author.slug }}/{{ story.slug }}">
            {{ story.title }}
          </a>
        </li>
      {% endfor %}
    </ul>
    <h3>Fandoms</h3>
    <ul>
      {% for fandom in author.fandoms %}
        <li>{{ fandom }}</li>
      {% endfor %}
    </ul>
    <h3>External URLs</h3>
    <ul>
      {% for site_url in author.site_urls %}
        <li><a href="{{site_url.last}}">{{site_url.first}}</a></li>
      {% endfor %}
    </ul>
  </div>
{% endfor %}
