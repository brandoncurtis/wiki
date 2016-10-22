---
layout: default
title: Hank Quinlan's Blog
---
	<h1>{{ page.title }}</h1>
	<ul class="wikipages">

	  {% for wikipage in site.wikipages %}
	    <li><span>{{ wikipage.date | date_to_string }}</span> » <a href="{{ wikipage.url }}" title="{{ wikipage.title }}">{{ post.title }}</a></li>
	  {% endfor %}
	</ul>
