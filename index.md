---
layout: default
title: Home
---

<div class="page-intro">
  A catalog of <strong>Broadcom mainframe solutions</strong> that integrate with the
  <strong>Zowe API Mediation Layer</strong> or provide a <strong>VS Code extension</strong>
  for modern mainframe development.
</div>

## All Solutions

<div class="filter-bar">
  <label for="search">Filter:</label>
  <input type="text" id="search" placeholder="Search by name or tag..." oninput="filterCards(this.value)">
</div>

<div class="catalog-grid" id="catalog-grid">
  {% assign sorted = site.solutions | sort: "title" %}
  {% for solution in sorted %}
  <div class="solution-card" data-title="{{ solution.title | downcase }}" data-tags="{{ solution.tags | join: ' ' | downcase }}">
    <h3><a href="{{ solution.url | relative_url }}">{{ solution.title }}</a></h3>
    <p class="card-tagline">{{ solution.tagline }}</p>
    <div class="card-badges">
      {% if solution.api_ml %}<span class="badge badge-apiml">API ML</span>{% endif %}
      {% if solution.vscode %}<span class="badge badge-vscode">VS Code</span>{% endif %}
    </div>
    <div class="card-tags">
      {% for tag in solution.tags %}<span class="tag">{{ tag }}</span>{% endfor %}
    </div>
  </div>
  {% endfor %}
</div>

<script>
function filterCards(query) {
  query = query.toLowerCase().trim();
  document.querySelectorAll('.solution-card').forEach(function(card) {
    var title = card.dataset.title || '';
    var tags  = card.dataset.tags  || '';
    card.style.display = (!query || title.includes(query) || tags.includes(query)) ? '' : 'none';
  });
}
</script>

---

**{{ site.solutions | size }} solutions** catalogued &nbsp;·&nbsp;
[API ML integrations]({{ '/api-ml' | relative_url }}) &nbsp;·&nbsp;
[VS Code extensions]({{ '/vscode' | relative_url }})
