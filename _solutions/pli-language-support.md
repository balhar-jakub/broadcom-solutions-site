---
title: PL/I Language Support
tagline: Language server for PL/I source files including include file resolution in VS Code.
tags: [vscode, language-support, pli, code4z]
api_ml: false
vscode: true
marketplace_url: https://marketplace.visualstudio.com/items?itemName=broadcomMFD.pli-language-support
marketplace_publisher: broadcomMFD
github_url: https://github.com/BroadcomMFD/che-che4z-lsp-for-pli
docs_url: https://techdocs.broadcom.com/us/en/ca-mainframe-software/devops/code4z/2-0.html
---

## Overview

PL/I Language Support brings Language Server Protocol (LSP) capabilities to **IBM PL/I for z/OS** development inside VS Code. It reduces the friction of editing PL/I programs locally while ensuring accurate code navigation.

Key features:

- **Syntax highlighting** — full PL/I grammar including structures, on-units, and built-in functions.
- **Autocomplete** — keywords, declared variables, procedure names, and include members.
- **Diagnostics** — inline syntax errors and warnings.
- **Go to definition / Find references** — navigate across declarations and usages.
- **Include file resolution** — fetch `%INCLUDE` members from local paths or from z/OS data sets via Zowe profiles.
- **Outline view** — hierarchical view of procedures, packages, and data declarations.

## Extension Details

| Field | Value |
|---|---|
| Publisher | `broadcomMFD` |
| Extension ID | `broadcomMFD.pli-language-support` |
| Part of | Code4z extension pack |
| License | EPL-2.0 |
