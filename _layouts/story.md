---
layout: default
---

{% assign story = page %}
{% assign author = site.authors | where: "slug", story.author | first %}
{% capture build_qualified_slug %}
  {% if author %}
    {{ author.slug | default: story.author | slugify }}--
  {% endif %}
  {{ story.slug }}
{% endcapture %}
{% assign qualified_slug = build_qualified_slug | strip_newlines | replace: " ", "" %}
{% assign chapters = site.chapters | where: "story", qualified_slug | sort: "chapter_index" %}
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
      {% capture build_chapter_url %}
        {{ site.baseurl }}/chapters
        {% if author %}
          /{{ author.slug }}
        {% endif %}
        /{{story.slug}}
        /{{chapter.slug}}
      {% endcapture %}
      {% assign chapter_url = build_chapter_url | strip_newlines | replace: " ", "" %}
      <li><a href="{{chapter_url}}">{{ chapter.title }}</a></li>
    {% endfor %}
  </ul>
{% endif %}

<hr>

<a href="{{site.baseurl}}/stories">Back To Stories</a>
