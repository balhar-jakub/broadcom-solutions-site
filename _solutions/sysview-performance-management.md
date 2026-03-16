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

## Server-Side Requirements

SYSVIEW requires:

1. **SYSVIEW Performance Management** installed and running as a started task on z/OS.
2. **SYSVIEW REST API** — included with the SYSVIEW product but must be explicitly enabled and configured with a TCP/IP port before it can accept REST requests.
3. **z/OS security authorization** — certain SYSVIEW capabilities require elevated permissions:
   - **Issuing MVS operator commands** requires the SYSVIEW started task user ID to have the appropriate SAF/RACF `OPERCMDS` class permissions.
   - **Starting or stopping address spaces** requires `MCSOPER` authority or equivalent.
   - Consult your security administrator to grant only the minimum required permissions.

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

The SYSVIEW REST API is onboarded to the API Mediation Layer via a **static YAML service definition**:

1. Create the YAML definition describing the SYSVIEW service endpoint, `serviceId`, and metadata, and place it in the API ML's static definition directory on z/OS.
2. The **API ML Discovery Service** registers SYSVIEW at startup (or on a configuration refresh).
3. The **API Catalog** exposes SYSVIEW's OpenAPI documentation for self-service discovery.
4. SYSVIEW metrics and console operations are accessible via the **standardized API ML Gateway** endpoint.
5. **APIML token-based SSO** eliminates per-command authentication in CI/CD or scripting contexts.

## Zowe CLI Plugin

```bash
npm install -g @broadcom/sysview-for-zowe-cli
zowe sysview list cpu-utilization
```

> **Authorization note:** Commands that issue MVS operator commands (e.g., `D A,L` — Display Active Jobs) require the SYSVIEW user ID to hold `OPERCMDS` authority in RACF or equivalent SAF security product. Confirm with your z/OS security administrator before enabling these operations in automated pipelines.

## Product Details

| Field | Value |
|---|---|
| Vendor | Broadcom |
| npm package | `@broadcom/sysview-for-zowe-cli` |
| REST API | Yes — included in product installation |
| Docs | [SYSVIEW TechDocs](https://techdocs.broadcom.com/us/en/ca-mainframe-software/performance-management/sysview-performance-management/14-1.html) |
