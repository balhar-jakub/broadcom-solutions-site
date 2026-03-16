---
title: DBM-Db2 for VS Code
tagline: Manage IBM Db2 for z/OS schemas, objects, and change packages from VS Code.
tags: [vscode, api-ml, db2, database, code4z]
api_ml: true
api_ml_details: >-
  DBM-Db2 for VS Code connects to the DBM for Db2 REST API on z/OS. When that
  service is registered behind the API Mediation Layer, the extension authenticates
  via API ML token, participating in the shared SSO session with other Zowe and
  Code4z tools.
vscode: true
marketplace_url: https://marketplace.visualstudio.com/items?itemName=broadcomMFD.dbm-db2
marketplace_publisher: broadcomMFD
github_url: https://github.com/BroadcomMFD/dbm-db2
npm_package: "@broadcom/dbm-db2-for-zowe-cli"
docs_url: https://techdocs.broadcom.com/us/en/ca-mainframe-software/devops/code4z/2-0.html
---

## Overview

DBM-Db2 for VS Code brings **Broadcom Database Management Solutions for Db2 for z/OS** into Visual Studio Code. It is aimed at Db2 DBAs and developers who want to manage database objects, detect schema drift, and automate change management from a modern IDE.

Key features:

- **Schema browser** — navigate Db2 databases, table spaces, tables, indexes, and views in a tree view.
- **DDL generation** — generate CREATE/ALTER DDL for existing Db2 objects.
- **Change package management** — create and submit Db2 change packages that encapsulate schema alterations.
- **Impact analysis** — understand downstream effects of schema changes before applying them.
- **Compare** — diff current and target schema definitions to detect drift.
- **SQL editor** — write and execute SQL against Db2 for z/OS with syntax highlighting.
- **Deployment tracking** — audit history of schema changes applied to production.

## API Mediation Layer Integration

The DBM for Db2 REST API running on z/OS can be onboarded to the API ML Discovery Service. When registered:

- The VS Code extension addresses Db2 services through the API ML Gateway.
- APIML token authentication replaces per-request credential handling.
- The Db2 service appears in the API Catalog with its OpenAPI documentation.

## CLI Companion

```bash
npm install -g @broadcom/dbm-db2-for-zowe-cli
zowe dbm-db2 list objects --subsystem DSNP --type TABLE
```

## Extension Details

| Field | Value |
|---|---|
| Publisher | `broadcomMFD` |
| Extension ID | `broadcomMFD.dbm-db2` |
| Backend product | Broadcom DBM for Db2 for z/OS |
| License | Broadcom proprietary |
