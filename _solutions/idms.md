---
title: CA IDMS
tagline: Network database management for z/OS with REST API integration via API Mediation Layer.
tags: [api-ml, database, idms, network-database]
api_ml: true
api_ml_details: >-
  CA IDMS exposes a REST API that can be registered with the API Mediation Layer
  Discovery Service. The Zowe CLI plugin authenticates through the API ML Gateway
  using an APIML token, enabling SSO access to IDMS from the command line.
vscode: false
npm_package: "@broadcom/idms-for-zowe-cli"
docs_url: https://techdocs.broadcom.com/us/en/ca-mainframe-software/database-management/ca-idms/19-0.html
---

## Server-Side Requirements

CA IDMS integration requires the following components active on z/OS:

1. **CA IDMS** — the database management system itself, including the **IDMS Central Version (CV)**, which is the address space that manages all database activity. The CV must be running for any client or REST API access.
2. **CA IDMS REST API** — a separate API server component included with CA IDMS that exposes IDMS operations over HTTPS. It must be explicitly enabled and configured; it is not started automatically with the CV.

## Overview

**CA IDMS** (Integrated Database Management System) is Broadcom's network database management system for IBM z/OS. It is a high-performance DBMS based on the CODASYL network data model and is widely used in banking, insurance, and government mainframe environments.

Zowe integration provides programmatic access to IDMS operations for automation and DevOps use cases.

Key capabilities:

- **Network data model** — sets, records, and areas organized according to the CODASYL standard.
- **DML and SQL interfaces** — IDMS supports both its native Data Manipulation Language (DML) and a relational SQL interface. The SQL interface operates on IDMS-defined schemas, not arbitrary relational tables.
- **High availability** — active/active clustering for continuous availability.
- **Security** — integration with RACF and other SAF-compliant security products.
- **REST API** — programmatic access to IDMS operations for automation.

## API Mediation Layer Integration

The IDMS REST API can be onboarded to the API Mediation Layer by registering it with the **API ML Discovery Service** (via a static YAML service definition or the Zowe onboarding SDK). Once registered:

- IDMS operations are accessible through the **API ML Gateway** at a consistent endpoint URL.
- CLI operations use **APIML token authentication** — no per-command credentials required.
- The service appears in the **API Catalog** with its OpenAPI documentation.

## Zowe CLI Plugin

The `@broadcom/idms-for-zowe-cli` plugin provides IDMS operations from the command line using the same Zowe profile configuration:

```bash
npm install -g @broadcom/idms-for-zowe-cli
zowe idms list databases
zowe idms get record --database MYDB --record-name EMPLOYEE
```

> **Note:** The CLI plugin uses IDMS's native DML-based operations, not generic SQL SELECT syntax. Consult the [IDMS TechDocs](https://techdocs.broadcom.com/us/en/ca-mainframe-software/database-management/ca-idms/19-0.html) for the full command reference.

## Product Details

| Field | Value |
|---|---|
| Vendor | Broadcom |
| npm package | `@broadcom/idms-for-zowe-cli` |
| REST API | Yes — requires explicit enablement in the IDMS installation |
| Required z/OS component | CA IDMS Central Version (CV) |
| Docs | [IDMS TechDocs](https://techdocs.broadcom.com/us/en/ca-mainframe-software/database-management/ca-idms/19-0.html) |
