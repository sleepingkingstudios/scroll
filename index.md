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
