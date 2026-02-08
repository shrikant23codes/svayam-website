---
layout: default
title: Bookshelf
permalink: /bookshelf/
---

<div class="bookshelf-wrapper">
  <div class="bookshelf-header">
    <h1>Bookshelf</h1>
    <p class="last-updated">(Last updated: 12 Oct 2025)</p>
    <p class="description">Books that I have read or am currently reading.</p>
  </div>

  <h2>Books Read</h2>
  <div class="books-grid">
    <div class="book-card">
      <div class="book-info">
        <h3>Around India in 80 Trains</h3>
        <p class="author">Author Name</p>
        <p class="year">2024</p>
      </div>
    </div>

    <div class="book-card">
      <div class="book-info">
        <h3>Book Title 2</h3>
        <p class="author">Author Name</p>
        <p class="year">2024</p>
      </div>
    </div>

    <div class="book-card">
      <div class="book-info">
        <h3>Book Title 3</h3>
        <p class="author">Author Name</p>
        <p class="year">2024</p>
      </div>
    </div>

    <div class="book-card">
      <div class="book-info">
        <h3>Book Title 4</h3>
        <p class="author">Author Name</p>
        <p class="year">2024</p>
      </div>
    </div>
  </div>
</div>

<style>
.bookshelf-wrapper {
  width: 100%;
  padding: 20px;
  box-sizing: border-box;
  max-width: 1200px;
  margin: 0 auto;
}

.bookshelf-header {
  text-align: center;
  margin-bottom: 40px;
}

.bookshelf-header h1 {
  font-size: 2.5em;
  margin: 20px 0;
  font-weight: 700;
}

.last-updated {
  font-size: 0.9em;
  color: #666;
  margin: 0;
  padding: 0;
}

.description {
  font-size: 1.1em;
  color: #555;
  margin-top: 15px;
}

.bookshelf-wrapper h2 {
  font-size: 1.8em;
  font-weight: 600;
  margin-bottom: 30px;
  margin-top: 40px;
}

.books-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 30px;
  margin-bottom: 40px;
}

.book-card {
  text-align: center;
  transition: transform 0.2s, box-shadow 0.2s;
  border: 1px solid #ddd;
  border-radius: 8px;
  padding: 15px;
}

.book-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
}

.book-cover {
  width: 100%;
  aspect-ratio: 2/3;
  margin-bottom: 15px;
  border-radius: 8px;
  overflow: hidden;
  background-color: #f0f0f0;
  border: 1px solid #ddd;
}

.book-cover img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.book-info h3 {
  font-size: 1.1em;
  font-weight: 600;
  margin: 10px 0 5px 0;
  color: #333;
  line-height: 1.3;
}

.book-info .author {
  font-size: 0.95em;
  color: #888;
  margin: 5px 0;
}

.book-info .year {
  font-size: 0.9em;
  color: #aaa;
  margin: 5px 0 0 0;
}

/* Responsive for tablets */
@media (max-width: 768px) {
  .books-grid {
    grid-template-columns: repeat(auto-fill, minmax(150px, 1fr));
    gap: 20px;
  }

  .bookshelf-header h1 {
    font-size: 2em;
  }

  .bookshelf-wrapper h2 {
    font-size: 1.5em;
  }
}

/* Responsive for mobile */
@media (max-width: 480px) {
  .bookshelf-wrapper {
    padding: 15px;
  }

  .books-grid {
    grid-template-columns: repeat(auto-fill, minmax(120px, 1fr));
    gap: 15px;
  }

  .bookshelf-header h1 {
    font-size: 1.8em;
  }

  .bookshelf-wrapper h2 {
    font-size: 1.3em;
  }
}
</style>