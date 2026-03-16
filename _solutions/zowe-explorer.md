---
title: Zowe Explorer
tagline: Interact with z/OS data sets, USS files, and JES jobs directly from VS Code.
tags: [zowe, vscode, data-sets, uss, jobs, api-ml]
api_ml: true
api_ml_details: >-
  Zowe Explorer uses the API Mediation Layer token-based authentication (APIML
  Authentication Token) to access z/OSMF. Profiles can be configured with an API
  ML base profile so that a single token grants access to all registered services,
  enabling Single Sign-On across all Zowe client tools.
vscode: true
marketplace_url: https://marketplace.visualstudio.com/items?itemName=Zowe.vscode-extension-for-zowe
marketplace_publisher: Zowe
github_url: https://github.com/zowe/zowe-explorer-vscode
npm_package: "@zowe/zowe-explorer-api"
docs_url: https://docs.zowe.org/stable/user-guide/ze-install
zowe_conformant: "Zowe Conformant — Explorer for VS Code (V3)"
---

## Server-Side Requirements

Zowe Explorer requires **z/OSMF (z/OS Management Facility)** to be installed, configured, and running on the target z/OS system. All core functions — data set access, USS file management, and JES job operations — are implemented via z/OSMF REST APIs. The following z/OSMF tasks must be active:

- **z/OSMF Jobs REST services** — required for JES job submission and spool viewing.
- **z/OSMF Data Set and File REST services** — required for data set and USS file operations.

When using the **API Mediation Layer**, the z/OSMF service must additionally be registered with the API ML Discovery Service, or the extension must be configured with a `zosmf` service profile alongside the `base` API ML profile.

## Overview

Zowe Explorer is the flagship VS Code extension of the [Zowe](https://zowe.org) open-source project, co-developed and sponsored by Broadcom. It brings the mainframe into the VS Code ecosystem, letting developers browse and edit z/OS resources without leaving their IDE.

Key capabilities include:

- **Data Sets** — create, edit, rename, copy, upload, and download sequential and partitioned data sets.
- **USS Files** — full directory and file management on z/OS Unix System Services.
- **JES Jobs** — submit JCL, monitor job status, and view spool output in real time.
- **Multiple profiles** — connect to several z/OS systems simultaneously with different credentials or authentication schemes.
- **Secure Credential Store** — optionally store passwords and tokens using the OS keychain.

## API Mediation Layer Integration

Zowe Explorer can authenticate through the **API Mediation Layer** instead of providing a username and password directly to each service. When a Zowe team configuration file includes a `base` profile pointing to the API ML Gateway, a single SSO token is obtained at login and reused across all service calls. This eliminates repeated password prompts and is compatible with MFA. The API ML Gateway internally uses PassTickets to authenticate to downstream z/OSMF services on the client's behalf — this is a server-to-server mechanism transparent to the end user.

To configure API ML authentication in Zowe Explorer:

1. Add a `base` profile to your Zowe team config (`zowe.config.json`) pointing to the API ML Gateway host and port.
2. Set `tokenType: apimlAuthenticationToken` in the base profile.
3. In Zowe Explorer, log in once via **Zowe Explorer: Log in to Authentication Service**.

## Extension Details

| Field | Value |
|---|---|
| Publisher | `Zowe` |
| Extension ID | `Zowe.vscode-extension-for-zowe` |
| Current Version | v3.x (follows Zowe LTS releases) |
| License | EPL-2.0 |
| Minimum VS Code | 1.79.0 |

## Related Tools

- [Zowe CLI](https://github.com/zowe/zowe-cli) — command-line companion that shares the same team config profiles.
- [Explorer for Endevor](../explorer-for-endevor/) — Broadcom extension that builds on Zowe Explorer's base profile and API ML integration.
- [CICS for Zowe Explorer](https://github.com/zowe/cics-for-zowe-client) — community extension adding IBM CICS resource management.
