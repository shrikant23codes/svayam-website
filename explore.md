---
layout: default
title: To Explore
permalink: /explore/
---

<div class="explore-wrapper">
  <header class="explore-header">
    <h1>To Explore</h1>
    <p class="description">A running queue of videos, podcasts, blogs, books, and other things to watch or read.</p>
  </header>

  <div class="explore-filters" aria-label="Explore filters">
    <button class="explore-filter is-active" type="button" data-filter="all">All</button>
    <button class="explore-filter" type="button" data-filter="video">Videos</button>
    <button class="explore-filter" type="button" data-filter="podcast">Podcasts</button>
    <button class="explore-filter" type="button" data-filter="blog">Blogs</button>
    <button class="explore-filter" type="button" data-filter="book">Books</button>
    <button class="explore-filter" type="button" data-filter="done">Done</button>
  </div>

  {% assign queued_items = site.data.explore | where_exp: "item", "item.status != 'done'" %}
  {% assign done_items = site.data.explore | where: "status", "done" %}

  <section class="explore-section" data-section="queued">
    <div class="explore-section-header">
      <h2>Queued</h2>
      <span>{{ queued_items | size }} item{% unless queued_items.size == 1 %}s{% endunless %}</span>
    </div>

    <div class="explore-list">
      {% for item in queued_items %}
        {% include explore-item.html item=item %}
      {% endfor %}

      {% if queued_items.size == 0 %}
      <p class="explore-empty">Nothing queued yet.</p>
      {% endif %}
    </div>
  </section>

  <details class="explore-section explore-done" data-section="done">
    <summary>
      <span>Done</span>
      <span>{{ done_items | size }} item{% unless done_items.size == 1 %}s{% endunless %}</span>
    </summary>

    <div class="explore-list">
      {% for item in done_items %}
        {% include explore-item.html item=item status="done" status_label="Done" %}
      {% endfor %}

      {% if done_items.size == 0 %}
      <p class="explore-empty">Nothing completed yet.</p>
      {% endif %}
    </div>
  </details>

  <p class="explore-empty explore-filter-empty" hidden>No items match this filter yet.</p>
</div>

<script>
const filterButtons = document.querySelectorAll('.explore-filter');
const sections = document.querySelectorAll('.explore-section');
const filterEmptyMessage = document.querySelector('.explore-filter-empty');

filterButtons.forEach((button) => {
  button.addEventListener('click', () => {
    const filter = button.dataset.filter;

    filterButtons.forEach((item) => item.classList.remove('is-active'));
    button.classList.add('is-active');

    document.querySelectorAll('.explore-item').forEach((item) => {
      item.hidden = filter !== 'all' && item.dataset.type !== filter && item.dataset.status !== filter;
    });

    const isAll = filter === 'all';
    let hasVisibleItems = false;
    sections.forEach((section) => {
      const visibleItems = section.querySelectorAll('.explore-item:not([hidden])');
      const emptyMessage = section.querySelector('.explore-empty');

      section.hidden = visibleItems.length === 0 && !isAll;

      if (emptyMessage) {
        emptyMessage.hidden = visibleItems.length > 0 || !isAll;
      }

      if (section.tagName === 'DETAILS') {
        section.open = visibleItems.length > 0 && !isAll;
      }

      if (visibleItems.length) {
        hasVisibleItems = true;
      }
    });

    filterEmptyMessage.hidden = isAll || hasVisibleItems;
  });
});
</script>
