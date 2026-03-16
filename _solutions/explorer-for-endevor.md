---
title: Explorer for Endevor
tagline: Browse, edit, and manage CA Endevor SCM inventory elements from VS Code.
tags: [vscode, api-ml, scm, endevor, source-control]
api_ml: true
api_ml_details: >-
  Explorer for Endevor connects to Endevor Web Services through the API Mediation
  Layer. It supports API ML base profiles and PassTicket-based token authentication,
  meaning a single API ML SSO token grants access to Endevor without re-entering
  credentials.
vscode: true
marketplace_url: https://marketplace.visualstudio.com/items?itemName=broadcomMFD.explorer-for-endevor
marketplace_publisher: broadcomMFD
github_url: https://github.com/BroadcomMFD/explorer-for-endevor
npm_package: "@broadcom/endevor-for-zowe-cli"
docs_url: https://techdocs.broadcom.com/us/en/ca-mainframe-software/devops/code4z/2-0.html
zowe_conformant: "Zowe Conformant — Explorer for VS Code (V3)"
---

## Overview

Explorer for Endevor brings **CA Endevor Software Change Manager (SCM)** into Visual Studio Code as part of the [Code4z](https://mainframe.broadcom.com/code4z-developer-cockpit) suite. It allows mainframe developers to interact with Endevor inventory locations — stages, environments, systems, subsystems, and elements — without switching to a 3270 terminal or the Endevor web UI.

Highlighted features:

- **Inventory tree view** — navigate the full Endevor hierarchy in the VS Code sidebar.
- **Edit elements in-place** — check out, edit, and generate/submit elements directly from the IDE.
- **History and diff** — view change history and compare element versions side by side.
- **Element actions** — retrieve, add, update, move, delete, and generate Endevor elements.
- **Map-based navigation** — follow Endevor's map structure (from-to stage relationships).
- **Bridge for Git** — works with the [Bridge for Git Explorer](../bridge-for-git-explorer/) to sync Endevor elements into Git repositories.

## API Mediation Layer Integration

Explorer for Endevor communicates with Endevor Web Services. When those services are registered behind the **API ML Gateway**, the extension routes all traffic through the gateway and can use an APIML Authentication Token (PassTicket or JWT) to authenticate. This means:

- No direct credentials stored per-Endevor-connection when using API ML.
- SSO across all Code4z tools that share the same Zowe base profile.
- MFA compatibility through the API ML login flow.

Configure the integration by creating a Zowe team config `base` profile pointing to your API ML instance and referencing it in your Endevor connection profile.

## Zowe CLI Plugin

The companion CLI plugin `@broadcom/endevor-for-zowe-cli` provides the same Endevor operations from the terminal, using the same Zowe profile configuration:

```bash
npm install -g @broadcom/endevor-for-zowe-cli
zowe endevor list elements --environment DEV --system MYSYS --subsystem MYAPP
```

## Extension Details

| Field | Value |
|---|---|
| Publisher | `broadcomMFD` |
| Extension ID | `broadcomMFD.explorer-for-endevor` |
| Part of | Code4z extension pack |
| License | EPL-2.0 |
| Minimum VS Code | 1.79.0 |
