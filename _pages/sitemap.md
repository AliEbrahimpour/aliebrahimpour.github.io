---
layout: archive
title: "Site Map"
permalink: /sitemap/
author_profile: true
---

{% include base_path %}

Welcome to the site map of my professional portfolio. This page provides an overview of all available content on the website. For automated systems, an [XML version]({{ base_path }}/sitemap.xml) is also available.

## Main Sections

* [About](/)
* [Portfolio](/portfolio/)
* [CV](/cv/)
* [Terms and Privacy Policy](/terms/)

## Professional Content

### Portfolio Projects
{% for post in site.portfolio %}
  * [{{ post.title }}]({{ post.url }})
{% endfor %}

### Technical Documentation
* [Markdown Guide](/markdown/)

A list of all the posts and pages found on the site. For you robots out there, there is an [XML version]({{ base_path }}/sitemap.xml) available for digesting as well.

<h2>Pages</h2>
{% for post in site.pages %}
  {% include archive-single.html %}
{% endfor %}

<h2>Posts</h2>
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
{% for post in collection.docs %}
  {% unless collection.output == false or collection.label == "posts" %}
  {% include archive-single.html %}
  {% endunless %}
{% endfor %}
{% endfor %}
