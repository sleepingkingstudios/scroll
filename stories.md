---
---

# All Stories

<ul>
  {% assign stories = site.stories | sort: "title" %}
  {% for story in stories %}
    {% assign author = site.authors | where: "slug", story.author | first %}
    <li>
      <a href="{{site.baseurl}}/stories/{{story.author}}/{{story.slug}}">{{ story.title }}</a>
      by
      <a href="{{site.baseurl}}/authors/{{author.slug}}">{{ author.name }}</a>
      <br>
      Rating: {{ story.rating }}
      |
      Fandoms: {{ story.fandoms | join: ", " }}
      |
      Pairings: {{ story.pairings | join: ", " }}
      |
      Tags: {{ story.tags | join: ", " }}
    </li>
  {% endfor %}
</ul>
