# Workflow Monitor

**SQL workflow execution monitoring for .NET and SQL Server.**

Workflow Monitor provides a local dashboard and REST API for tracking backend processes, workers, imports, batch jobs and other SQL-backed workflows.

## What it monitors

- Running, successful and failed executions
- Start time, completion time and duration
- Process-level execution history
- Processing totals, correct/incorrect records and affected rows
- Errors associated with failed executions
- Filters and CSV export
- Worker/API integration
- Spanish and English interface

## Architecture

```text
                    Browser
                       |
                       v
             Workflow Monitor Web
               MVC + REST API
                       |
                       v
                   SQL Server
                       ^
                       |
             Workflow Monitor Worker
```

The Windows installation runs the Web/API and Worker as Windows services. The product is designed to keep monitoring data in the customer's SQL Server environment.

## Demo edition

The installable Demo is intended for technical evaluation:

- 30-day evaluation period
- Up to 3 registered processes
- 1 Worker/integration
- Real dashboard, REST API and processing
- Reusable sample CSV included
- Read-only access after the evaluation period expires

The Demo is a Windows x64 self-contained package.

## Latest version

**Workflow Monitor 1.1.2** — September 4, 2026

Version 1.1.2 consolidates the validated Windows installer/uninstaller, branding and packaging hardening of the 1.1.x line.

## Download

The public Demo is distributed through **GitHub Releases** together with its SHA-256 checksum.

[Go to Releases](https://github.com/stimpfldev/WorkflowMonitor/releases)

Installation instructions: [docs/INSTALLATION.md](docs/INSTALLATION.md)

Demo scope and limitations: [docs/DEMO.md](docs/DEMO.md)

Release history: [CHANGELOG.md](CHANGELOG.md)

## Requirements

- Windows x64
- SQL Server available locally or through a reachable SQL Server instance
- Administrator permissions during installation
- A modern web browser

The Demo package is self-contained; installing a separate .NET runtime is not required.

## Commercial editions

Professional and Enterprise editions use the same monitoring core with licensed limits and deployment options intended for production environments.

Commercial packages are distributed separately and are not published in this repository.

## Repository scope

This repository is the **public product and distribution surface** for Workflow Monitor. It intentionally does not contain the private commercial source code, license-generation tooling, internal build scripts or customer-specific packages.

---

### Resumen en español

Workflow Monitor permite registrar y consultar ejecuciones de procesos backend y SQL desde un dashboard web, con API REST, Worker, filtros, métricas de procesamiento y exportación CSV.

La edición Demo permite una evaluación técnica durante 30 días, con hasta 3 procesos y 1 Worker/integración. La distribución pública se realiza desde la sección **Releases** de este repositorio.
