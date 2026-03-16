---
title: DBM-Db2 for VS Code
tagline: Manage IBM Db2 for z/OS schemas, objects, and change packages from VS Code.
tags: [vscode, api-ml, db2, database, code4z]
api_ml: true
api_ml_details: >-
  DBM-Db2 for VS Code connects to the Broadcom DBM for Db2 for z/OS REST API. When
  that service is registered with the API Mediation Layer Discovery Service, the
  extension authenticates via an APIML token, participating in the shared SSO
  session with other Zowe and Code4z tools.
vscode: true
marketplace_url: https://marketplace.visualstudio.com/items?itemName=broadcomMFD.dbm-db2
marketplace_publisher: broadcomMFD
github_url: https://github.com/BroadcomMFD/dbm-db2
npm_package: "@broadcom/dbm-db2-for-zowe-cli"
docs_url: https://techdocs.broadcom.com/us/en/ca-mainframe-software/devops/code4z/2-0.html
---

## Server-Side Requirements

DBM-Db2 for VS Code requires:

1. **IBM Db2 for z/OS** — the target database subsystem must be installed, configured, and running. The extension manages Db2 objects and schemas; Db2 itself is the underlying database engine.
2. **Broadcom DBM for Db2 for z/OS** (also referred to as **Broadcom Database Management Solutions for Db2 for z/OS**) — the Broadcom product that provides the REST API and change management engine. This must be installed and its REST API service must be started as a z/OS address space.

The VS Code extension and CLI plugin connect to the **Broadcom DBM for Db2 REST API**, not directly to the Db2 subsystem.

## Overview

DBM-Db2 for VS Code is part of the [Code4z](https://mainframe.broadcom.com/code4z-developer-cockpit) suite. It is aimed at Db2 DBAs and developers who want to manage database objects, detect schema drift, and automate change management from a modern IDE — all backed by **Broadcom DBM for Db2 for z/OS**.

Key features:

- **Schema browser** — navigate Db2 databases, table spaces, tables, indexes, and views in a tree view.
- **DDL generation** — generate CREATE/ALTER DDL for existing Db2 objects.
- **Change package management** — create and submit Db2 change packages that encapsulate schema alterations.
- **Impact analysis** — understand downstream effects of schema changes before applying them.
- **Compare** — diff current and target schema definitions to detect drift.
- **SQL editor** — write and execute SQL against Db2 for z/OS with syntax highlighting.
- **Deployment tracking** — audit history of schema changes applied to production.

## API Mediation Layer Integration

The **Broadcom DBM for Db2 REST API** running on z/OS can be onboarded to the API ML Discovery Service (via static YAML or Zowe onboarding SDK). When registered:

- The VS Code extension and CLI plugin address the Db2 service through the **API ML Gateway**.
- **APIML token authentication** replaces per-request credential handling.
- The service appears in the **API Catalog** with its OpenAPI documentation.

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
| Also requires | IBM Db2 for z/OS subsystem |
| License | Broadcom proprietary |
