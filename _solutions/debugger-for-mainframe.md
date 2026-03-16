---
title: Debugger for Mainframe
tagline: Debug COBOL, PL/I, and Assembler programs running in CICS or batch from VS Code.
tags: [vscode, debugging, cobol, pli, cics, batch, code4z, intertest]
api_ml: false
vscode: true
marketplace_url: https://marketplace.visualstudio.com/items?itemName=broadcomMFD.debugger-for-mainframe
marketplace_publisher: broadcomMFD
github_url: https://github.com/BroadcomMFD/debugger-for-mainframe
docs_url: https://techdocs.broadcom.com/us/en/ca-mainframe-software/devops/code4z/2-0.html
---

## Overview

Debugger for Mainframe integrates with **Broadcom InterTest™** and **InterTest Batch** to bring the VS Code debug adapter protocol (DAP) to z/OS program debugging. Developers can set breakpoints, step through code, and inspect variables in CICS or batch programs — all from a familiar IDE interface.

Key features:

- **Breakpoints** — set, hit, and clear breakpoints in COBOL, PL/I, and HLASM programs.
- **Step through code** — step over, step into, step out at the source level.
- **Variable inspection** — view and modify working storage, linkage section, and register values.
- **Watch expressions** — monitor specific variables or memory addresses.
- **Call stack** — view the full program call chain at any point during execution.
- **CICS support** — debug CICS transactions interactively with InterTest for CICS.
- **Batch support** — debug batch jobs running under InterTest Batch.
- **Multi-language** — handles mixed-language programs (COBOL calling HLASM, etc.).

## Server-Side Requirement

This extension requires a licensed installation of **CA InterTest for CICS** or **CA InterTest Batch** on the target z/OS system. The extension communicates with the InterTest Debug Manager over a TCP/IP connection configured in the VS Code launch profile.

## Extension Details

| Field | Value |
|---|---|
| Publisher | `broadcomMFD` |
| Extension ID | `broadcomMFD.debugger-for-mainframe` |
| Part of | Code4z extension pack |
| Backend product | CA InterTest for CICS / CA InterTest Batch |
| Protocol | Debug Adapter Protocol (DAP) |
| License | Broadcom proprietary |
