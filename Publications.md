---
layout: publication
title: Publications
permalink: /Publications/
---

{% include home-header.html %}

<h1>{{ page.title }}</h1>

{%- assign publications = site.posts | sort: 'date' | reverse -%}

<div class="publications">
  {%- assign grouped_publications = publications | group_by_exp: "post", "post.date | date: '%Y'" -%}
  {%- for year in grouped_publications -%}
    <h2>{{ year.name }}</h2>
    <ul>
      {%- for post in year.items -%}
        <li>
          <p>
            {%- if post.authors -%}
              {%- assign bold_authors = post.authors | replace: "Y.-C. Tsai", "<strong>Y.-C. Tsai</strong>" -%}
              {{ bold_authors }},
            {%- endif -%}
            {{ post.date | date: '%Y' }}:
            {{ post.title }}.
            {%- if post.journal -%}
              <em>{{ post.journal }}</em>.
            {%- endif -%}
            {%- if post.status -%}
              {{ post.status }}.
            {%- endif -%}
            {%- if post.doi -%}
              <a href="{{ post.doi }}" target="_blank">{{ post.doi }}</a>
            {%- endif -%}
          </p>
        </li>
      {%- endfor -%}
    </ul>
  {%- endfor -%}
</div>
