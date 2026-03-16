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

## Overview

**CA IDMS** (Integrated Database Management System) is Broadcom's network database management system for IBM z/OS. It is a high-performance DBMS based on the CODASYL network data model and is widely used in banking, insurance, and government mainframe environments.

Zowe integration provides programmatic access to IDMS operations for automation and DevOps use cases.

Key capabilities:

- **Network data model** — sets, records, and areas organized according to the CODASYL standard.
- **SQL interface** — IDMS also supports an SQL interface alongside the native DML.
- **High availability** — active/active clustering for continuous availability.
- **Security** — integration with RACF and other SAF-compliant security products.
- **REST API** — programmatic access to IDMS operations for automation.

## API Mediation Layer Integration

The IDMS REST API can be onboarded to the API Mediation Layer, making IDMS operations accessible through the standardized API ML Gateway endpoint with APIML token authentication.

## Zowe CLI Plugin

```bash
npm install -g @broadcom/idms-for-zowe-cli
zowe idms run sql --statement "SELECT * FROM EMPLOYEE WHERE DEPT = 'SALES'"
```

## Product Details

| Field | Value |
|---|---|
| Vendor | Broadcom |
| npm package | `@broadcom/idms-for-zowe-cli` |
| REST API | Yes — included in product installation |
| Docs | [IDMS TechDocs](https://techdocs.broadcom.com/us/en/ca-mainframe-software/database-management/ca-idms/19-0.html) |
