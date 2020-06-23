---
title: "Allan Lab - Team"
layout: gridlay
excerpt: "Allan Lab: Team members"
sitemap: false
permalink: /team/
---

# Group Members

**We are looking for passionate new PhD students, Postdocs, and Master students to join the team! Do not hesitate to contact [us](hefei@tsinghua.edu.cn) if you're interested to our research.**

Jump to [staff](#staff), [alumni](#alumni), [administrative support](#administrative-support).

## Staff
{% assign number_printed = 0 %}
{% for member in site.data.team_members %}

{% assign even_odd = number_printed | modulo: 2 %}

{% if even_odd == 0 %}
<div class="row">
{% endif %}

<div class="col-sm-6 clearfix">
  <img src="{{ site.url }}{{ site.baseurl }}/images/teampic/{{ member.photo }}" class="img-responsive" width="25%" style="float: left" />
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




## Master and Bachelor Students
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

## Alumni
<div class="row">

<div class="col-sm-6 clearfix">
<h4>PhD Students</h4>
{% for member in site.data.alumni_phd %}
{{ member.name }}
{% endfor %}
</div>

<div class="col-sm-6 clearfix">
<h4>Master students</h4>
{% for member in site.data.alumni_master %}
{{ member.name }}
{% endfor %}
</div>

</div>


## Administrative Support
<a href="mailto:Rijsewijk@Physics.LeidenUniv.nl">Ellie van Rijsewijk</a> is helping us (and other groups) with administration.
