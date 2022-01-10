---
layout: default
---

{% assign author = page %}

<h1>{{ author.name }}</h1>

{% assign stories = site.stories | where: "author", author.slug %}

<h2>About</h2>

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

<h2>Stories ({{ stories | size }})</h2>

<ul>
  {% for story in stories %}
    <li>
      <a href="{{site.baseurl}}/stories/{{ author.slug }}/{{ story.slug }}">
        {{ story.title }}
      </a>
    </li>
  {% endfor %}
</ul>

{{ content }}

<hr>

<a href="{{site.baseurl}}/authors">Back To Authors</a>
