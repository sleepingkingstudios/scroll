---
layout: default
---

{% assign chapter = page %}
{% assign author_slug = chapter.story | split: "--" | first %}
{% assign author = site.authors | where: "slug", author_slug | first %}
{% assign story_slug = chapter.story | split: "--" | last %}
{% assign story = site.stories | where: "author", author_slug | where: "slug", story_slug | last %}
{% unless story %}
  {% assign story = site.stories | where: "slug", story_slug | last %}
{% endunless %}
{% assign story_chapters = site.chapters | where: "story", chapter.story %}
{% if chapter.next_chapter %}
  {% assign next_chapter = story_chapters | where: "slug", chapter.next_chapter | first %}
{% endif %}
{% if chapter.prev_chapter %}
  {% assign prev_chapter = story_chapters | where: "slug", chapter.prev_chapter | first %}
{% endif %}

<h1>{{ story.title }}</h1>

<p>
  By
  {% if author %}
    <a href="{{site.baseurl}}/authors/{{author.slug}}">{{ author.name }}</a>
  {% else %}
    {{ story.author }}
  {% endif %}
</p>

{% include chapter_navigation.md %}

<h2>{{ chapter.title }}</h2>

{{ content }}

{% include chapter_navigation.md %}

<hr>

{% if author %}
  <a href="{{site.baseurl}}/stories/{{story.author}}/{{story.slug}}">Back To {{ story.title }}</a>
{% else %}
  <a href="{{site.baseurl}}/stories/{{story.slug}}">Back To {{ story.title }}</a>
{% endif %}
