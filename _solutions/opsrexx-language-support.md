---
title: OPS/REXX Language Support
tagline: Edit OPS/MVS AOF rules and OPS/REXX programs in VS Code with syntax intelligence and live command execution.
tags: [vscode, api-ml, automation, ops-mvs, opsrexx, language-support, code4z]
api_ml: true
api_ml_details: >-
  OPS/REXX Language Support connects to the OPS/MVS REST API (OPSREST), which can
  be registered with the API Mediation Layer. When a Zowe base profile points to
  the API ML Gateway, the extension authenticates using an apimlAuthenticationToken
  and all OPS/MVS commands are routed through the gateway — providing SSO with
  Zowe Explorer and other Code4z tools.
vscode: true
marketplace_url: https://marketplace.visualstudio.com/items?itemName=broadcomMFD.opsrexx-language-support
marketplace_publisher: broadcomMFD
github_url: https://github.com/BroadcomMFD/opsrexx-language-support
docs_url: https://techdocs.broadcom.com/us/en/ca-mainframe-software/automation/ca-ops-mvs-event-management-and-automation/14-0.html
zowe_conformant: "Zowe Conformant — Explorer for VS Code (V3)"
---

## Server-Side Requirements

OPS/REXX Language Support has **no mandatory server-side prerequisites** for its core editing features (syntax highlighting, hover insights, autocompletion, and basic error checking all work offline against local files).

For live command execution and OPSLOG access, one of two server-side connections is required:

### Option 1: OPS/MVS REST API (recommended for enterprise use)

- **OPS/MVS® Event Management and Automation** installed and running on z/OS.
- **OPS/MVS REST API (`OPSREST`)** configured and running as a z/OS started task. This is the only option that supports API ML integration and provides access to the full feature set, including executing OPS/REXX programs and searching OPSLOG records.
- A Zowe team config file (`zowe.config.json`) containing an `ops` profile with the REST API host, port, and `"rest-api": true`.

### Option 2: SSH (for quick individual setup)

- **OPS/MVS** installed on z/OS.
- The **OX load module** (from `CCLXLOAD`, the OPS/MVS load library) must be accessible — either in a LNKLST/LPALIB library, or in a STEPLIB specified in the user's `.ops_profile`.
- A Zowe **SSH profile** pointing to the target LPAR.
- The `OPSVSCE` backend REXX program must be deployed to a designated data set on z/OS using the **OPS/MVS: Deploy Backend** VS Code command.

SSH gives access to a **subset** of features (rule status, enable/disable, auto-enable). Commands that require the REST API — executing OPS/REXX programs and searching OPSLOG records — are not available over SSH.

## Overview

OPS/REXX Language Support is part of the [Code4z](https://mainframe.broadcom.com/code4z-developer-cockpit) suite. It brings IDE-quality editing to OPS/MVS **Automated Operations Facility (AOF) rules** and **OPS/REXX programs**, which are the building blocks of z/OS automation. Engineers can develop, test, and manage automation rules directly from VS Code.

Key features:

- **Syntax highlighting** — full OPS/REXX grammar including AOF rule type identifiers (`)MSG`, `)CMD`, etc.) and OPS/REXX language extensions.
- **Hover insights** — documentation for OPS/REXX built-in functions, host environment names, and AOF event variable names on hover.
- **Autocompletion** — suggestions for AOF variables (triggered by `.` after a rule type stem), built-in functions, and host environment names.
- **Basic error checking** — AOF rule syntax and OPS/REXX syntax validated in the editor without a mainframe connection.
- **Snippets** — a library of frequently used AOF rule patterns to accelerate rule authoring.
- **Live rule management** (requires REST API or SSH connection):
  - Show, enable, disable, set/reset auto-enable for AOF rules — accessible via right-click in Zowe Explorer.
- **Execute OPS/REXX programs** (requires REST API):
  - Run programs directly from VS Code with parameter input.
- **Search OPSLOG records** (requires REST API):
  - Query live OPSLOG data with filter parameters.
- **Zowe Explorer integration** — file associations allow data set members containing OPS/REXX rules to be opened with correct language detection.

## API Mediation Layer Integration

When the **OPS/MVS REST API** is registered with the API ML Discovery Service, OPS/REXX Language Support can authenticate to it via the API ML Gateway using SSO. The configuration mirrors the Zowe team config approach used by other Code4z tools:

1. Set up a `base` profile in `zowe.config.json` pointing to the API ML Gateway host and port. Log in via Zowe Explorer (**Log in to Authentication Service**) to obtain an `apimlAuthenticationToken`.
2. Configure the `ops` profile with the base path to the OPS/MVS REST API registered on API ML:

```json
"base": {
  "type": "base",
  "properties": {
    "host": "apiml-gateway.example.com",
    "port": 7554,
    "tokenType": "apimlAuthenticationToken"
  },
  "secure": ["tokenValue"]
},
"OPSREST": {
  "type": "ops",
  "properties": {
    "basePath": "opsrest/api/v1",
    "rest-api": true
  }
}
```

3. Do **not** set `host`, `port`, `user`, or `password` on the `ops` profile — those values must come from the `base` profile only. Including them directly bypasses the API ML token.

After authentication, all OPS/MVS REST API commands from the extension route through the API ML Gateway and use the shared SSO token.

## Connection Modes

The extension supports three connection modes, configurable in VS Code settings:

| Mode | Behavior |
|---|---|
| `ADAPTIVE` (default) | Uses whichever connection type supports each command; falls back based on **Preferred Connection Order** setting |
| `ONLY_REST-API` | Uses the REST API exclusively; SSH-only commands will fail |
| `ONLY_SSH` | Uses SSH exclusively; REST API-only commands will fail |

## Extension Details

| Field | Value |
|---|---|
| Publisher | `broadcomMFD` |
| Extension ID | `broadcomMFD.opsrexx-language-support` |
| Part of | Code4z suite (not in the main extension pack) |
| Zowe Conformance | Explorer for VS Code V3 |
| Recommended companions | [REXX Language Support](https://marketplace.visualstudio.com/items?itemName=broadcomMFD.lsp-for-rexx), [Zowe Explorer](../zowe-explorer/) |
| License | Broadcom proprietary |
