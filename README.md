# Tuquet Schema Registry

> **Canonical JSON Schemas & CLI Manifests for the Tuquet Ecosystem**  
> Single Source of Truth (SSOT) for CLI manifests, microservice pillar configurations, and automation workflows.

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![JSON Schema Draft 2020-12](https://img.shields.io/badge/JSON_Schema-Draft_2020--12-green.svg)](https://json-schema.org/draft/2020-12/schema)
[![GitHub Pages](https://img.shields.io/badge/Hosted_at-tuquet.com%2Fschema-purple.svg)](https://tuquet.com/schema/)

---

## 1. Overview

The `tuquet/schema` repository is the centralized, standalone schema catalog for the **Tuquet Ecosystem**. It provides:
1. **VS Code Contributes CLI Manifest**: Declarative specification of all Tuquet CLI commands, arguments, options, and MCP tool bindings.
2. **Microservice Pillar Configuration Schemas**: Authoritative JSON Schemas for local runtime configuration files (`~/.specter/*/*.json`), providing instant IntelliSense and validation in modern IDEs.
3. **Automated GitHub Pages CDN**: Schemas are publicly accessible under `https://tuquet.com/schema/` for direct `$schema` resolution.

---

## 2. Catalog of Schemas

### CLI Command Manifests
| Schema File | Hosted URL | Description |
| :--- | :--- | :--- |
| [`cli.manifest.schema.json`](cli.manifest.schema.json) | `https://tuquet.com/schema/cli.manifest.schema.json` | Meta-schema validating CLI command catalogs (VS Code contributes standard). |
| [`cli.manifest.json`](cli.manifest.json) | `https://tuquet.com/schema/cli.manifest.json` | Master catalog of all 37 Tuquet CLI commands across 5 storage pillars and runtimes. |

### Microservice Pillar Configurations (`config/`)
| Configuration | Schema File | Hosted URL | Validates File |
| :--- | :--- | :--- | :--- |
| **Bridge Mesh** | [`bridge.schema.json`](config/bridge.schema.json) | `https://tuquet.com/schema/config/bridge.schema.json` | `~/.specter/bridge/bridge.json` |
| **Browser Runtime** | [`browser.schema.json`](config/browser.schema.json) | `https://tuquet.com/schema/config/browser.schema.json` | `~/.specter/browser/browser.json` |
| **Automa Engine** | [`automa.schema.json`](config/automa.schema.json) | `https://tuquet.com/schema/config/automa.schema.json` | `~/.specter/automa/automa.json` |
| **Runner Worker** | [`runner.schema.json`](config/runner.schema.json) | `https://tuquet.com/schema/config/runner.schema.json` | `~/.specter/automa/runner.json` |
| **Workstation Identity** | [`system.schema.json`](config/system.schema.json) | `https://tuquet.com/schema/config/system.schema.json` | `~/.specter/system/system.json` |
| **Synthetic Faker** | [`faker.schema.json`](config/faker.schema.json) | `https://tuquet.com/schema/config/faker.schema.json` | `~/.specter/faker/faker.json` |

---

## 3. Usage in Modern IDEs

### Method 1: Using `$schema` Header (Recommended)
Add the `$schema` property to any JSON configuration file:

```json
{
  "$schema": "https://tuquet.com/schema/config/bridge.schema.json",
  "default_user": "root",
  "http_proxy_port": 8118,
  "auto_reconnect": true,
  "servers": []
}
```

### Method 2: VS Code Workspace Configuration
Add the following to `.vscode/settings.json` or your `*.code-workspace` file:

```json
{
  "json.schemas": [
    {
      "fileMatch": ["*bridge.json"],
      "url": "https://tuquet.com/schema/config/bridge.schema.json"
    },
    {
      "fileMatch": ["*browser.json"],
      "url": "https://tuquet.com/schema/config/browser.schema.json"
    },
    {
      "fileMatch": ["*automa.json"],
      "url": "https://tuquet.com/schema/config/automa.schema.json"
    },
    {
      "fileMatch": ["*runner.json"],
      "url": "https://tuquet.com/schema/config/runner.schema.json"
    },
    {
      "fileMatch": ["*system.json"],
      "url": "https://tuquet.com/schema/config/system.schema.json"
    },
    {
      "fileMatch": ["*faker.json"],
      "url": "https://tuquet.com/schema/config/faker.schema.json"
    }
  ]
}
```

---

## 4. Contract Verification

Consumers such as [`tuquet/cli`](https://github.com/tuquet/cli) verify 100% parity with this schema via automated gate tests (`cargo test --test schema_contract`). Any undeclared command or invalid schema triggers a test failure.

---

## 5. License

MIT © [Tuquet Ecosystem](https://github.com/tuquet)
