---
title: OPS/MVS Event Management and Automation
tagline: Automate z/OS operations and manage AOF rules, SSM resources, and OPSLOG via REST API and Zowe CLI.
tags: [api-ml, automation, ops-mvs, opsrexx, operations, ssm]
api_ml: true
api_ml_details: >-
  OPS/MVS exposes a REST API (the OPSREST component) that registers with the API
  Mediation Layer Discovery Service. Zowe CLI and the OPS/REXX Language Support VS
  Code extension authenticate through the API ML Gateway using an APIML token,
  enabling SSO across all Zowe-integrated tools. API ML integration requires the
  OPS/MVS REST API specifically — the older RESTful Web Services component cannot
  be used with API ML.
vscode: false
npm_package: "@broadcom/ops-for-zowe-cli"
github_url: https://github.com/BroadcomMFD/ca7-for-zowe-cli
docs_url: https://techdocs.broadcom.com/us/en/ca-mainframe-software/automation/ca-ops-mvs-event-management-and-automation/14-0.html
zowe_conformant: "Zowe Conformant — CLI (V3)"
---

## Server-Side Requirements

OPS/MVS integration requires the following components on z/OS:

1. **OPS/MVS® Event Management and Automation** — the core product, running as one or more started tasks (OPS/MVS subsystems, typically named `OPSS`).
2. **OPS/MVS REST API (`OPSREST`)** — a separate REST API server component that runs as a z/OS started task under a Java Virtual Machine (JVM) within UNIX System Services (USS). It must be explicitly configured and started; it is not part of the main OPS/MVS address space.

> **Important:** OPS/MVS offers two API server components — the **REST API (OPSREST)** and the older **RESTful Web Services**. Only the **REST API** supports integration with the Zowe API Mediation Layer. The older RESTful Web Services component cannot be registered with API ML.

**Security requirements:** All REST API users must be authorized through OPS/MVS security (SAF/RACF) before they can access the endpoints. Specific SAF permissions are required for each type of operation (viewing rules, executing REXX programs, issuing operator commands, managing SSM resources). Refer to the [Authorize REST API Users](https://techdocs.broadcom.com/us/en/ca-mainframe-software/automation/ca-ops-mvs-event-management-and-automation/14-0/securing/authorize-rest-api-users.html) documentation for the full permissions list.

**Multi-system (OPSplex) note:** When running multiple OPS/MVS instances across different LPARs, one instance of the REST API must be installed and configured per LPAR. When multiple OPS/MVS instances run on a single LPAR, only one REST API instance is required for that LPAR.

## Overview

**OPS/MVS® Event Management and Automation** is Broadcom's z/OS automation product. It intercepts and responds to z/OS events — messages, commands, TSO sessions, SMF records, and more — using Automated Operations Facility (AOF) rules written in OPS/REXX, an extended dialect of REXX. It also manages system resources via the System State Manager (SSM).

Zowe integration allows automation engineers and operators to manage OPS/MVS from the command line and incorporate automation administration into DevOps pipelines.

Key capabilities via the REST API:

- **AOF rule management** — display, enable, disable, and set auto-enable for automation rules and rule sets.
- **SSM resource management** — display the current and desired state of resources; start and stop resources.
- **OPS/REXX execution** — execute OPS/REXX programs programmatically via REST.
- **Operator command execution** — issue MVS operator commands and capture output.
- **OPSLOG access** — search and retrieve OPSLOG records (the OPS/MVS message log).
- **RDF tables** — display Relational Data Framework table data.
- **Subsystem information** — list active OPS/MVS subsystems.

## API Mediation Layer Integration

The OPS/MVS REST API (`OPSREST`) registers with the **API ML Discovery Service** using its built-in Zowe integration capability (configured via `application.yml` on the z/OS server). Once registered:

- The **API Gateway** routes all REST API requests to OPS/MVS using the assigned `serviceId` (typically `opsrest`).
- Clients authenticate to the **API ML Gateway** and receive a JWT (`apimlAuthenticationToken`), which is used for all subsequent OPS/MVS REST API calls.
- The **API Catalog** displays the OPS/MVS REST API OpenAPI specification.

**Zowe team config profile for API ML (`zowe.config.json`):**

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

> **Note:** Do not set `host`, `port`, `user`, or `password` directly on the `ops` profile when using API ML — these must come from the `base` profile only. Setting them directly causes Zowe to bypass the API ML token and access OPS/MVS directly.

## Zowe CLI Plugin

```bash
npm install -g @broadcom/ops-for-zowe-cli

# Rule management
zowe ops show rule --ruleset MYRULESET --rulename MYRULE
zowe ops enable rule --ruleset MYRULESET --rulename MYRULE
zowe ops disable rule --ruleset MYRULESET --rulename MYRULE

# SSM resource management
zowe ops show resource --resource MYAPP
zowe ops start resource --resource MYAPP
zowe ops stop resource --resource MYAPP

# Execute OPS/REXX program (REST API required)
zowe ops execute rexx --rexx-name MYPROG --subsystem OPSS

# Issue an operator command (REST API required)
zowe ops execute command --command "D A,L" --subsystem OPSS

# Search OPSLOG records (REST API required)
zowe ops show records --subsystem OPSS
```

> **Note:** Commands marked "REST API required" are only available when `"rest-api": true` is set in the Zowe `ops` profile and the `OPSREST` component is active. Commands that work with both the REST API and the older RESTful Web Services component do not require this flag.

## Product Details

| Field | Value |
|---|---|
| Vendor | Broadcom |
| Product | OPS/MVS® Event Management and Automation |
| Current version | 14.0 |
| REST API component | OPSREST (z/OS started task, JVM/USS) |
| npm package | `@broadcom/ops-for-zowe-cli` |
| Zowe Conformance | CLI V3 |
| Docs | [OPS/MVS 14.0 TechDocs](https://techdocs.broadcom.com/us/en/ca-mainframe-software/automation/ca-ops-mvs-event-management-and-automation/14-0.html) |
