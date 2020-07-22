---
layout: default
title: Study
main : true
---

<ul class="catalogue">
    {% assign sorted = site.pages | sort: 'order' | reverse %}
    {% for page in sorted %}
    {% if page.study == true %}
    {% include post-list.html %}
    {% endif %}
    {% endfor %}
 </ul>