---
title: "THUFV Lab - Project"
layout: gridlay
excerpt: "THUFV Lab -- Project"
sitemap: false
redirect_from:
  - /zord/
permalink: /projects/
---

# Projects

{% assign number_printed = 0 %}
{% for proje in site.data.prolist %}

{% assign even_odd = number_printed | modulo: 2 %}
{% if proje.highlight == 1 %}

{% if even_odd == 0 %}
<div class="row">
{% endif %}

<div class="col-sm-6 clearfix">
 <div class="well">
  <pubtit>{{ proje.title }}</pubtit>
  <img src="{{ site.url }}{{ site.baseurl }}/images/propic/{{ proje.image }}" class="img-responsive" width="45%" style="float: left" />
  <p>{{ proje.description }}</p>
  <p><em>{{ proje.authors }}</em></p>
  {% for link in proje.links %}
  <p><strong><a href="{{ link.url }}">{{ link.display }}</a></strong></p>
  {% endfor %}
  <p class="text-danger"><strong> {{ proje.news1 }}</strong></p>
  <p> {{ proje.news2 }}</p>
 </div>
</div>

{% assign number_printed = number_printed | plus: 1 %}

{% if even_odd == 1 %}
</div>
{% endif %}

{% endif %}
{% endfor %}

{% assign even_odd = number_printed | modulo: 2 %}
{% if even_odd == 1 %}
</div>
{% endif %}

<p> &nbsp; </p>