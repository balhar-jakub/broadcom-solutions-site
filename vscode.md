---
layout: default
title: VS Code Extensions
permalink: /vscode/
description: Broadcom mainframe VS Code extensions published under the broadcomMFD and Zowe publishers — Code4z suite and Zowe Explorer.
---

<!-- Page Hero -->
<div class="page-hero">
  <div class="content-width page-hero-content">
    <span class="page-hero-eyebrow">Integration Catalog</span>
    <h1 class="page-hero-title">VS Code Extensions</h1>
    <p class="page-hero-desc">
      Broadcom's Code4z suite and the Zowe Explorer extension bring mainframe
      development — COBOL, HLASM, JCL, debugging, and data management — into
      Visual Studio Code.
    </p>
  </div>
  <div class="page-hero-slash"></div>
</div>

<!-- Code4z info banner -->
<div class="site-section section-alt" style="padding:2.5rem 0 3rem;">
  <div class="content-width">

    <div class="section-header" style="margin-bottom:1.5rem;">
      <span class="section-eyebrow">Publisher</span>
      <h2 class="section-title">Code4z by Broadcom</h2>
      <p class="section-desc">
        Extensions are published under the
        <a href="https://marketplace.visualstudio.com/publishers/broadcomMFD" target="_blank" rel="noopener"><code>broadcomMFD</code></a>
        publisher on the VS Code Marketplace. Install the bundle or pick individual extensions.
      </p>
    </div>

    <div class="card-grid" style="grid-template-columns: repeat(3, 1fr);">

      <div class="solution-card" style="cursor:default;">
        <div class="card-icon icon-vscode">📦</div>
        <div class="card-title">Code4z Extension Pack</div>
        <p class="card-desc">
          Installs all Code4z extensions in a single click.
          The recommended starting point for mainframe developers.
        </p>
        <div class="card-footer">
          <a href="https://marketplace.visualstudio.com/items?itemName=broadcomMFD.code4z-extension-pack"
             target="_blank" rel="noopener" class="btn btn-secondary btn-sm">
            Install Pack
          </a>
        </div>
      </div>

      <div class="solution-card" style="cursor:default;">
        <div class="card-icon" style="background:rgba(0,152,199,0.1);color:#0098C7;width:44px;height:44px;border-radius:3px;display:flex;align-items:center;justify-content:center;font-size:1.3rem;">🌐</div>
        <div class="card-title">Zowe Explorer</div>
        <p class="card-desc">
          Published by the Zowe open-source project. Interact with z/OS
          data sets, USS files, and JES jobs with API ML SSO support.
        </p>
        <div class="card-footer">
          <a href="https://marketplace.visualstudio.com/items?itemName=Zowe.vscode-extension-for-zowe"
             target="_blank" rel="noopener" class="btn btn-secondary btn-sm">
            Marketplace
          </a>
        </div>
      </div>

      <div class="solution-card" style="cursor:default;">
        <div class="card-icon icon-apiml">🔑</div>
        <div class="card-title">API ML + VS Code SSO</div>
        <p class="card-desc">
          Extensions that support API ML base profiles share a single
          sign-on token — no repeated password prompts across tools.
        </p>
        <div class="card-footer">
          <a href="{{ '/api-ml/' | relative_url }}" class="btn btn-secondary btn-sm">
            API ML Integrations
          </a>
        </div>
      </div>

    </div>

    <div class="info-banner" style="margin-top:1.5rem;">
      <strong>Quick install (VS Code CLI):</strong>
      <code style="margin-left:8px; font-size:0.875rem;">code --install-extension broadcomMFD.code4z-extension-pack</code>
    </div>

  </div>
</div>

<!-- Extensions grid -->
<div class="site-section" id="extensions">
  <div class="content-width">

    <div class="section-header">
      <span class="section-eyebrow">Catalog</span>
      <h2 class="section-title">
        <span class="section-title-underline">All VS Code Extensions</span>
      </h2>
      <p class="section-desc">
        {% assign vscode_solutions = site.solutions | where: "vscode", true %}
        {{ vscode_solutions | size }} extensions catalogued.
        Extensions marked with <span class="badge badge-apiml">API ML</span> support API Mediation Layer token authentication.
      </p>
    </div>

    <div class="card-grid">
      {% assign sorted = site.solutions | where: "vscode", true | sort: "title" %}
      {% for solution in sorted %}
        {% if solution.api_ml %}
          {% assign s_icon = "⚡" %}
          {% assign s_icon_class = "icon-both" %}
        {% else %}
          {% assign s_icon = "🧩" %}
          {% assign s_icon_class = "icon-vscode" %}
        {% endif %}

        <a href="{{ solution.url | relative_url }}" class="solution-card">
          <div class="card-icon {{ s_icon_class }}">{{ s_icon }}</div>
          <div class="card-title">{{ solution.title }}</div>
          <p class="card-desc">{{ solution.tagline }}</p>
          <div class="card-badges">
            <span class="badge badge-vscode">VS Code</span>
            {% if solution.api_ml %}<span class="badge badge-apiml">API ML</span>{% endif %}
            {% if solution.zowe_conformant %}<span class="badge badge-conformant">Conformant</span>{% endif %}
          </div>
          <div class="card-footer">
            {% if solution.marketplace_url %}
              <a href="{{ solution.marketplace_url }}" target="_blank" rel="noopener"
                 onclick="event.stopPropagation()"
                 style="font-size:0.75rem; color:var(--link-color);">
                Marketplace ↗
              </a>
            {% endif %}
            <span class="card-arrow">→</span>
          </div>
        </a>
      {% endfor %}
    </div>

  </div>
</div>

<!-- Dark CTA -->
<div style="background:linear-gradient(135deg,#0a0e16,#1a2540);position:relative;overflow:hidden;">
  <div style="position:absolute;inset:0;background-image:radial-gradient(circle,rgba(0,152,199,0.12) 1px,transparent 1px);background-size:28px 28px;"></div>
  <div class="content-width" style="padding:3.5rem 0;position:relative;z-index:1;display:flex;align-items:center;justify-content:space-between;flex-wrap:wrap;gap:2rem;">
    <div>
      <h2 style="font-size:1.4rem;font-weight:800;color:#0098C7;margin-bottom:0.4rem;">Browse the Marketplace</h2>
      <p style="color:rgba(255,255,255,0.65);max-width:480px;line-height:1.55;font-size:0.95rem;">
        All Broadcom mainframe extensions are published at the official
        VS Code Marketplace under the <code style="color:#ccc;">broadcomMFD</code> publisher.
      </p>
    </div>
    <a href="https://marketplace.visualstudio.com/publishers/broadcomMFD"
       target="_blank" rel="noopener" class="btn btn-primary">
      Open Marketplace →
    </a>
  </div>
</div>
