---
title: Projects
layout: default
permalink: /projects/
published: true
---

<!-- for data engineering project -->
<div class="ProjectContainer">
  <div><h2>Data Enginnering projects </h2></div>
  <div class="gallery">
    
    {% assign de_projects = site.projects | where: "topic", "data_engineering" %}
    
    {% for project in de_projects %}
    
      <div class="projectTile">
        <a href="{{ project.url | relative_url }}">
          <span>
            <h2>{{ project.title }}</h2>
            <br/>
            <p>{{ project.description }}</p>
          </span>
        </a>
      </div>
    {% endfor %}

  </div>
</div>

<!-- for bigquery -->
<div class="ProjectContainer">
  <div><h2>BigQuery projects </h2></div>
  <div class="gallery">
    
    {% assign de_projects = site.projects | where: "topic", "bigquery" %}
    
    {% for project in de_projects %}
    
      <div class="projectTile">
        <a href="{{ project.url | relative_url }}">
          <span>
            <h2>{{ project.title }}</h2>
            <br/>
            <p>{{ project.description }}</p>
          </span>
        </a>
      </div>
    {% endfor %}

  </div>
</div>