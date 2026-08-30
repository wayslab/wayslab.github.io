---
layout: page
permalink: code/
---
<h2>Code</h2>
<ul>
{% for article in site.posts %}
  {% if article.github %}
    <li> 
      <a href="{{ article.github }}">{{ article.title }}</a> ({{ article.date | date: "%Y %B" }})
      {% if article.github_desc %}
        <p>{{ article.github_desc }}</p>
      {% elsif article.osd %}
        <p>{{ article.osd }}</p>
      {% endif %}
    </li>
  {% endif %}
  {% for misc in article.miscs %}
    {% if misc.content_url contains "github.com" and misc.content_url != article.github %}
    <li>
      <a href="{{ misc.content_url }}">{{ article.title }} — {{ misc.content_type }}</a> ({{ article.date | date: "%Y %B" }})
      {% if misc.content_desc %}
        <p>{{ misc.content_desc }}</p>
      {% endif %}
    </li>
    {% endif %}
  {% endfor %}
{% endfor %}
</ul>

<h2>Datasets</h2>
<ul>
{% for article in site.posts %}
  {% if article.dataset %}
    <li> 
      <a href="{{ article.dataset }}">{{ article.title }}</a> ({{ article.date | date: "%Y %B" }})
      {% if article.osd %}
        <p>{{ article.osd }}</p>
      {% endif %}
    </li>
  {% endif %}
  {% for misc in article.miscs %}
    {% if misc.content_type == "Dataset" %}
    <li>
      <a href="{{ misc.content_url }}">{{ article.title }}</a> ({{ article.date | date: "%Y %B" }})
      {% if misc.content_desc %}
        <p>{{ misc.content_desc }}</p>
      {% elsif article.osd %}
        <p>{{ article.osd }}</p>
      {% endif %}
    </li>
    {% endif %}
  {% endfor %}
{% endfor %}
</ul>
  