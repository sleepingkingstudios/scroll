---
---

# All Stories

<ul>
  {% assign stories = site.stories | sort: "title" %}
  {% for story in stories %}
    {% assign author = site.authors | where: "slug", story.author | first %}
    <li>
      {% if author %}
        <a href="{{site.baseurl}}/stories/{{story.author}}/{{story.slug}}">{{ story.title }}</a>
        by
        <a href="{{site.baseurl}}/authors/{{author.slug}}">{{ author.name }}</a>
      {% else %}
        <a href="{{site.baseurl}}/stories/{{story.slug}}">{{ story.title }}</a>
        by
        {{ story.author }}
      {% endif %}
      <br>
      Rating: {{ story.rating | default: "None" }}
      |
      Fandoms: {{ story.fandoms | join: ", " | default: "None" }}
      |
      Pairings: {{ story.pairings | join: ", " | default: "None" }}
      |
      Tags: {{ story.tags | join: ", " | default: "None" }}
    </li>
  {% endfor %}
</ul>
