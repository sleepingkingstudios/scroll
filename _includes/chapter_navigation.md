<p>
  {% if next_chapter %}
    <span style="float: right">
      <a href="{{site.baseurl}}/chapters/{{author.slug}}/{{story.slug}}/{{next_chapter.slug}}">
        {{ next_chapter.title }} >
      </a>
    </span>
  {% endif %}

  {% if prev_chapter %}
    <span>
      <a href="{{site.baseurl}}/chapters/{{author.slug}}/{{story.slug}}/{{prev_chapter.slug}}">
        < {{ prev_chapter.title }}
      </a>
    </span>
  {% else %}
    &nbsp;
  {% endif %}
</p>
