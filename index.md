---
layout: default
title: Broadcom Mainframe Solutions
---

<!-- ══════════════════════════════════════════════════════════
     HERO
════════════════════════════════════════════════════════════ -->
<div class="site-hero">
  <div class="hero-bg"></div>
  <div class="content-width hero-content">
    <span class="hero-eyebrow">Broadcom Mainframe DevOps</span>
    <h1 class="hero-title">Mainframe Integration Solutions</h1>
    <p class="hero-subtitle">
      Discover Broadcom products that integrate with the Zowe API&nbsp;Mediation
      Layer or extend VS&nbsp;Code for modern mainframe development.
    </p>
    <div class="hero-actions">
      <a href="#solutions" class="btn btn-primary">
        <span>Explore Solutions</span>
        <span class="btn-icon">→</span>
      </a>
      <a href="{{ '/api-ml/' | relative_url }}" class="btn btn-outline">
        API Mediation Layer
      </a>
      <a href="{{ '/vscode/' | relative_url }}" class="btn btn-outline">
        VS Code Extensions
      </a>
    </div>

    <div class="hero-stats">
      <div class="hero-stat">
        <div class="hero-stat-number">{{ site.solutions | size }}</div>
        <div class="hero-stat-label">Solutions</div>
      </div>
      <div class="hero-stat">
        {% assign apiml_count = site.solutions | where: "api_ml", true | size %}
        <div class="hero-stat-number">{{ apiml_count }}</div>
        <div class="hero-stat-label">API ML Integrations</div>
      </div>
      <div class="hero-stat">
        {% assign vscode_count = site.solutions | where: "vscode", true | size %}
        <div class="hero-stat-number">{{ vscode_count }}</div>
        <div class="hero-stat-label">VS Code Extensions</div>
      </div>
    </div>
  </div>
  <div class="hero-slash"></div>
</div>

<!-- ══════════════════════════════════════════════════════════
     QUICK LINKS — matches reference site's top card row
════════════════════════════════════════════════════════════ -->
<div class="site-section section-alt" style="padding: 2.5rem 0;">
  <div class="content-width">
    <div class="card-grid">

      <a href="{{ '/api-ml/' | relative_url }}" class="solution-card">
        <div class="card-icon icon-apiml">🔗</div>
        <div class="card-title">API Mediation Layer</div>
        <p class="card-desc">
          Explore all solutions that integrate with the Zowe API Gateway — single
          sign-on, dynamic service discovery, and OpenAPI documentation.
        </p>
        <div class="card-footer">
          <span class="badge badge-apiml">{{ apiml_count }} solutions</span>
          <span class="card-arrow">→</span>
        </div>
      </a>

      <a href="{{ '/vscode/' | relative_url }}" class="solution-card">
        <div class="card-icon icon-vscode">🧩</div>
        <div class="card-title">VS Code Extensions</div>
        <p class="card-desc">
          Browse the Code4z extension pack and related tools published under the
          <code>broadcomMFD</code> publisher for mainframe development.
        </p>
        <div class="card-footer">
          <span class="badge badge-vscode">{{ vscode_count }} extensions</span>
          <span class="card-arrow">→</span>
        </div>
      </a>

      <a href="https://docs.zowe.org" target="_blank" rel="noopener" class="solution-card">
        <div class="card-icon" style="background:rgba(0,152,199,0.1); color:#0098C7; width:44px; height:44px; border-radius:3px; display:flex; align-items:center; justify-content:center; font-size:1.3rem;">📖</div>
        <div class="card-title">Zowe Documentation</div>
        <p class="card-desc">
          Official technical documentation for the Zowe open-source project —
          API ML, CLI, Explorer, SDKs, and the full component reference.
        </p>
        <div class="card-footer">
          <span style="font-size:0.78rem; color:var(--text-faint);">docs.zowe.org</span>
          <span class="card-arrow">→</span>
        </div>
      </a>

    </div>
  </div>
</div>

<!-- ══════════════════════════════════════════════════════════
     ALL SOLUTIONS — searchable card grid
════════════════════════════════════════════════════════════ -->
<div class="site-section" id="solutions">
  <div class="content-width">

    <div class="section-header">
      <span class="section-eyebrow">Catalog</span>
      <h2 class="section-title">
        <span class="section-title-underline">All Solutions</span>
      </h2>
      <p class="section-desc">
        Each entry below has been verified against official Broadcom and Zowe
        documentation. Use the filter to narrow by name or technology tag.
      </p>
    </div>

    <div class="filter-bar">
      <label for="search">Filter:</label>
      <input
        type="text"
        id="search"
        class="filter-input"
        placeholder="Type a name or tag (e.g. cobol, api-ml, vscode)…"
        oninput="filterSolutions(this.value)"
        aria-label="Filter solutions"
        autocomplete="off"
      >
      <span class="filter-count" id="filter-count">{{ site.solutions | size }} of {{ site.solutions | size }}</span>

      <div style="display:flex; gap:8px; margin-left:auto;">
        <button onclick="filterByTag('api_ml')" class="btn btn-sm" id="btn-apiml"
          style="background:rgba(204,9,47,0.08); color:var(--brand-red); border:1px solid rgba(204,9,47,0.3); border-radius:3px; cursor:pointer; font-size:0.75rem; font-weight:700; padding:5px 12px; letter-spacing:0.04em;">
          API ML only
        </button>
        <button onclick="filterByTag('vscode')" class="btn btn-sm" id="btn-vscode"
          style="background:rgba(0,122,204,0.08); color:#007acc; border:1px solid rgba(0,122,204,0.3); border-radius:3px; cursor:pointer; font-size:0.75rem; font-weight:700; padding:5px 12px; letter-spacing:0.04em;">
          VS Code only
        </button>
        <button onclick="filterByTag('')" class="btn btn-sm" id="btn-all"
          style="background:var(--surface-light); color:var(--text-secondary); border:1px solid var(--divider); border-radius:3px; cursor:pointer; font-size:0.75rem; font-weight:700; padding:5px 12px; letter-spacing:0.04em;">
          Show all
        </button>
      </div>
    </div>

    <div class="card-grid" id="solution-grid">
      {% assign sorted_solutions = site.solutions | sort: "title" %}
      {% for solution in sorted_solutions %}
        {% if solution.api_ml and solution.vscode %}
          {% assign s_icon = "⚡" %}
          {% assign s_icon_class = "icon-both" %}
        {% elsif solution.api_ml %}
          {% assign s_icon = "🔗" %}
          {% assign s_icon_class = "icon-apiml" %}
        {% elsif solution.vscode %}
          {% assign s_icon = "🧩" %}
          {% assign s_icon_class = "icon-vscode" %}
        {% else %}
          {% assign s_icon = "🛠️" %}
          {% assign s_icon_class = "icon-tool" %}
        {% endif %}

      <a href="{{ solution.url | relative_url }}" class="solution-card"
         data-title="{{ solution.title | downcase }}"
         data-tags="{{ solution.tags | join: ' ' | downcase }}"
         data-apiml="{% if solution.api_ml %}true{% else %}false{% endif %}"
         data-vscode="{% if solution.vscode %}true{% else %}false{% endif %}">

        <div class="card-icon {{ s_icon_class }}">{{ s_icon }}</div>

        <div class="card-title">{{ solution.title }}</div>
        <p class="card-desc">{{ solution.tagline }}</p>

        <div class="card-badges">
          {% if solution.api_ml %}<span class="badge badge-apiml">API ML</span>{% endif %}
          {% if solution.vscode %}<span class="badge badge-vscode">VS Code</span>{% endif %}
          {% if solution.npm_package %}<span class="badge badge-cli">CLI</span>{% endif %}
          {% if solution.zowe_conformant %}<span class="badge badge-conformant">Conformant</span>{% endif %}
        </div>

        <div class="card-footer">
          <div style="display:flex; gap:5px; flex-wrap:wrap;">
            {% for tag in solution.tags limit: 3 %}
              <span class="tag">{{ tag }}</span>
            {% endfor %}
          </div>
          <span class="card-arrow">→</span>
        </div>
      </a>
      {% endfor %}
    </div>

    <p id="no-results" style="display:none; text-align:center; padding:3rem 0; color:var(--text-faint);">
      No solutions match your filter. <button onclick="filterByTag('')" style="background:none; border:none; color:var(--brand-red); cursor:pointer; font-weight:700;">Clear filter →</button>
    </p>

  </div>
</div>

<!-- ══════════════════════════════════════════════════════════
     DARK HIGHLIGHT — mirrors reference site's dark CTA band
════════════════════════════════════════════════════════════ -->
<div style="background: linear-gradient(135deg, #0a0e16 0%, #1a2540 60%, #0f1e35 100%); position:relative; overflow:hidden;">
  <div style="position:absolute; inset:0; background-image: radial-gradient(circle, rgba(0,152,199,0.12) 1px, transparent 1px); background-size:28px 28px;"></div>
  <div class="content-width" style="padding: 4rem 0; position:relative; z-index:1; display:flex; align-items:center; justify-content:space-between; flex-wrap:wrap; gap:2rem;">
    <div>
      <h2 style="font-size:1.6rem; font-weight:800; color:#0098C7; margin-bottom:0.5rem;">
        Zowe Conformance Program
      </h2>
      <p style="color:rgba(255,255,255,0.7); max-width:520px; line-height:1.6;">
        Products earning Zowe Conformant status guarantee a high level of
        interoperability, security, and user experience when used alongside
        other Zowe-based tools.
      </p>
    </div>
    <a href="https://www.openmainframeproject.org/our-projects/zowe-conformance-program/"
       target="_blank" rel="noopener" class="btn btn-primary">
      Learn about Conformance →
    </a>
  </div>
</div>

<script>
var activeTagFilter = '';
var totalCount = {{ site.solutions | size }};

function filterSolutions(query) {
  query = query.toLowerCase().trim();
  var cards = document.querySelectorAll('#solution-grid .solution-card');
  var visible = 0;
  cards.forEach(function(card) {
    var titleMatch = (card.dataset.title || '').includes(query);
    var tagsMatch  = (card.dataset.tags  || '').includes(query);
    var tagFilter  = !activeTagFilter
      || (activeTagFilter === 'api_ml'  && card.dataset.apiml  === 'true')
      || (activeTagFilter === 'vscode'  && card.dataset.vscode === 'true');
    var show = (!query || titleMatch || tagsMatch) && tagFilter;
    card.style.display = show ? '' : 'none';
    if (show) visible++;
  });
  document.getElementById('filter-count').textContent = visible + ' of ' + totalCount;
  document.getElementById('no-results').style.display = (visible === 0) ? '' : 'none';
}

function filterByTag(tag) {
  activeTagFilter = tag;
  filterSolutions(document.getElementById('search').value);
}
</script>
