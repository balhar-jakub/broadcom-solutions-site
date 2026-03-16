---
title: JCL Check Support
tagline: Server-side JCL validation backed by JCLCheck Workload Automation via API ML.
tags: [vscode, api-ml, jcl, validation, code4z]
api_ml: true
api_ml_details: >-
  JCL Check Support connects to the JCLCheck REST API on z/OS. When the JCLCheck
  service is registered behind the API Mediation Layer Gateway, the extension
  routes validation requests through the gateway and authenticates using an API ML
  token, supporting SSO with other Code4z tools.
vscode: true
marketplace_url: https://marketplace.visualstudio.com/items?itemName=broadcomMFD.jcl-check-support
marketplace_publisher: broadcomMFD
github_url: https://github.com/BroadcomMFD/jcl-check-support
npm_package: "@broadcom/jclcheck-for-zowe-cli"
docs_url: https://techdocs.broadcom.com/us/en/ca-mainframe-software/devops/code4z/2-0.html
---

## Overview

JCL Check Support enhances the basic [JCL Language Support](../jcl-language-support/) extension by adding **server-side validation** backed by **CA JCLCheck Workload Automation**. Instead of simple syntax checks, the extension submits JCL to the JCLCheck REST API and surfaces errors that would only be detected by the mainframe JCL interpreter.

Key features:

- **Deep JCL validation** — catches allocation errors, undefined datasets, procedure conflicts, and parameter issues that local editors cannot detect.
- **Inline diagnostics** — errors returned by JCLCheck are displayed as VS Code problems on the relevant lines.
- **Quick-fix suggestions** — common errors include suggested corrections.
- **On-save or on-demand** — choose whether validation runs automatically on save or only when manually triggered.
- **Multiple connections** — validate against different z/OS systems using separate Zowe profiles.

## API Mediation Layer Integration

JCL Check Support calls the **JCLCheck REST API**, which can be deployed behind the API ML Gateway. When configured with an API ML base profile:

- All JCL validation requests route through the API Gateway.
- The extension authenticates with a single APIML token (no per-request password).
- Validation works as part of the same SSO session as Zowe Explorer and other Code4z tools.

## CLI Companion

```bash
npm install -g @broadcom/jclcheck-for-zowe-cli
zowe jclcheck check jcl --local-file ./my-job.jcl
```

## Extension Details

| Field | Value |
|---|---|
| Publisher | `broadcomMFD` |
| Extension ID | `broadcomMFD.jcl-check-support` |
| Part of | Code4z extension pack |
| Backend product | CA JCLCheck Workload Automation |
| License | Broadcom proprietary |
