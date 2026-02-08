<!-- ---
layout: default
body_class: notes-page
title: Notes
permalink: /notes/
---

<div class="collapsible-widget">
  <div class="widget-section">
    <button class="widget-header" onclick="toggleSection(this)">
      <span class="header-title">Book Summaries</span>
      <span class="toggle-icon">▼</span>
    </button>
    <div class="widget-content">
      <div class="content-item"><a href="{{ site.baseurl }}/notes/around-india-in-80-trains/">Around India in 80 Trains</a></div>
      <div class="content-item"><a href="{{ site.baseurl }}/notes/the-man-who-loved-numbers/">📄 The Man who loved Number</a></div>
      <div class="content-item"><a href="{{ site.baseurl }}/notes/monuments-men/">📄 Monuments Men</a></div>
    </div>
  </div>

  <div class="widget-section">
    <button class="widget-header" onclick="toggleSection(this)">
      <span class="header-title">Podcast Notes</span>
      <span class="toggle-icon">▼</span>
    </button>
    <div class="widget-content" style="display: none;">
      <div class="content-item">Podcast Note 1</div>
      <div class="content-item">Podcast Note 2</div>
    </div>
  </div>

  <div class="widget-section">
    <button class="widget-header" onclick="toggleSection(this)">
      <span class="header-title">Concall / Annual Reports</span>
      <span class="toggle-icon">▼</span>
    </button>
    <div class="widget-content" style="display: none;">
      <div class="content-item">Paradeep Phosphate Q2 FY 25/26</div>
      <div class="content-item">Rossari Biotech Q2 FY 25/26</div>
    </div>
  </div>
</div>
<script>
function toggleSection(button) {
  const content = button.nextElementSibling;
  const icon = button.querySelector('.toggle-icon');
  
  if (content.style.display === 'none') {
    content.style.display = 'block';
    icon.style.transform = 'rotate(180deg)';
  } else {
    content.style.display = 'none';
    icon.style.transform = 'rotate(0deg)';
  }
}
</script> -->