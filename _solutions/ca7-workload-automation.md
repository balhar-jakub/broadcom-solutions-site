---
title: CA 7 Workload Automation
tagline: Enterprise job scheduling for z/OS with a REST API onboarded to the API Mediation Layer.
tags: [api-ml, workload-automation, scheduling, batch, ca7]
api_ml: true
api_ml_details: >-
  CA 7 exposes a REST API that can be registered with the API Mediation Layer
  Discovery Service. All Zowe CLI operations against CA 7 authenticate through the
  API ML Gateway, enabling SSO and eliminating per-command credential prompts.
vscode: false
github_url: https://github.com/BroadcomMFD/ca7-for-zowe-cli
npm_package: "@broadcom/ca7-for-zowe-cli"
docs_url: https://techdocs.broadcom.com/us/en/ca-mainframe-software/automation/ca-7-workload-automation-aia/12-1.html
---

## Server-Side Requirements

CA 7 Workload Automation requires:

1. **CA 7** installed on z/OS as a started task.
2. **CA 7 Web Services / REST API** — a web application component of CA 7 that must be explicitly enabled and configured. It is not started automatically with the main CA 7 address space.

## Overview

**CA 7 Workload Automation** is Broadcom's enterprise job scheduling product for IBM z/OS. It manages the end-to-end lifecycle of batch workloads — definition, scheduling, dependency management, execution, and exception handling — across z/OS and distributed platforms.

Integration with Zowe and the API Mediation Layer allows developers and operators to manage CA 7 workloads from the command line and to incorporate job scheduling operations into DevOps pipelines.

Key capabilities:

- **Job scheduling** — define jobs, schedule triggers (time, event, predecessor completion), and manage calendars.
- **Dependency management** — model complex job-dependency chains and cross-platform dependencies.
- **Exception handling** — automatic restart/rerun, abend recovery, and SLA monitoring.
- **REST API** — CA 7 exposes a REST API for programmatic access to scheduling operations.
- **Zowe CLI integration** — the `@broadcom/ca7-for-zowe-cli` plugin wraps the REST API with Zowe-style commands.

## API Mediation Layer Integration

The CA 7 REST API can be onboarded to the API Mediation Layer as a registered microservice:

1. Create a **static YAML service definition** for CA 7 and place it in the API ML's configured static definition directory on z/OS. This file describes the CA 7 service endpoint, `serviceId`, and metadata for the API Catalog.
2. The **API ML Discovery Service** picks up the definition at startup (or on a refresh). From this point the **API Gateway** routes requests to CA 7 using the assigned `serviceId`.
3. The **API Catalog** displays CA 7's OpenAPI documentation for self-service discovery.
4. **APIML token-based SSO** eliminates per-command credential prompts when using the Zowe CLI plugin.

> **Note:** CA 7 does not use the Zowe onboarding SDK for self-registration. The static YAML definition approach is the supported method.

## Zowe CLI Plugin

```bash
npm install -g @broadcom/ca7-for-zowe-cli
zowe ca7 list job --job-name DAILYEOD
zowe ca7 run job --job-name PAYROLL
```

## Product Details

| Field | Value |
|---|---|
| Vendor | Broadcom |
| Product family | CA Automation |
| REST API | Yes — included in product installation |
| npm package | `@broadcom/ca7-for-zowe-cli` |
| Docs | [CA 7 TechDocs](https://techdocs.broadcom.com/us/en/ca-mainframe-software/automation/ca-7-workload-automation-aia/12-1.html) |
