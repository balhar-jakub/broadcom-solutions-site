---
title: Explorer for Endevor
tagline: Browse, edit, and manage CA Endevor SCM inventory elements from VS Code.
tags: [vscode, api-ml, scm, endevor, source-control]
api_ml: true
api_ml_details: >-
  Explorer for Endevor connects to Endevor Web Services through the API Mediation
  Layer. It supports API ML base profiles: the client authenticates to the API ML
  Gateway and receives a JWT (apimlAuthenticationToken), which is then used for all
  subsequent requests. The API ML internally uses PassTickets to authenticate to
  Endevor Web Services on the client's behalf.
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

## Server-Side Requirements

Explorer for Endevor requires two server-side components on z/OS:

1. **CA Endevor SCM** — the mainframe source control manager and its inventory database.
2. **Endevor Web Services** — the REST API layer that exposes Endevor operations over HTTPS. This must be deployed and running as a separate web application (typically on a Liberty or Tomcat server on z/OS) before the VS Code extension can connect.

When Endevor Web Services is registered with the **API ML Discovery Service**, it is accessible through the API ML Gateway at a consistent URL. Without API ML, the extension connects directly to the Endevor Web Services host and port.

## API Mediation Layer Integration

Explorer for Endevor communicates with Endevor Web Services through the **API ML Gateway** when a Zowe `base` profile is configured. The authentication flow is:

1. The client (VS Code / Zowe CLI) authenticates to the API ML Gateway with a username and password and receives a **JWT** (`apimlAuthenticationToken`).
2. All subsequent requests to Endevor Web Services are routed through the Gateway, carrying this JWT.
3. The API ML Gateway internally generates a **PassTicket** and passes it to Endevor Web Services on the client's behalf — PassTickets are a server-to-server mechanism and are not handled by the client directly.

This means:

- No direct credentials stored per-Endevor-connection when using API ML.
- SSO across all Code4z tools that share the same Zowe `base` profile.
- MFA compatibility through the API ML login flow.

**Configuration:** Create a Zowe team config `base` profile pointing to your API ML Gateway host and port, then reference it in your Endevor connection profile.

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
