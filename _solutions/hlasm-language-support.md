---
title: HLASM Language Support
tagline: Rich language server for High Level Assembler (HLASM) with macro expansion and diagnostics.
tags: [vscode, language-support, hlasm, assembler, code4z]
api_ml: false
vscode: true
marketplace_url: https://marketplace.visualstudio.com/items?itemName=broadcomMFD.hlasm-language-support
marketplace_publisher: broadcomMFD
github_url: https://github.com/BroadcomMFD/che-che4z-lsp-for-hlasm
docs_url: https://techdocs.broadcom.com/us/en/ca-mainframe-software/devops/code4z/2-0.html
---

## Overview

HLASM Language Support provides a comprehensive Language Server Protocol (LSP) implementation for **IBM High Level Assembler (HLASM)** in VS Code. It is notable for running a full HLASM preprocessor and macro expander locally, giving developers accurate diagnostics without a mainframe connection.

Key features:

- **Syntax highlighting** — HLASM instructions, macros, literals, and operands.
- **Macro expansion** — resolves macro calls locally, including nested macros and conditional assembly.
- **Diagnostics** — syntax and semantic errors flagged inline as you type.
- **Autocomplete** — instruction mnemonics, register names, and macro parameter suggestions.
- **Go to definition / Find references** — navigate symbols across source files and macro libraries.
- **Hover documentation** — operand-level documentation for machine instructions.
- **Outline view** — structured view of CSECTs, DSECTs, macros, and labels.
- **Instruction set support** — z/Architecture, z/OS system macros.

## Extension Details

| Field | Value |
|---|---|
| Publisher | `broadcomMFD` |
| Extension ID | `broadcomMFD.hlasm-language-support` |
| Part of | Code4z extension pack |
| Language server | C++ implementation with WebAssembly packaging |
| License | EPL-2.0 |
