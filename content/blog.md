---
layout: base.njk
title: Blog
description: Update from my blog post
pagination:
  data: collections.posts
  size: 5
  reverse: true
testdata:
 - item1
 - item2
 - item3
 - item4
permalink: "blog/{% if pagination.pageNumber > 0 %}page-{{ pagination.pageNumber + 1 }}/{% endif %}index.html"
---
<article class="article-content">
<h1><a href="{{page.url}}">{{title}}</a></h1>
<h2>{{description}}</h2>
<section id="recent-posts">
{%- for post in pagination.items %}
<div class="post">
<h3><a href="{{post.url}}">{{post.data.title}}</a></h3>
<p class="post-meta"><i class="fas fa-calendar"></i> Published on <time datetime="{{ post.date | htmlDateString }}">{{ post.date | readableDate("dd LLLL yyyy") }}</time> by <i class="fas fa-user"></i> <a href="{{metadata.author.url}}">{{metadata.author.name}}</a></p>
<p>{{post.data.description}}</p>
<a href="{{post.url}}">Read {{post.data.title}}</a>
</div>
{% endfor %}
</section>
</article>
<nav>
<ul class="pagination">
{% if pagination.href.previous %}<li><a class="active" href="{{ pagination.href.previous }}">← Previous</a></li>{% endif %}
{% if pagination.href.next %}<li><a class="active" href="{{ pagination.href.next }}">Next →</a></li>{% endif %}
</ul>
</nav>
