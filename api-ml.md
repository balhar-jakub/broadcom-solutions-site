---
layout: default
title: API Mediation Layer Integrations
permalink: /api-ml/
description: Broadcom solutions that integrate with the Zowe API Mediation Layer gateway, discovery service, and API catalog.
---

<!-- Page Hero -->
<div class="page-hero">
  <div class="content-width page-hero-content">
    <span class="page-hero-eyebrow">Integration Catalog</span>
    <h1 class="page-hero-title">API Mediation Layer</h1>
    <p class="page-hero-desc">
      Solutions that integrate with the Zowe API Gateway — enabling single sign-on,
      dynamic service discovery, and standardized OpenAPI documentation for mainframe services.
    </p>
  </div>
  <div class="page-hero-slash"></div>
</div>

<!-- Architecture explainer -->
<div class="site-section section-alt" style="padding: 2.5rem 0 3rem;">
  <div class="content-width">
    <div class="section-header" style="margin-bottom: 1.5rem;">
      <span class="section-eyebrow">Architecture</span>
      <h2 class="section-title">What is the API Mediation Layer?</h2>
      <p class="section-desc">
        The API ML is an open-source, z/OS-hosted gateway built as part of the
        <a href="https://zowe.org" target="_blank" rel="noopener">Zowe</a> project.
        It provides a single point of entry for all mainframe REST APIs.
      </p>
    </div>

    <div class="arch-grid">
      <div class="arch-card">
        <div class="arch-card-icon">🌐</div>
        <h4>API Gateway</h4>
        <p>Reverse proxy — routes client requests to registered microservices via a consistent URL.</p>
      </div>
      <div class="arch-card">
        <div class="arch-card-icon">🗂️</div>
        <h4>Discovery Service</h4>
        <p>Central registry built on Netflix Eureka — services register and deregister dynamically.</p>
      </div>
      <div class="arch-card">
        <div class="arch-card-icon">📋</div>
        <h4>API Catalog</h4>
        <p>Web UI + REST API — browse all registered services and their Swagger/OpenAPI docs.</p>
      </div>
      <div class="arch-card">
        <div class="arch-card-icon">⚡</div>
        <h4>Caching Service</h4>
        <p>Stateless cache backed by Infinispan — enables high-availability Zowe configurations.</p>
      </div>
    </div>

    <div class="info-banner">
      <strong>Key benefits:</strong> Single Sign-On via APIML token &nbsp;·&nbsp;
      Consistent gateway URL regardless of service location &nbsp;·&nbsp;
      High availability with multiple gateway instances &nbsp;·&nbsp;
      TLS-encrypted communication (TLSv1.2+) &nbsp;·&nbsp;
      <a href="https://github.com/zowe/api-layer" target="_blank" rel="noopener">GitHub: zowe/api-layer</a>
    </div>
  </div>
</div>

<!-- Solutions grid -->
<div class="site-section" id="solutions">
  <div class="content-width">
    <div class="section-header">
      <span class="section-eyebrow">Catalog</span>
      <h2 class="section-title">
        <span class="section-title-underline">Solutions with API ML Integration</span>
      </h2>
      <p class="section-desc">
        {% assign apiml_solutions = site.solutions | where: "api_ml", true %}
        {{ apiml_solutions | size }} solutions are verified to integrate with the API Mediation Layer.
      </p>
    </div>

    <div class="card-grid">
      {% assign sorted = site.solutions | where: "api_ml", true | sort: "title" %}
      {% for solution in sorted %}
        {% if solution.vscode %}
          {% assign s_icon = "⚡" %}
          {% assign s_icon_class = "icon-both" %}
        {% else %}
          {% assign s_icon = "🔗" %}
          {% assign s_icon_class = "icon-apiml" %}
        {% endif %}

        <a href="{{ solution.url | relative_url }}" class="solution-card">
          <div class="card-icon {{ s_icon_class }}">{{ s_icon }}</div>
          <div class="card-title">{{ solution.title }}</div>
          <p class="card-desc">{{ solution.tagline }}</p>
          <div class="card-badges">
            <span class="badge badge-apiml">API ML</span>
            {% if solution.vscode %}<span class="badge badge-vscode">VS Code</span>{% endif %}
            {% if solution.npm_package %}<span class="badge badge-cli">CLI</span>{% endif %}
          </div>
          <div class="card-footer">
            <div style="font-size:0.78rem; color:var(--text-faint); line-height:1.4; flex:1;">
              {{ solution.api_ml_details | truncatewords: 12 }}
            </div>
            <span class="card-arrow">→</span>
          </div>
        </a>
      {% endfor %}
    </div>
  </div>
</div>

<!-- Dark CTA -->
<div style="background:linear-gradient(135deg,#0a0e16,#1a2540); position:relative; overflow:hidden;">
  <div style="position:absolute;inset:0;background-image:radial-gradient(circle,rgba(0,152,199,0.12) 1px,transparent 1px);background-size:28px 28px;"></div>
  <div class="content-width" style="padding:3.5rem 0;position:relative;z-index:1;display:flex;align-items:center;justify-content:space-between;flex-wrap:wrap;gap:2rem;">
    <div>
      <h2 style="font-size:1.4rem;font-weight:800;color:#0098C7;margin-bottom:0.4rem;">Onboard your API to the Gateway</h2>
      <p style="color:rgba(255,255,255,0.65);max-width:480px;line-height:1.55;font-size:0.95rem;">
        REST, GraphQL, and WebSocket services can be registered with the Discovery Service
        using Java, Node.js, Python, or static YAML definitions.
      </p>
    </div>
    <a href="https://docs.zowe.org/stable/extend/extend-apiml/onboard-overview"
       target="_blank" rel="noopener" class="btn btn-primary">
      Onboarding Guide →
    </a>
  </div>
</div>
