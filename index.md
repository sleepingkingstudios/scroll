---
---

# Scroll

## [All Authors](/authors)

<ul>
  {% for author in site.authors limit:5 %}
    {% assign stories = site.stories | where: "author", author.slug %}
    <li>
      <a href="{{site.baseurl}}/authors/{{author.slug}}">{{ author.name }}</a>
      ({{ stories | size }} Stor{% if stories.size == 1 %}y{% else %}ies{% endif %})
    </li>
  {% endfor %}
</ul>

## [All Stories](/stories)

<ul>
  {% for story in site.stories limit:10 %}
    {% assign author = site.authors | where: "slug", story.author | first %}
    <li>
      <a href="{{site.baseurl}}/stories/{{story.author}}/{{story.slug}}">{{ story.title }}</a>
      by
      <a href="{{site.baseurl}}/authors/{{author.slug}}">{{ author.name }}</a>
    </li>
  {% endfor %}
</ul>
