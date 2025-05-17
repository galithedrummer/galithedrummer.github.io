---
layout: default
---

# 浏览：pingyin/

{% raw %}
<ul>
  <!-- 子文件夹列表 -->
  {% assign current_dir = "pingyin" %}
  {% assign folders = "" | split: "" %}
  {% for file in site.static_files %}
    {% assign parts = file.path | split: "/" %}
    {% if parts[1] == current_dir %}
      {% if parts.size > parts.index_of(current_dir) | plus: 2 %}
        {% assign subfolder = parts[parts.index_of(current_dir) | plus: 1] %}
        {% unless folders contains subfolder %}
          {% assign folders = folders | push: subfolder %}
          <li><a href="{{ current_dir }}/{{ subfolder }}/index.html">{{ subfolder }}/</a></li>
        {% endunless %}
      {% endif %}
    {% endif %}
  {% endfor %}
</ul>

<h2>文件列表</h2>
<ul>
  {% for file in site.static_files %}
    {% assign parts = file.path | split: "/" %}
    {% if file.path contains current_dir and parts.size == current_dir | split: "/" | size | plus: 1 %}
      <li><a href="{{ file.path }}">{{ file.name }}</a></li>
    {% endif %}
  {% endfor %}
</ul>
{% endraw %}
