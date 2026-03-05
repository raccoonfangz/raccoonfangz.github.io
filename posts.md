---
layout: default
title: "Posts"
permalink: /posts/
---

<section class="posts-archive" style="margin-top: .5rem;">

  <h3>Archive</h3>

  <div id="search-container" style="margin:0.6rem 0 1rem 0; user-select:none;">
    <input type="text" id="searchInput" placeholder="Search posts..."
      style="display:block; width:200px; max-width:90%; padding:0.4rem 0.6rem;
             border:2px solid var(--heading-color); border-radius:5px;
             font-family: var(--font-secondary); font-size:0.95rem;
             background-color: var(--background-color); color: var(--text-color);
             outline:none;">
  </div>

  <div style="margin-bottom: .75rem;">
    <strong>Total posts:</strong> <span id="post-count">—</span>
  </div>

  <p style="margin-top:0;"><strong>Most recent post:</strong> <span id="last-posted">—</span> ago</p>

  <!-- FICTION POSTS (collapsed by default) -->
  {% assign fiction_posts = site.tags.fiction %}
  {% if fiction_posts %}
  <details class="tag-group" data-tag="fiction" style="user-select:none;">
    <summary style="cursor:pointer; font-weight:bold; font-size:1.05rem; margin:.8rem 0;">#fiction</summary>
    <ul class="embedded blog-posts" aria-label="Posts tagged fiction">
      {% for post in fiction_posts %}
      <li style="user-select:none;">
        <span><i>
          {% if post.date %}
            <time datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: "%d %B, %Y" }}</time>
          {% else %}
            <time>—</time>
          {% endif %}
        </i></span>
        <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
      </li>
      {% endfor %}
    </ul>
  </details>
  {% endif %}

    <!-- 2026 POSTS -->
  <details open class="tag-group" data-tag="2026" style="user-select:none;">
    <summary style="cursor:pointer; font-weight:bold; font-size:1.05rem; margin:.8rem 0;">#2026</summary>
    <ul class="embedded blog-posts" aria-label="Posts from 2025">
      {% for post in site.posts %}
        {% assign post_date = post.date | date: "%Y-%m-%d" %}
        {% if post_date >= "2026-01-01" and post_date < "2027-01-01" %}
          <li style="user-select:none;">
            <span><i><time datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: "%d %B, %Y" }}</time></i></span>
            <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
          </li>
        {% endif %}
      {% endfor %}
    </ul>
  </details>

  <!-- 2025 POSTS -->
  <details open class="tag-group" data-tag="2025" style="user-select:none;">
    <summary style="cursor:pointer; font-weight:bold; font-size:1.05rem; margin:.8rem 0;">#2025</summary>
    <ul class="embedded blog-posts" aria-label="Posts from 2025">
      {% for post in site.posts %}
        {% assign post_date = post.date | date: "%Y-%m-%d" %}
        {% if post_date >= "2025-01-01" and post_date < "2026-01-01" %}
          <li style="user-select:none;">
            <span><i><time datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: "%d %B, %Y" }}</time></i></span>
            <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
          </li>
        {% endif %}
      {% endfor %}
    </ul>
  </details>

  <div id="blog-age" style="margin-top:1.25rem;"></div>
</section>


<script>
document.addEventListener("DOMContentLoaded", function () {
  const searchInput = document.getElementById('searchInput');
  const countEl = document.getElementById('post-count');
  const lastPostedEl = document.getElementById('last-posted');
  const blogAgeEl = document.getElementById('blog-age');

  function updateCount() {
    const allPostItems = Array.from(document.querySelectorAll('ul.blog-posts li'));
    const visible = allPostItems.filter(li => li.offsetParent !== null);
    countEl.textContent = visible.length;
  }

  function timeAgo(date) {
    if (!(date instanceof Date) || isNaN(date)) return 'unknown';
    const s = Math.floor((Date.now() - date.getTime()) / 1000);
    if (s < 60) return s + ' seconds';
    const m = Math.floor(s / 60);
    if (m < 60) return m + ' minutes';
    const h = Math.floor(m / 60);
    if (h < 24) return h + ' hours';
    const d = Math.floor(h / 24);
    return d + ' days';
  }

  // Blog age
  (function setBlogAge() {
    const creationDate = new Date(2025, 5, 20); // June = 5
    const days = Math.floor((Date.now() - creationDate.getTime()) / (1000*60*60*24));
    blogAgeEl.innerHTML = "<strong>Blog created:</strong> " + days + " days ago";
  })();

  // Last post
  {% assign last_post = site.posts | sort: 'date' | last %}
  {% if last_post %}
  (function setLastPost() {
    const iso = "{{ last_post.date | date: '%Y-%m-%dT%H:%M:%SZ' }}";
    const d = new Date(iso);
    lastPostedEl.textContent = timeAgo(d);
  })();
  {% else %}
  lastPostedEl.textContent = "No posts yet";
  {% endif %}

  // Initial count
  updateCount();

  const detailsEls = Array.from(document.querySelectorAll('details.tag-group'));
  searchInput.addEventListener('input', function () {
    const q = this.value.trim().toLowerCase();
    detailsEls.forEach(details => {
      const lis = Array.from(details.querySelectorAll('ul.blog-posts li'));
      let anyMatch = false;
      lis.forEach(li => {
        const text = li.textContent.toLowerCase();
        const match = text.includes(q);
        li.style.display = match ? "" : "none";
        if (match) anyMatch = true;
      });
      details.open = q && anyMatch;
    });
    updateCount();
  });
});
</script>
