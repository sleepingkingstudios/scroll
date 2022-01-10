---
layout: default
---

{% assign story = page %}
{% assign author = site.authors | where: "slug", story.author | first %}
{% capture qualified_slug %}{{ author.slug }}--{{ story.slug }}{% endcapture %}
{% assign chapters = site.chapters | where: "story", qualified_slug %}
{% assign chapters_count = chapters | size %}

<h1>{{ story.title }}</h1>

<p>
  By
  <a href="{{site.baseurl}}/authors/{{author.slug}}">{{ author.name }}</a>
</p>

<p>
  <strong>Rating:</strong> {{ story.rating }}
</p>

<p>
  <strong>Fandoms:</strong> {{ story.fandoms | join: ", " }}
</p>

<p>
  <strong>Pairings:</strong> {{ story.pairings | join: ", " }}
</p>

<p>
  <strong>Tags:</strong> {{ story.tags | join: ", " }}
</p>

{{ content }}

{% if chapters_count == 1 %}
  {% assign chapter = chapters | first %}
  {{ chapter.content }}
{% else %}
  <h2>Chapters</h2>

  <ul>
    {% for chapter in chapters %}
      <li><a href="{{site.baseurl}}/chapters/{{author.slug}}/{{story.slug}}/{{chapter.slug}}">{{ chapter.title }}</a></li>
    {% endfor %}
  </ul>
{% endif %}

<hr>

<a href="{{site.baseurl}}/stories">Back To Stories</a>
