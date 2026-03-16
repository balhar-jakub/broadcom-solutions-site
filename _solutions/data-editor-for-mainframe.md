---
title: Data Editor for Mainframe
tagline: Browse and edit z/OS data sets — including VSAM — using a table-based UI in VS Code.
tags: [vscode, api-ml, data-sets, vsam, file-master-plus, code4z]
api_ml: true
api_ml_details: >-
  Data Editor for Mainframe connects to the File Master Plus REST API hosted on
  z/OS. When File Master Plus is registered behind the API Mediation Layer Gateway,
  the extension authenticates via an API ML token, enabling SSO across the Code4z
  tool suite.
vscode: true
marketplace_url: https://marketplace.visualstudio.com/items?itemName=broadcomMFD.data-editor-for-mainframe
marketplace_publisher: broadcomMFD
github_url: https://github.com/BroadcomMFD/data-editor-for-mainframe
npm_package: "@broadcom/file-master-plus-for-zowe-cli"
docs_url: https://techdocs.broadcom.com/us/en/ca-mainframe-software/devops/code4z/2-0.html
---

## Overview

Data Editor for Mainframe is part of the [Code4z](https://mainframe.broadcom.com/code4z-developer-cockpit) suite. Backed by **CA File Master Plus**, it provides a structured, table-based editor for z/OS data sets, removing the need for a 3270 terminal to browse or modify file contents.

Key features:

- **Browse and edit** sequential, partitioned (PDS/PDSE), and VSAM data sets.
- **Table view** — data is presented in a column-oriented grid based on record layout.
- **Record layout import** — parse COBOL copybooks or PL/I structures to define column headers.
- **Filter and search** — filter records by field values without downloading the entire file.
- **Hex view** — toggle between character and hexadecimal display for packed/binary fields.
- **Compare** — diff two data sets or two versions of the same file.
- **Upload** — push locally edited data back to the mainframe.

## API Mediation Layer Integration

Data Editor for Mainframe uses the **File Master Plus REST API** on z/OS. When that REST API is registered behind the API ML Gateway, the extension:

- Routes all requests through the gateway endpoint.
- Authenticates with an APIML Authentication Token rather than raw credentials.
- Participates in the Zowe SSO session shared with Zowe Explorer and other Code4z tools.

## CLI Companion

```bash
npm install -g @broadcom/file-master-plus-for-zowe-cli
zowe fmp browse-data-set "MY.DATA.SET"
```

## Extension Details

| Field | Value |
|---|---|
| Publisher | `broadcomMFD` |
| Extension ID | `broadcomMFD.data-editor-for-mainframe` |
| Part of | Code4z extension pack |
| Backend product | CA File Master Plus |
| License | Broadcom proprietary |
