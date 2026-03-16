---
title: Abend Analyzer for Mainframe
tagline: View and analyze z/OS abend reports and symbolic dump data directly in VS Code.
tags: [vscode, debugging, abend, dump-analysis, code4z]
api_ml: false
vscode: true
marketplace_url: https://marketplace.visualstudio.com/items?itemName=broadcomMFD.abend-analyzer
marketplace_publisher: broadcomMFD
github_url: https://github.com/BroadcomMFD/abend-analyzer-for-mainframe
docs_url: https://techdocs.broadcom.com/us/en/ca-mainframe-software/devops/code4z/2-0.html
---

## Overview

Abend Analyzer for Mainframe is part of the [Code4z](https://mainframe.broadcom.com/code4z-developer-cockpit) suite. It connects to the **CA Abend-AID** server-side product to retrieve abend reports and display them alongside source code in VS Code, dramatically speeding up the time it takes to diagnose a program failure.

Key features:

- **Abend report browser** — list and open abend reports stored in the Abend-AID history database.
- **Source correlation** — maps the failing instruction back to the COBOL, PL/I, or Assembler source line.
- **Symbolic dump** — displays working storage, registers, and the call chain in human-readable form rather than raw hex.
- **Offset navigation** — jump from the abend offset to the corresponding source location.
- **Filter reports** — search by job name, abend code, date range, or program name.
- **Side-by-side view** — view the abend report and source file simultaneously.

## Server-Side Requirements

Requires a licensed installation of **CA Abend-AID** on the target z/OS system. CA Abend-AID must be configured with its **REST API component** enabled and running.

The VS Code extension connects to the Abend-AID REST API using a **Zowe connection profile** (the same profile type used by Zowe Explorer). The host, port, and credentials are defined in the Zowe team config file (`zowe.config.json`) — there is no separate connection dialog within the extension itself. Ensure the Abend-AID REST API is accessible over HTTPS from the workstation where VS Code runs.

## Extension Details

| Field | Value |
|---|---|
| Publisher | `broadcomMFD` |
| Extension ID | `broadcomMFD.abend-analyzer` |
| Part of | Code4z extension pack |
| Backend product | CA Abend-AID |
| License | Broadcom proprietary |
