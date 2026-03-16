---
title: Output Management (OM Spool / CA View)
tagline: Manage z/OS JES spool output and archived reports programmatically via API Mediation Layer.
tags: [api-ml, output-management, spool, reports, operations]
api_ml: true
api_ml_details: >-
  CA OM for z/OS (OM Spool) and CA View expose REST APIs that can be registered
  with the API Mediation Layer Discovery Service. The Zowe CLI plugins authenticate
  through the API ML Gateway using APIML token-based SSO.
vscode: false
docs_url: https://techdocs.broadcom.com/us/en/ca-mainframe-software/devops/ca-view/14-0.html
---

## Server-Side Requirements

This page covers two separate Broadcom output management products, each with its own backend:

### OM Spool — CA OM for z/OS
- **CA OM for z/OS** must be installed and running as a started task.
- The **OM Spool REST API** is a component of CA OM for z/OS and must be explicitly enabled. It provides access to the JES2/JES3 spool queue.

### OM View — CA View / CA Deliver
- **CA View** must be installed and running. CA View manages the capture and storage of archived report data from the JES output stream.
- **CA Deliver** (optional companion product) handles automated report distribution rules; it is not required solely for REST API access to CA View.
- The **CA View REST API** is included with the CA View installation and must be enabled.

> **Note on package naming:** The npm package `@broadcom/om-view-for-zowe-cli` and `@broadcom/caview-for-zowe-cli` target the same CA View backend — `caview` is the older package name and `om-view` is the current name. Use `@broadcom/om-view-for-zowe-cli` for new installations.

## Overview

Broadcom's Output Management solutions handle the capture, storage, distribution, and retrieval of z/OS spool output (JES output) and archived reports. Two Zowe CLI plugins address distinct aspects of output management:

### OM Spool (`@broadcom/om-spool-for-zowe-cli`)

Focuses on **live JES spool management** — interacting with the active JES2/JES3 output queue via the CA OM for z/OS REST API.

- List and filter JES spool output by job name, output class, or destination.
- Retrieve spool data sets and download them locally.
- Hold, release, or route spool files.
- Purge spool output programmatically.

### CA View (`@broadcom/om-view-for-zowe-cli`)

Focuses on **archived report retrieval** — accessing the CA View report repository of captured and stored output.

- Retrieve archived reports from the CA View repository.
- Search reports by report name, date range, or user ID.
- Download report data for local analysis or redistribution.
- Integrate report retrieval into automated pipelines.

## API Mediation Layer Integration

Each REST API (OM Spool and CA View) is onboarded to the API ML **independently**, each with its own `serviceId` registered with the Discovery Service. Once registered:

- The **API Gateway** proxies requests to the appropriate backend using each service's `serviceId`.
- **APIML token authentication** provides SSO across all Zowe-integrated tools.
- The **API Catalog** surfaces the OpenAPI documentation for each service separately.

## Zowe CLI Plugins

```bash
# OM Spool — live JES spool access via CA OM for z/OS
npm install -g @broadcom/om-spool-for-zowe-cli
zowe om-spool list output --job-name MYJOB

# CA View — archived report access
npm install -g @broadcom/om-view-for-zowe-cli
zowe ca-view get report --report-name MONTHLY-SALES
```

## Product Details

| Field | Value |
|---|---|
| Vendor | Broadcom |
| OM Spool package | `@broadcom/om-spool-for-zowe-cli` |
| CA View package | `@broadcom/om-view-for-zowe-cli` (replaces legacy `@broadcom/caview-for-zowe-cli`) |
| OM Spool backend | CA OM for z/OS |
| CA View backend | CA View (CA Deliver optional) |
| CA View Docs | [CA View TechDocs](https://techdocs.broadcom.com/us/en/ca-mainframe-software/devops/ca-view/14-0.html) |
| CA OM Docs | [CA OM TechDocs](https://techdocs.broadcom.com/us/en/ca-mainframe-software/devops/ca-output-management-for-zos/12-0.html) |
