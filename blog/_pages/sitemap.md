---
layout: archive
title: "Карта Сайта"
excerpt: "Список всех записей и страниц, найденных на сайте."
permalink: /sitemap/
author_profile: false
---

Список всех записей и страниц, найденных на сайте. Для роботов доступна [XML-версия]({{ '/sitemap.xml' | relative_url }}) для обработки.

<h2>Страницы</h2>
{% for post in site.pages %}
  {% include archive-single.html %}
{% endfor %}

<h2>Записи</h2>
{% for post in site.posts %}
  {% include archive-single.html %}
{% endfor %}


{% capture written_label %}'None'{% endcapture %}

{% for collection in site.collections %}
  {% unless collection.output == false or collection.label == "posts" %}
    {% capture label %}{{ collection.label }}{% endcapture %}
    {% if label != written_label %}
      <h2>{{ label }}</h2>
      {% capture written_label %}{{ label }}{% endcapture %}
    {% endif %}
  {% endunless %}
  {% for doc in collection.docs %}
    {% unless collection.output == false or collection.label == "posts" %}
      {% include archive-single.html %}
    {% endunless %}
  {% endfor %}
{% endfor %}