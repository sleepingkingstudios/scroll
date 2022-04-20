<p>
  {% if next_chapter %}
    {% capture build_next_chapter_url %}
      {{ site.baseurl }}/chapters
      {% if author %}
        /{{ author.slug }}
      {% endif %}
      /{{story.slug}}
      /{{next_chapter.slug}}
    {% endcapture %}
    {% assign next_chapter_url = build_next_chapter_url | strip_newlines | replace: " ", "" %}
    <span style="float: right">
      <a href="{{next_chapter_url}}">
        {{ next_chapter.title }} >
      </a>
    </span>
  {% endif %}

  {% if prev_chapter %}
    {% capture build_prev_chapter_url %}
      {{ site.baseurl }}/chapters
      {% if author %}
        /{{ author.slug }}
      {% endif %}
      /{{story.slug}}
      /{{prev_chapter.slug}}
    {% endcapture %}
    {% assign prev_chapter_url = build_prev_chapter_url | strip_newlines | replace: " ", "" %}
    <span>
      <a href="{{prev_chapter_url}}">
        < {{ prev_chapter.title }}
      </a>
    </span>
  {% else %}
    &nbsp;
  {% endif %}
</p>
