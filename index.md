---
layout: default
title: BC Wiki
---
	<h1>{{ page.title }}</h1>
	<ul class="wikipages">

	  {% for wikipage in site.wikipages %}
	    <li> » <a href="{{ wikipage.url }}" title="{{ wikipage.title }}">{{ post.title }}</a></li>
	  {% endfor %}
	</ul>
