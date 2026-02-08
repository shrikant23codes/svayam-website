---
layout: default
title: Projects
permalink: /projects/
---

<div class="projects-wrapper">
  <div class="projects-header">
    <h1>Projects</h1>
    <p class="description">Collection of projects I've worked on or am currently working on.</p>
  </div>

  <div class="projects-grid">
    {% for project in site.projects %}
    <div class="project-card">
      <a href="{{ project.url | relative_url }}">
        <div class="project-info">
          <h3>{{ project.title }}</h3>
          <p class="project-description">{{ project.description }}</p>
          <p class="project-tech">{{ project.tech }}</p>
        </div>
      </a>
    </div>
    {% endfor %}
  </div>
</div>

<style>
.projects-wrapper {
  width: 100%;
  padding: 20px;
  box-sizing: border-box;
  max-width: 1200px;
  margin: 0 auto;
}

.projects-header {
  text-align: center;
  margin-bottom: 40px;
}

.projects-header h1 {
  font-size: 2.5em;
  margin: 20px 0;
  font-weight: 700;
}

.description {
  font-size: 1.1em;
  color: #555;
  margin-top: 15px;
}

.projects-grid {
  display: grid;
  /* grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); */
  gap: 30px;
  margin-bottom: 40px;
}

.project-card {
  border: 1px solid #ddd;
  border-radius: 8px;
  padding: 20px;
  transition: transform 0.2s, box-shadow 0.2s;
  background-color: #f9f9f9;
}

.project-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
}

.project-card a {
  text-decoration: none;
  color: inherit;
}

.project-info h3 {
  font-size: 1.3em;
  font-weight: 600;
  margin: 0 0 10px 0;
  color: #333;
}

.project-description {
  font-size: 0.95em;
  color: #666;
  margin: 10px 0;
  line-height: 1.5;
}

.project-tech {
  font-size: 0.85em;
  color: #0066cc;
  margin: 10px 0 0 0;
  font-weight: 500;
}

/* Responsive for tablets */
@media (max-width: 768px) {
  .projects-grid {
    grid-template-columns: repeat(2, 1fr);
    gap: 20px;
  }

  .projects-header h1 {
    font-size: 2em;
  }
}

/* Responsive for mobile */
@media (max-width: 480px) {
  .projects-wrapper {
    padding: 15px;
  }

  .projects-grid {
    grid-template-columns: 1fr;
    gap: 15px;
  }

  .projects-header h1 {
    font-size: 1.8em;
  }
}
</style>
