---
title: Mainframe Application Tuner (MAT)
tagline: Performance analysis and tuning for z/OS applications via REST API and Zowe CLI.
tags: [api-ml, performance, tuning, monitoring, mat]
api_ml: true
api_ml_details: >-
  MAT exposes REST APIs (MAT Detect and MAT Analyze) that can be registered with
  the API Mediation Layer Discovery Service. Zowe CLI operations authenticate
  through the API ML Gateway, supporting SSO across all Broadcom Zowe integrations.
vscode: false
npm_package: "@broadcom/mat-detect-for-zowe-cli"
docs_url: https://techdocs.broadcom.com/us/en/ca-mainframe-software/devops/mainframe-application-tuner/11-5.html
---

## Overview

**Broadcom Mainframe Application Tuner (MAT)** is a performance measurement and tuning tool for z/OS applications. It collects CPU, I/O, memory, and wait-time data from running programs and provides actionable analysis to identify and resolve performance bottlenecks.

Zowe integration allows performance data to be accessed programmatically, incorporated into CI/CD pipelines, and consumed by DevOps tooling outside the mainframe.

Key capabilities:

- **Performance monitoring** — collect execution profiles for COBOL, PL/I, Assembler, and Java programs.
- **CPU / I/O analysis** — identify hot paths, expensive instructions, and I/O wait contributors.
- **Comparative analysis** — compare performance between code versions (pre/post change).
- **SLA compliance** — track whether workloads meet defined performance targets.
- **REST APIs** — two API surfaces:
  - **MAT Detect API** — detect performance anomalies and retrieve measurement data.
  - **MAT Analyze API** — deep-dive analysis of collected performance profiles.

## API Mediation Layer Integration

Both MAT Detect and MAT Analyze REST services can be onboarded to the API ML. Once registered:

- Services appear in the API Catalog with OpenAPI documentation.
- The API Gateway routes requests to MAT using the assigned `serviceId`.
- CLI operations use APIML token authentication — no per-command credentials required.

## Zowe CLI Plugins

```bash
# Anomaly detection and monitoring
npm install -g @broadcom/mat-detect-for-zowe-cli
zowe mat-detect get-profile --profile MYPROG

# Deep-dive analysis
npm install -g @broadcom/mat-analyze-for-zowe-cli
zowe mat-analyze get-report --profile MYPROG --type CPU
```

## Product Details

| Field | Value |
|---|---|
| Vendor | Broadcom |
| npm packages | `@broadcom/mat-detect-for-zowe-cli`, `@broadcom/mat-analyze-for-zowe-cli` |
| REST APIs | MAT Detect API, MAT Analyze API |
| Docs | [MAT TechDocs](https://techdocs.broadcom.com/us/en/ca-mainframe-software/devops/mainframe-application-tuner/11-5.html) |
