---
title: Bridge for Git Explorer
tagline: Synchronize CA Endevor SCM elements with Git repositories from VS Code.
tags: [vscode, api-ml, endevor, git, devops, code4z]
api_ml: true
api_ml_details: >-
  Bridge for Git Explorer communicates with the Endevor Bridge for Git REST API,
  which can be deployed behind the API Mediation Layer Gateway. Authentication uses
  API ML token-based SSO, consistent with other Code4z extensions that share the
  same Zowe base profile.
vscode: true
marketplace_url: https://marketplace.visualstudio.com/items?itemName=broadcomMFD.bridge-for-git-explorer
marketplace_publisher: broadcomMFD
github_url: https://github.com/BroadcomMFD/bridge-for-git-explorer
npm_package: "@broadcom/endevor-bridge-for-git-for-zowe-cli"
docs_url: https://techdocs.broadcom.com/us/en/ca-mainframe-software/devops/code4z/2-0.html
---

## Overview

Bridge for Git Explorer is the VS Code interface for **CA Endevor Bridge for Git** — a product that synchronizes Endevor SCM elements with Git repositories. It allows mainframe teams to adopt modern Git-based workflows (pull requests, branch strategies, CI/CD pipelines) while keeping Endevor as the authoritative mainframe SCM.

Key features:

- **Repository mapping view** — see which Endevor maps and subsystems are synchronized with which Git repos.
- **Synchronization status** — view pending changes, conflicts, and last-sync timestamps.
- **Trigger sync** — manually initiate a pull (Git → Endevor) or push (Endevor → Git) from the IDE.
- **Conflict resolution** — view and resolve synchronization conflicts before committing.
- **Branch mapping** — configure which Git branches map to which Endevor stages.
- **Audit trail** — link Git commits back to Endevor change packages and elements.

## API Mediation Layer Integration

The Bridge for Git REST API is deployed as a z/OS service and can be registered with the API ML Discovery Service. When deployed behind the API Gateway:

- VS Code extension and CLI plugin route all requests through the API ML Gateway URL.
- A single APIML SSO token is used for authentication.
- The service is discoverable in the API Catalog alongside other Zowe-registered services.

## CLI Companion

```bash
npm install -g @broadcom/endevor-bridge-for-git-for-zowe-cli
zowe ebg sync map --endevor-map MYMAP --git-repo https://github.com/org/repo
```

## Extension Details

| Field | Value |
|---|---|
| Publisher | `broadcomMFD` |
| Extension ID | `broadcomMFD.bridge-for-git-explorer` |
| Backend product | CA Endevor Bridge for Git |
| License | Broadcom proprietary |
