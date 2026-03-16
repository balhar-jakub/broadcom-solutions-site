---
layout: default
title: VS Code Extensions
permalink: /vscode/
---

<div class="page-intro">
  Broadcom publishes mainframe VS Code extensions under the
  <strong><a href="https://marketplace.visualstudio.com/publishers/broadcomMFD" target="_blank" rel="noopener">broadcomMFD</a></strong>
  publisher as part of the <strong>Code4z</strong> suite. The
  <strong><a href="https://marketplace.visualstudio.com/items?itemName=Zowe.vscode-extension-for-zowe" target="_blank" rel="noopener">Zowe Explorer</a></strong>
  extension is published separately by the Zowe open-source project.
</div>

## Code4z Extension Pack

The [Code4z Extension Pack](https://marketplace.visualstudio.com/items?itemName=broadcomMFD.code4z-extension-pack)
bundles most of the extensions below into a single install. Individual extensions can also be installed separately.

**Install the pack:**
```
ext install broadcomMFD.code4z-extension-pack
```

---

## VS Code Extensions

<div class="catalog-grid">
  {% assign vscode_solutions = site.solutions | where: "vscode", true | sort: "title" %}
  {% for solution in vscode_solutions %}
  <div class="solution-card">
    <h3><a href="{{ solution.url | relative_url }}">{{ solution.title }}</a></h3>
    <p class="card-tagline">{{ solution.tagline }}</p>
    <div class="card-badges">
      <span class="badge badge-vscode">VS Code</span>
      {% if solution.api_ml %}<span class="badge badge-apiml">API ML</span>{% endif %}
    </div>
    {% if solution.marketplace_url %}
    <div>
      <a href="{{ solution.marketplace_url }}" class="btn btn-vscode" target="_blank" rel="noopener" style="font-size:0.78rem; padding:3px 10px;">Marketplace</a>
      {% if solution.github_url %}
      <a href="{{ solution.github_url }}" class="btn btn-github" target="_blank" rel="noopener" style="font-size:0.78rem; padding:3px 10px;">GitHub</a>
      {% endif %}
    </div>
    {% endif %}
    <div class="card-tags">
      {% for tag in solution.tags %}<span class="tag">{{ tag }}</span>{% endfor %}
    </div>
  </div>
  {% endfor %}
</div>

---

**{{ vscode_solutions | size }} VS Code extensions** catalogued &nbsp;·&nbsp;
[VS Code Marketplace — broadcomMFD](https://marketplace.visualstudio.com/publishers/broadcomMFD)
