---
title: Output Management (OM Spool / OM View)
tagline: Manage and distribute z/OS spool output and reports via API Mediation Layer.
tags: [api-ml, output-management, spool, reports, operations]
api_ml: true
api_ml_details: >-
  OM Spool and OM View expose REST APIs that can be registered with the API
  Mediation Layer Discovery Service. Both Zowe CLI plugins authenticate through the
  API ML Gateway using APIML token-based SSO.
vscode: false
docs_url: https://techdocs.broadcom.com/us/en/ca-mainframe-software/devops/ca-view/14-0.html
---

## Overview

Broadcom's **Output Management** solutions handle the capture, storage, distribution, and retrieval of z/OS spool output (JES output) and reports. Two separate Zowe CLI plugins cover distinct aspects of output management:

### OM Spool (`@broadcom/om-spool-for-zowe-cli`)
Focuses on **JES spool management** — retrieving, routing, and managing JES2/JES3 output queues.

- List and filter JES spool output by job name, output class, or destination.
- Retrieve spool data sets and download them locally.
- Route or hold/release spool files.
- Purge spool output programmatically.

### OM View / CA View (`@broadcom/om-view-for-zowe-cli` / `@broadcom/caview-for-zowe-cli`)
Focuses on **report archival and distribution** — managing the CA View/CA Deliver report repository.

- Retrieve archived reports from the CA View repository.
- Search reports by report name, date range, or user ID.
- Download report data for local analysis or redistribution.
- Integrate report retrieval into automated pipelines.

## API Mediation Layer Integration

Both REST APIs (OM Spool and CA View) can be onboarded to the API ML Discovery Service. Once registered:

- The API Gateway proxies all requests using the assigned `serviceId`.
- APIML token authentication provides SSO across all Zowe-integrated tools.
- The API Catalog surfaces the OpenAPI documentation for both services.

## Zowe CLI Plugins

```bash
# OM Spool
npm install -g @broadcom/om-spool-for-zowe-cli
zowe om-spool list output --job-name MYJOB

# OM View / CA View
npm install -g @broadcom/om-view-for-zowe-cli
zowe ca-view get report --report-name MONTHLY-SALES
```

## Product Details

| Field | Value |
|---|---|
| Vendor | Broadcom |
| npm packages | `@broadcom/om-spool-for-zowe-cli`, `@broadcom/om-view-for-zowe-cli`, `@broadcom/caview-for-zowe-cli` |
| Backend products | CA OM for z/OS, CA View, CA Deliver |
| Docs | [CA View TechDocs](https://techdocs.broadcom.com/us/en/ca-mainframe-software/devops/ca-view/14-0.html) |
