---
title: COBOL Control Flow
tagline: Visualize the execution flow of COBOL programs as an interactive graph in VS Code.
tags: [vscode, cobol, visualization, code4z]
api_ml: false
vscode: true
marketplace_url: https://marketplace.visualstudio.com/items?itemName=broadcomMFD.ccf
marketplace_publisher: broadcomMFD
github_url: https://github.com/BroadcomMFD/cobol-control-flow
docs_url: https://techdocs.broadcom.com/us/en/ca-mainframe-software/devops/code4z/2-0.html
---

## Overview

COBOL Control Flow generates an **interactive flowchart** of a COBOL program's execution path directly inside VS Code. It is designed to aid code comprehension, onboarding, and debugging by making the logical structure of COBOL programs immediately visible.

Key features:

- **Flowchart generation** — click any COBOL source file to render its control flow graph.
- **Navigate by clicking** — click a node in the graph to jump to the corresponding source line.
- **Bidirectional** — clicking source lines highlights the corresponding graph node.
- **PERFORM tracking** — visualizes PERFORM ... THRU constructs and nested PERFORM calls.
- **Conditional branches** — IF/ELSE/EVALUATE branches are represented as separate paths.
- **Export** — save the generated diagram as an SVG image.
- **Works offline** — no mainframe connection required; analysis runs entirely on local source files.

## Integration with COBOL Language Support

COBOL Control Flow works best alongside [COBOL Language Support](../cobol-language-support/). When COBOL Language Support resolves copybooks, Control Flow can include them in the graph, providing a complete view of programs that span multiple copybook members.

## Extension Details

| Field | Value |
|---|---|
| Publisher | `broadcomMFD` |
| Extension ID | `broadcomMFD.ccf` |
| Part of | Code4z extension pack |
| Requires | COBOL Language Support (recommended) |
| License | EPL-2.0 |
