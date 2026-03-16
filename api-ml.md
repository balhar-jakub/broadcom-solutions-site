---
layout: default
title: API Mediation Layer Integrations
permalink: /api-ml/
---

<div class="page-intro apiml">
  The <strong>Zowe API Mediation Layer (API ML)</strong> is an open-source gateway,
  discovery service, and API catalog for IBM z/OS mainframe services. The solutions
  below integrate with API ML — routing traffic through the gateway, authenticating
  with APIML tokens, and registering their OpenAPI documentation in the catalog.
</div>

## What is the API Mediation Layer?

The API ML consists of four core components:

| Component | Role |
|---|---|
| **API Gateway** | Reverse proxy — routes client requests to registered microservices |
| **Discovery Service** | Central registry — services register/deregister dynamically (Netflix Eureka) |
| **API Catalog** | Web UI + REST API — browse all registered services and their Swagger docs |
| **Caching Service** | Stateless cache — supports high-availability for Zowe components |

Key benefits for onboarded services:
- **Single Sign-On (SSO)** via APIML Authentication Token
- **Consistent URL** — clients always use the Gateway endpoint regardless of service location
- **High availability** — multiple Gateway instances behind a load balancer
- **OpenAPI documentation** automatically surfaced in the Catalog

**Official docs:** [docs.zowe.org — API Mediation Layer](https://docs.zowe.org/stable/getting-started/overview#api-mediation-layer)  
**GitHub:** [github.com/zowe/api-layer](https://github.com/zowe/api-layer)

---

## Solutions with API ML Integration

<div class="catalog-grid">
  {% assign api_ml_solutions = site.solutions | where: "api_ml", true | sort: "title" %}
  {% for solution in api_ml_solutions %}
  <div class="solution-card">
    <h3><a href="{{ solution.url | relative_url }}">{{ solution.title }}</a></h3>
    <p class="card-tagline">{{ solution.tagline }}</p>
    <div class="card-badges">
      <span class="badge badge-apiml">API ML</span>
      {% if solution.vscode %}<span class="badge badge-vscode">VS Code</span>{% endif %}
    </div>
    <div class="card-tags">
      {% for tag in solution.tags %}<span class="tag">{{ tag }}</span>{% endfor %}
    </div>
  </div>
  {% endfor %}
</div>

---

**{{ api_ml_solutions | size }} solutions** integrate with the API Mediation Layer.
