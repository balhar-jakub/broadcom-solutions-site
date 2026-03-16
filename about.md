---
layout: default
title: About This Catalog
permalink: /about/
---

<!-- Page Hero -->
<div class="page-hero">
  <div class="content-width page-hero-content">
    <span class="page-hero-eyebrow">About</span>
    <h1 class="page-hero-title">About This Catalog</h1>
    <p class="page-hero-desc">
      A reference catalog of Broadcom mainframe solutions that integrate with the
      Zowe API Mediation Layer or provide a VS Code extension for modern mainframe development.
    </p>
  </div>
  <div class="page-hero-slash"></div>
</div>

<div class="site-section">
  <div class="content-width" style="max-width: 860px;">

    <div class="info-banner">
      This catalog is independently maintained for reference and educational purposes.
      All product information is sourced from official Broadcom TechDocs, GitHub repositories,
      the VS Code Marketplace, and the Zowe documentation site.
    </div>

    <h2 style="font-size:1.3rem; font-weight:800; margin:2rem 0 1rem; padding-bottom:6px; border-bottom:2px solid var(--divider);">
      What's included
    </h2>
    <p style="color:var(--text-secondary); line-height:1.65; margin-bottom:1rem;">
      A solution is included in this catalog if it meets <strong>at least one</strong> of the following criteria:
    </p>
    <ul style="margin:0 0 1.5rem 1.5rem; color:var(--text-secondary); line-height:1.8;">
      <li><strong>API Mediation Layer integration</strong> — the product registers a REST API behind the Zowe API Gateway, uses APIML token authentication, or has earned a Zowe Conformance badge for API ML.</li>
      <li><strong>VS Code extension</strong> — the product provides an extension published under the <code>broadcomMFD</code> or <code>Zowe</code> publisher on the VS Code Marketplace.</li>
    </ul>

    <h2 style="font-size:1.3rem; font-weight:800; margin:2rem 0 1rem; padding-bottom:6px; border-bottom:2px solid var(--divider);">
      Sources
    </h2>

    <table class="data-table">
      <thead>
        <tr><th>Source</th><th>URL</th><th>Used for</th></tr>
      </thead>
      <tbody>
        <tr>
          <td>Zowe Documentation</td>
          <td><a href="https://docs.zowe.org" target="_blank" rel="noopener">docs.zowe.org</a></td>
          <td>API ML architecture, component descriptions, onboarding guides</td>
        </tr>
        <tr>
          <td>API Layer (GitHub)</td>
          <td><a href="https://github.com/zowe/api-layer" target="_blank" rel="noopener">github.com/zowe/api-layer</a></td>
          <td>Technical specification and changelog</td>
        </tr>
        <tr>
          <td>Zowe Explorer (GitHub)</td>
          <td><a href="https://github.com/zowe/zowe-explorer-vscode" target="_blank" rel="noopener">github.com/zowe/zowe-explorer-vscode</a></td>
          <td>Extension features and API ML integration details</td>
        </tr>
        <tr>
          <td>BroadcomMFD (GitHub)</td>
          <td><a href="https://github.com/BroadcomMFD" target="_blank" rel="noopener">github.com/BroadcomMFD</a></td>
          <td>Code4z extension source, README descriptions</td>
        </tr>
        <tr>
          <td>VS Code Marketplace</td>
          <td><a href="https://marketplace.visualstudio.com/publishers/broadcomMFD" target="_blank" rel="noopener">marketplace.visualstudio.com/publishers/broadcomMFD</a></td>
          <td>Extension IDs, install counts, publisher metadata</td>
        </tr>
        <tr>
          <td>npm Registry</td>
          <td><a href="https://www.npmjs.com/~broadcom-mbauto" target="_blank" rel="noopener">npmjs.com/~broadcom-mbauto</a></td>
          <td>Zowe CLI plugin package names and descriptions</td>
        </tr>
        <tr>
          <td>Broadcom TechDocs — Code4z</td>
          <td><a href="https://techdocs.broadcom.com/us/en/ca-mainframe-software/devops/code4z/2-0.html" target="_blank" rel="noopener">techdocs.broadcom.com</a></td>
          <td>Official product documentation</td>
        </tr>
        <tr>
          <td>Zowe Conformance Program</td>
          <td><a href="https://www.openmainframeproject.org/our-projects/zowe-conformance-program/" target="_blank" rel="noopener">openmainframeproject.org</a></td>
          <td>Conformance badge data and certification categories</td>
        </tr>
      </tbody>
    </table>

    <h2 style="font-size:1.3rem; font-weight:800; margin:2rem 0 1rem; padding-bottom:6px; border-bottom:2px solid var(--divider);">
      Zowe Conformance Program
    </h2>
    <p style="color:var(--text-secondary); line-height:1.65; margin-bottom:1rem;">
      The <a href="https://www.openmainframeproject.org/our-projects/zowe-conformance-program/" target="_blank" rel="noopener">Zowe Conformance Program</a>
      certifies ISV products in four categories. Solutions in this catalog that have earned
      a badge show a <span class="badge badge-conformant">Conformant</span> label on their detail page.
    </p>

    <div class="card-grid" style="grid-template-columns:repeat(2,1fr); gap:1rem; margin-bottom:2rem;">
      <div style="padding:1rem 1.2rem; border:1px solid var(--divider); border-radius:6px; background:var(--surface-light);">
        <div style="font-weight:700; margin-bottom:4px; font-size:0.9rem;">🔗 API Mediation Layer</div>
        <p style="font-size:0.82rem; color:var(--text-muted); margin:0; line-height:1.5;">Product integrates correctly with the API ML gateway, discovery, and catalog.</p>
      </div>
      <div style="padding:1rem 1.2rem; border:1px solid var(--divider); border-radius:6px; background:var(--surface-light);">
        <div style="font-weight:700; margin-bottom:4px; font-size:0.9rem;">🖥️ App Framework</div>
        <p style="font-size:0.82rem; color:var(--text-muted); margin:0; line-height:1.5;">Product provides a plug-in for the Zowe Desktop web application framework.</p>
      </div>
      <div style="padding:1rem 1.2rem; border:1px solid var(--divider); border-radius:6px; background:var(--surface-light);">
        <div style="font-weight:700; margin-bottom:4px; font-size:0.9rem;">⌨️ CLI</div>
        <p style="font-size:0.82rem; color:var(--text-muted); margin:0; line-height:1.5;">Product provides a conformant Zowe CLI plug-in using the Imperative framework.</p>
      </div>
      <div style="padding:1rem 1.2rem; border:1px solid var(--divider); border-radius:6px; background:var(--surface-light);">
        <div style="font-weight:700; margin-bottom:4px; font-size:0.9rem;">🧩 Explorer for VS Code</div>
        <p style="font-size:0.82rem; color:var(--text-muted); margin:0; line-height:1.5;">Product provides a conformant VS Code extension or Zowe Explorer integration.</p>
      </div>
    </div>

    <h2 style="font-size:1.3rem; font-weight:800; margin:2rem 0 1rem; padding-bottom:6px; border-bottom:2px solid var(--divider);">
      About Zowe
    </h2>
    <p style="color:var(--text-secondary); line-height:1.65; margin-bottom:1rem;">
      <a href="https://zowe.org" target="_blank" rel="noopener">Zowe</a> is an open-source project
      hosted by the <a href="https://openmainframeproject.org" target="_blank" rel="noopener">Open Mainframe Project</a>
      (Linux Foundation). Broadcom is a founding sponsor and primary contributor.
    </p>

    <div class="highlight-box">
      <h2 style="font-size:1.15rem; margin-bottom:1rem;">Zowe Core Components</h2>
      <table class="data-table" style="background:transparent;">
        <thead>
          <tr>
            <th style="background:rgba(255,255,255,0.05); color:rgba(255,255,255,0.6);">Component</th>
            <th style="background:rgba(255,255,255,0.05); color:rgba(255,255,255,0.6);">Type</th>
            <th style="background:rgba(255,255,255,0.05); color:rgba(255,255,255,0.6);">Description</th>
          </tr>
        </thead>
        <tbody>
          <tr><td style="color:rgba(255,255,255,0.8);">API Mediation Layer</td><td style="color:rgba(255,255,255,0.5);">Server</td><td style="color:rgba(255,255,255,0.65);">Gateway, Discovery Service, API Catalog, Caching Service</td></tr>
          <tr><td style="color:rgba(255,255,255,0.8);">Zowe Application Framework</td><td style="color:rgba(255,255,255,0.5);">Server</td><td style="color:rgba(255,255,255,0.65);">Web desktop with pluggable z/OS applications</td></tr>
          <tr><td style="color:rgba(255,255,255,0.8);">Zowe CLI</td><td style="color:rgba(255,255,255,0.5);">Client</td><td style="color:rgba(255,255,255,0.65);">Command-line interface to z/OS; extensible via plug-ins</td></tr>
          <tr><td style="color:rgba(255,255,255,0.8);">Zowe Explorer</td><td style="color:rgba(255,255,255,0.5);">Client</td><td style="color:rgba(255,255,255,0.65);">VS Code extension for data sets, USS files, and JES jobs</td></tr>
          <tr><td style="color:rgba(255,255,255,0.8);">Client SDKs</td><td style="color:rgba(255,255,255,0.5);">Client</td><td style="color:rgba(255,255,255,0.65);">Node.js, Java, Kotlin, Python programmatic APIs</td></tr>
        </tbody>
      </table>
    </div>

  </div>
</div>
