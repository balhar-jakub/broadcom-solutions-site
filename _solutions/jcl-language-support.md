---
title: JCL Language Support
tagline: Syntax highlighting, snippets, and basic validation for Job Control Language in VS Code.
tags: [vscode, language-support, jcl, code4z]
api_ml: false
vscode: true
marketplace_url: https://marketplace.visualstudio.com/items?itemName=broadcomMFD.jcl-language-support
marketplace_publisher: broadcomMFD
github_url: https://github.com/BroadcomMFD/che-che4z-lsp-for-jcl
docs_url: https://techdocs.broadcom.com/us/en/ca-mainframe-software/devops/code4z/2-0.html
---

## Overview

JCL Language Support is a lightweight VS Code extension for editing **Job Control Language (JCL)** files locally. It provides the editing quality-of-life improvements that JCL developers expect from a modern IDE.

Key features:

- **Syntax highlighting** — JCL statements (JOB, EXEC, DD), parameters, comments, and inline procedures.
- **Code snippets** — boilerplate for common JCL patterns: JOB cards, EXEC steps, PROC definitions, dataset allocations.
- **Basic validation** — detects obvious structural errors before job submission.
- **Comment support** — toggle line comments with the standard VS Code shortcut.

## Companion: JCL Check Support

For deeper JCL validation backed by the **JCLCheck Workload Automation** product, see [JCL Check Support](../jcl-check-support/), which uses the same VS Code editing experience but adds server-side validation via API ML.

## Extension Details

| Field | Value |
|---|---|
| Publisher | `broadcomMFD` |
| Extension ID | `broadcomMFD.jcl-language-support` |
| Part of | Code4z extension pack |
| License | EPL-2.0 |
