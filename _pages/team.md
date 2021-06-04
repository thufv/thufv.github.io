---
title: "Allan Lab - Team"
layout: gridlay
excerpt: "Allan Lab: Team members"
sitemap: false
permalink: /team/
---

# Group Members

**We are looking for passionate new PhD students, Postdocs, and Master students to join the team! Do not hesitate to contact us if you're interested to our research.**

## Faculty
{% assign number_printed = 0 %}
{% for member in site.data.team_members %}

{% assign even_odd = number_printed | modulo: 2 %}

{% if even_odd == 0 %}
<div class="row">
{% endif %}

<div class="col-sm-6 clearfix">
  <h4>{{ member.name }}</h4>
  <i>{{ member.info }}<br>email: <{{ member.email }}></i>
  <ul style="overflow: hidden">

  {% if member.number_intro == 1 %}
  <li> {{ member.intro1 }} </li>
  {% endif %}

  {% if member.number_intro == 2 %}
  <li> {{ member.intro1 }} </li>
  <li> {{ member.intro2 }} </li>
  {% endif %}

  {% if member.number_intro == 3 %}
  <li> {{ member.intro1 }} </li>
  <li> {{ member.intro2 }} </li>
  <li> {{ member.intro3 }} </li>
  {% endif %}

  {% if member.number_intro == 4 %}
  <li> {{ member.intro1 }} </li>
  <li> {{ member.intro2 }} </li>
  <li> {{ member.intro3 }} </li>
  <li> {{ member.intro4 }} </li>
  {% endif %}

  {% if member.number_intro == 5 %}
  <li> {{ member.intro1 }} </li>
  <li> {{ member.intro2 }} </li>
  <li> {{ member.intro3 }} </li>
  <li> {{ member.intro4 }} </li>
  <li> {{ member.intro5 }} </li>
  {% endif %}

  </ul>
</div>

{% assign number_printed = number_printed | plus: 1 %}

{% if even_odd == 1 %}
</div>
{% endif %}

{% endfor %}

{% assign even_odd = number_printed | modulo: 2 %}
{% if even_odd == 1 %}
</div>
{% endif %}




## Students
{% assign number_printed = 0 %}
{% for member in site.data.students %}

{% assign even_odd = number_printed | modulo: 2 %}

{% if even_odd == 0 %}
<div class="row">
{% endif %}

<div class="col-sm-6 clearfix">
  <h4>{{ member.name }}</h4>
  <i>{{ member.info }}<br>email: <{{ member.email }}></i>
  <ul style="overflow: hidden">

  {% if member.number_intro == 1 %}
  <li> {{ member.intro1 }} </li>
  {% endif %}

  {% if member.number_intro == 2 %}
  <li> {{ member.intro1 }} </li>
  <li> {{ member.intro2 }} </li>
  {% endif %}

  {% if member.number_intro == 3 %}
  <li> {{ member.intro1 }} </li>
  <li> {{ member.intro2 }} </li>
  <li> {{ member.intro3 }} </li>
  {% endif %}

  {% if member.number_intro == 4 %}
  <li> {{ member.intro1 }} </li>
  <li> {{ member.intro2 }} </li>
  <li> {{ member.intro3 }} </li>
  <li> {{ member.intro4 }} </li>
  {% endif %}

  </ul>
</div>

{% assign number_printed = number_printed | plus: 1 %}

{% if even_odd == 1 %}
</div>
{% endif %}

{% endfor %}

{% assign even_odd = number_printed | modulo: 2 %}
{% if even_odd == 1 %}
</div>
{% endif %}
