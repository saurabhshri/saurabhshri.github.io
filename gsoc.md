---
layout: page
permalink: /gsoc/index.html
title: Saurabh Shrivastava's GSoC 2017 Project Page | GSoC with CCExtractor
tags:
  - GSoC
  - open-source
  - CCAligner
  - subtitles
  - timeline
  - milestones
  - deliverable
  - evaluation
imagefeature: posts/Accepted_in_GSoC.png
chart: true
description: >-
  This page contains information pertaining to Saurabh Shrivastava's GSoC project which include, but is not limited to - project timeline, milestones, deliverable
  et cetera.
comments: true
categories:
  - GSoC
featured: false
---
<figure>
  <img src="{{ site.url }}/images/about/saurabh-shrivastava.png" alt="Saurabh Shrivastava" style="width:35%;" >
  <figcaption>Saurabh Shrivastava</figcaption>
</figure>

{% assign total_words = 0 %}
{% assign total_readtime = 0 %}
{% assign featuredcount = 0 %}
{% assign statuscount = 0 %}

{% for post in site.posts %}
    {% assign post_words = post.content | strip_html | number_of_words %}
    {% assign readtime = post_words | append: '.0' | divided_by:200 %}
    {% assign total_words = total_words | plus: post_words %}
    {% assign total_readtime = total_readtime | plus: readtime %}
    {% if post.featured %}
    {% assign featuredcount = featuredcount | plus: 1 %}
    {% endif %}
{% endfor %}


My name is **Saurabh Shrivastava**, and this is my personal blog. I am an Information Technology Engineering undergraduate student at [Institute of Engineering & Technology, DAVV Indore](http://ietdavv.edu.in/ "IET DAVV, Indore"). I was born and brought up in Bhopal, MP and I am currently studying in Indore, MP. 

I recently got introduced to the world of open source and I haven’t looked back since. I absolutely love the idea of open source software and am thouroughly enjoying it. I am trying my part to [contribute](https://github.com/saurabhshri "My Github Profile.") as I learn :) It feels amazing to know that my contribution is _actually_ out there and people are using it.

My proposal for creating a tool for _word by word audio subtitle synchronization_ has been [accepted](https://saurabhshri.github.io/2017/05/gsoc/accepted-in-google-summer-of-code-2017 "Accepted in Google Summer of Code 2017!") for Google Summer of Code, 2017 with the amazing organization - [CCExtractor Development](https://ccextractor.org), and I will be spending my summer building it. :)

This blog will be the place where I primarily log my GSoC progress. It currently has {{ site.posts | size }} posts in {{ site.categories | size }} categories which combinedly have {{ total_words }} words, which will take an average reader ({{ site.wpm }} WPM) approximately <span class="time">{{ total_readtime }}</span> minutes to read. {% if featuredcount != 0 %}There are <a href="{{ site.url }}/featured">{{ featuredcount }} featured posts</a>, you should definitely check those out.{% endif %} The most recent post is {% for post in site.posts limit:1 %}{% if post.description %}<a href="{{ site.url }}{{ post.url }}" title="{{ post.description }}">"{{ post.title }}"</a>{% else %}<a href="{{ site.url }}{{ post.url }}" title="{{ post.description }}" title="Read more about {{ post.title }}">"{{ post.title }}"</a>{% endif %}{% endfor %} which was published on {% for post in site.posts limit:1 %}{% assign modifiedtime = post.modified | date: "%Y%m%d" %}{% assign posttime = post.date | date: "%Y%m%d" %}<time datetime="{{ post.date | date_to_xmlschema }}" class="post-time">{{ post.date | date: "%d %b %Y" }}</time>{% if post.modified %}{% if modifiedtime != posttime %} and last modified on <time datetime="{{ post.modified | date: "%Y-%m-%d" }}" itemprop="dateModified">{{ post.modified | date: "%d %b %Y" }}</time>{% endif %}{% endif %}{% endfor %}. The last commit was on {{ site.time | date: "%A, %d %b %Y" }} at {{ site.time | date: "%I:%M %p" }} [UTC](http://en.wikipedia.org/wiki/Coordinated_Universal_Time "Temps Universel Coordonné").

<figure>
	<img src="{{ site.url }}/images/posts/accepted_proof.PNG" alt="CCAligner | Saurabh Shrivastava | CCExtractor">
	<figcaption>My accepted GSoC 2017 project, as listed on official GSoC website</figcaption>
</figure>

<!--
<figure class="third">
	<a href="{{ site.url }}/images/about/1.jpg"><img src="{{ site.url }}/images/about/1-001.jpg"></a>
	<a href="{{ site.url }}/images/about/2.jpg"><img src="{{ site.url }}/images/about/2-001.jpg"></a>
	<a href="{{ site.url }}/images/about/3.jpg"><img src="{{ site.url }}/images/about/3-001.jpg"></a>
</figure>
<figure class="half">
	<a href="{{ site.url }}/images/about/4.jpg"><img src="{{ site.url }}/images/about/4-001.jpg"></a>
	<a href="{{ site.url }}/images/about/5.jpg"><img src="{{ site.url }}/images/about/5-001.jpg"></a>
</figure>
<figure class="third">
	<a href="{{ site.url }}/images/about/6.jpg"><img src="{{ site.url }}/images/about/6-001.jpg"></a>
	<a href="{{ site.url }}/images/about/7.jpg"><img src="{{ site.url }}/images/about/7-001.jpg"></a>
	<a href="{{ site.url }}/images/about/8.jpg"><img src="{{ site.url }}/images/about/8-001.jpg"></a>
	<figcaption>Doha at its full glory.</figcaption>
</figure>

-->

At some point in the not-terribly-distant future, I hope to become a good and professional software developer. I am learning as I try and explore things.

Thank you for taking your time out to read this. Follow the blog to subscribe to my future posts. 

-  
_Saurabh Shrivastava_  
_May The Twenty Fourth Be With You!_