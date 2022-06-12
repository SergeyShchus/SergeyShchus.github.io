---
layout: default
title: Projects
description: Slides and transcripts of my best talks.
---

<div class="completeright">

    <!-- display the name of the category -->
    <div class="category-header">
      <hr>
      <h2>Projects</h2>

      <!-- Go back the main page to see a collection of my best projects -->
      <div class="sidebar-text">
        &rarr; <a href="/index.html#projects">GO TO THE MAIN PAGE TO SEE ONLY ✦ SELECTED PROJECTS</a>
      </div>

      <!-- put a little intro text below the category title -->
      <div class="blogcontainer article-text">
          <p>Before delving into data vis, I studied print design for six years. Here are some of my older works that are still data vis related, and newer ones I've created for newsrooms or my blog. Heck, there's even one (!) interactive graphic in here.</p>
      </div>
    </div>


  <div class="grid">

    {% for post in site.categories.design %}

    <!-- don't display about and impressum page -->
    {% unless post.layout == 'withoutdate' %}

      <!-- open external links -->
      {% capture url_to_use %}{{ post.url }}{% endcapture %}
      {% if post.external %}
        {% capture url_to_use %}{{ post.external }}{% endcapture %}
      {% endif %}

      <!-- display title, image and date for each post -->
      <a class="thumb" href="{{ post.url }}">
      <div class="post">
        <div class="post-image">
          <img src="{{ post.image }}"/>
        </div>
        <div class="post-date">

          <!-- show if it's a faved article -->
          {% if post.categories contains "fav" %}
            ✦
          {% endif %}

          <!-- display month & year when blog post or talk. Only display year for design work -->
          {% if category contains "design" %}
             {{ post.date | date: "%Y" }}
          {% else %}
             {{ post.date | date: "%B %Y" }}
          {% endif %}

          <!-- show for which client I've worked for -->
          {% unless post.whofor == nil %}
            <b><span style="color:#cc0000">{{ post.whofor }}</b></span>
          {% endunless %}



        </div>
        <h1 class="post-title">
            {{ post.title }}
        </h1>
        <div class="post-date">
            {{ post.summary }}
        </div>
      </div></a>

      {% endunless %}
    {% endfor %}


  </div>

  <!-- <div class="category-header">
    <hr>
    <h2>All articles</h2>
  </div>
  {% include aboutme.html %} -->

</div>