---
title: COBOL Language Support
tagline: Full-featured language server for COBOL development with copybook resolution in VS Code.
tags: [vscode, language-support, cobol, code4z]
api_ml: false
vscode: true
marketplace_url: https://marketplace.visualstudio.com/items?itemName=broadcomMFD.cobol-language-support
marketplace_publisher: broadcomMFD
github_url: https://github.com/BroadcomMFD/che-che4z-lsp-for-cobol
docs_url: https://techdocs.broadcom.com/us/en/ca-mainframe-software/devops/code4z/2-0.html
---

## Overview

COBOL Language Support is one of the core extensions in the [Code4z](https://mainframe.broadcom.com/code4z-developer-cockpit) suite. It implements a full Language Server Protocol (LSP) server for COBOL, bringing IDE-grade editing to mainframe developers regardless of their experience level.

Key features:

- **Syntax highlighting** — full COBOL grammar including CICS, DB2, and DaCo dialects.
- **Autocomplete** — context-aware suggestions for keywords, variables, paragraphs, and copybooks.
- **Real-time diagnostics** — inline errors and warnings as you type, before submitting to the mainframe.
- **Go to definition / Find references** — navigate across paragraphs, variables, and copybook members.
- **Copybook resolution** — fetches copybooks from local workspace, USS paths, z/OS data sets (via Zowe), or a local cache.
- **Outline view** — structured overview of divisions, sections, paragraphs, and data items.
- **Hover documentation** — shows type and context information when hovering over identifiers.
- **Snippets** — boilerplate for common COBOL structures.

## Copybook Resolution via Zowe

When copybooks reside on the mainframe, COBOL Language Support can resolve them dynamically using **Zowe Explorer profiles**. Configure the data set or USS paths in `.vscode/settings.json`:

```json
{
  "cobol-lsp.copybook-config": [
    {
      "profile": "my-zosmf-profile",
      "type": "DATASET",
      "paths": ["SYS1.COPYLIB", "TEAM.COPYLIB"]
    }
  ]
}
```

## Extension Details

| Field | Value |
|---|---|
| Publisher | `broadcomMFD` |
| Extension ID | `broadcomMFD.cobol-language-support` |
| Part of | Code4z extension pack |
| Language server | Java-based LSP implementation |
| Supported dialects | IBM COBOL, CICS, DB2 SQL, DaCo |
| License | EPL-2.0 |
