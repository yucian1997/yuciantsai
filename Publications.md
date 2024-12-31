---
layout: publication 
title: Publications
permalink: /Publications/ 
---
{% include home-header.html %}

<h1>{{ page.title }}</h1>

{%- assign publications = site.posts | group_by_exp: "post", "post.date | date: '%Y'" -%}

<div class="publications">
  {%- for year in publications reversed -%}
    <h2>{{ year.name }}</h2>
    <ul>
      {%- for post in year.items -%}
        <li>
          <p>
            {%- if post.authors -%}
              {{ post.authors }},
            {%- endif -%}
            {{ post.date | date: '%Y' }}:
            <a href="{{ post.url | relative_url }}">{{ post.title }}</a>.
            {%- if post.journal -%}
              {{ post.journal }},
            {%- endif -%}
            {%- if post.status -%}
              {{ post.status }}.
            {%- endif -%}
          </p>
        </li>
      {%- endfor -%}
    </ul>
  {%- endfor -%}
</div>

<script>
  function backToTop() {
    window.scrollTo({ top: 0, behavior: 'smooth' });
  }
</script>
