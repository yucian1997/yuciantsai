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

<!-- Back to Top button -->
<a href="#" onclick="backToTop()" class="back-to-top">Top &#8648;</a>

<script>
  function backToTop() {
    window.scrollTo({ top: 0, behavior: 'smooth' });
  }

  // Mobile menu toggle for the header in home-header.html
  document.addEventListener('DOMContentLoaded', function() {
    const toggles = document.querySelectorAll('.menu-toggle');

    toggles.forEach(function(toggle) {
      const headerBar = toggle.closest('.home-header-bar');
      if (!headerBar) return;

      const menu = headerBar.querySelector('.home-header-menu');
      if (!menu) return;

      toggle.addEventListener('click', function(event) {
        event.preventDefault();
        menu.classList.toggle('open');
      });
    });
  });
</script>

<style>
  /* Back-to-top: fixed bottom-right */
  .back-to-top {
    position: fixed;
    right: 20px;
    bottom: 20px;
    background: #ffffff;
    border: 1px solid #007bff;
    padding: 8px 12px;
    border-radius: 4px;
    color: #007bff;
    font-size: 14px;
    text-decoration: none;
    z-index: 1000;
  }

  .back-to-top:hover {
    background: #007bff;
    color: #ffffff;
  }

  .publications ul {
    padding-left: 1.5rem;
  }

  .publications li {
    margin-bottom: 1rem;
  }

  /* Header container (matches your concept) */
  .home-header-bar {
    width: 100%;
    height: 100%;
    display: flex;
    align-items: center;
    justify-content: space-between;

    -webkit-box-shadow: 0 1em 1em -.9em var(--border-color);
       -moz-box-shadow: 0 1em 1em -.9em var(--border-color);
            box-shadow: 0 1em 1em -.9em var(--border-color);
  }

  /* Desktop: horizontal menu */
  .home-header-menu {
    display: flex;
    gap: 1rem;
    list-style: none;
    margin: 0;
    padding: 0;
  }

  .home-header-menu li {
    margin: 0;
  }

  .home-header-menu .pure-menu-link {
    text-decoration: none;
    border-bottom: 1px solid rgba(0, 0, 0, 0);
  }

  .home-header-menu .pure-menu-link:hover,
  .home-header-menu .pure-menu-link:focus {
    color: inherit;
    background-color: inherit;
    border-bottom-color: var(--link-color);
  }

  .home-header-menu .current-item {
    border-bottom-color: var(--link-color);
  }

  /* Menu toggle link (from home-header.html) */
  .menu-toggle {
    display: none; /* hidden on desktop */
  }

  /* MOBILE: show button, hide menu until open */
  @media (max-width: 768px) {
    .home-header-bar {
      flex-direction: column;
      align-items: flex-start;
    }

    .menu-toggle {
      display: inline-block;
      margin-bottom: 0.5rem;
    }

    .home-header-menu {
      display: none;
      flex-direction: column;
      gap: 0.5rem;
      margin-top: 0.5rem;
    }

    .home-header-menu.open {
      display: flex;
    }
  }
</style>
