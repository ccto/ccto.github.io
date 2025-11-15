---
layout: home
show_menu: false
---

{% assign paginated_posts = paginator.posts | default: site.posts %}

{% if paginated_posts.size > 0 %}
<ul class="paginated-posts">
{% for post in paginated_posts %}
  <li>
    <span>{{ post.date | date: site.theme_config.date_format }}</span>
    <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
  </li>
{% endfor %}
</ul>
{% endif %}

{% if paginator and paginator.total_pages > 1 %}
<nav class="pagination">
  {% if paginator.previous_page %}
    <a class="prev" href="{{ paginator.previous_page_path | relative_url }}">上一页</a>
  {% endif %}
  <span class="page-info">第 {{ paginator.page }} / {{ paginator.total_pages }} 页</span>
  {% if paginator.next_page %}
    <a class="next" href="{{ paginator.next_page_path | relative_url }}">下一页</a>
  {% endif %}
</nav>
{% endif %}
