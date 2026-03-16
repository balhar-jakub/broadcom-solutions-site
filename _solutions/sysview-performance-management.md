---
title: SYSVIEW Performance Management
tagline: Real-time z/OS system performance monitoring and management via REST API and Zowe CLI.
tags: [api-ml, monitoring, performance, sysview, operations]
api_ml: true
api_ml_details: >-
  SYSVIEW exposes a REST API that can be registered with the API Mediation Layer
  Discovery Service. Zowe CLI commands authenticate through the API ML Gateway,
  enabling SSO and programmatic access to real-time z/OS performance data.
vscode: false
npm_package: "@broadcom/sysview-for-zowe-cli"
docs_url: https://techdocs.broadcom.com/us/en/ca-mainframe-software/performance-management/sysview-performance-management/14-1.html
---

## Overview

**SYSVIEW Performance Management** is Broadcom's real-time performance monitoring and management solution for IBM z/OS. It provides operators and performance engineers with detailed visibility into system resources — CPU, memory, I/O, paging, and more — and allows them to take corrective actions directly from the monitoring interface.

Integration with Zowe allows SYSVIEW data to be accessed programmatically and incorporated into DevOps and AIOps pipelines.

Key capabilities:

- **Real-time monitoring** — live dashboards for CPU utilization, address space activity, I/O rates, and memory usage.
- **Historical trending** — capture and replay performance data over time to identify patterns.
- **Alerts and thresholds** — define alert conditions and automate responses.
- **z/OS console commands** — issue MVS operator commands and view console output.
- **Address space management** — view, start, stop, and manage z/OS address spaces.
- **REST API** — programmatic access to system metrics and console operations.

## API Mediation Layer Integration

The SYSVIEW REST API can be onboarded to the API Mediation Layer:

1. Register the SYSVIEW REST service with the API ML Discovery Service.
2. The API Catalog exposes SYSVIEW's OpenAPI documentation for self-service discovery.
3. SYSVIEW metrics are accessible via the standardized API ML Gateway endpoint.
4. APIML token-based SSO eliminates per-command authentication in CI/CD or scripting contexts.

## Zowe CLI Plugin

```bash
npm install -g @broadcom/sysview-for-zowe-cli
zowe sysview list cpu-utilization
zowe sysview issue command "D A,L"
```

## Product Details

| Field | Value |
|---|---|
| Vendor | Broadcom |
| npm package | `@broadcom/sysview-for-zowe-cli` |
| REST API | Yes — included in product installation |
| Docs | [SYSVIEW TechDocs](https://techdocs.broadcom.com/us/en/ca-mainframe-software/performance-management/sysview-performance-management/14-1.html) |
