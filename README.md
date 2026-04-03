# apm-vscode-extension

VS Code extension specific APM package for winccoa-tools-pack.

## Overview

This package contains AI agent skills, prompts, and instructions specific to **VS Code extension development**.

Inherits from `apm-org` (organization-wide configuration).

## Usage

Add to your VS Code extension's `apm.yml`:

```yaml
dependencies:
  apm:
    - winccoa-tools-pack/apm-org
    - winccoa-tools-pack/apm-vscode-extension
```

Then run:

```bash
apm install
```

## Contents

- `instructions/` — VS Code extension development context
- `skills/` — Extension-specific AI capabilities
- `prompts/` — Extension-specific templates

## Structure

```
apm-vscode-extension/
├── apm.yml
├── README.md
├── instructions/
├── skills/
└── prompts/
```
