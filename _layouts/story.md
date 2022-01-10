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
  {% if author %}
    <a href="{{site.baseurl}}/authors/{{author.slug}}">{{ author.name }}</a>
  {% else %}
    {{ story.author }}
  {% endif %}
</p>

{% if story.rating %}
  <p>
    <strong>Rating:</strong> {{ story.rating }}
  </p>
{% endif %}

{% if story.fandoms %}
  <p>
    <strong>Fandoms:</strong> {{ story.fandoms | join: ", " }}
  </p>
{% endif %}

{% if story.pairings %}
  <p>
    <strong>Pairings:</strong> {{ story.pairings | join: ", " }}
  </p>
{% endif %}

{% if story.tags %}
  <p>
    <strong>Tags:</strong> {{ story.tags | join: ", " }}
  </p>
{% endif %}

{{ content }}

{% if chapters_count == 0 %}
  <!-- Do nothing here. -->
{% elsif chapters_count == 1 %}
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
