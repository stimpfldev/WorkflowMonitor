<p>
  <img src="assets/workflow-monitor-mark.svg" alt="Workflow Monitor" width="64" />
</p>

# Workflow Monitor

**SQL workflow execution monitoring for .NET and SQL Server.**

Workflow Monitor provides a local dashboard and REST API for tracking backend processes, workers, imports, batch jobs and other SQL-backed workflows.

## Why it exists

Business-critical backend processes often run without a single operational view. When a batch, integration, Worker, import, or stored procedure fails—or remains active longer than expected—teams may need to reconstruct what happened from scattered logs, direct database queries, and manual checks.

Workflow Monitor centralizes the execution evidence needed to answer:

- What ran, when, and for how long?
- Is it still running, completed successfully, failed, or cancelled?
- How many records were processed correctly or incorrectly?
- How many rows were affected?
- What error was reported?
- Which executions appear stale or unusually long-running?
- What happened for a selected process and date range?

## Main capabilities

- REST API to start, finish, list, and inspect executions
- Execution states: `Running`, `Succeeded`, `Failed`, and `Cancelled`
- Authenticated MVC dashboard
- Process-level execution history and detail
- Start time, completion time, duration, and stale-execution detection
- Processing metrics: total, correct, incorrect, and affected rows
- Error information for failed executions
- Filtering, sorting, pagination, and CSV export
- Worker Service for CSV processing and stored-procedure integration
- SQL Server staging, transactions, procedures, and consistency constraints
- API-key authentication for Workers and integrations
- Local administrator authentication
- Spanish and English localization
- Rate limiting, defensive browser headers, safe errors, and health checks
- Offline signed-license validation for commercial editions
- Demo access rules and capacity limits
- Windows Service hosting for Web/API and Worker

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

The Windows installation runs the Web/API and Worker as Windows services. Monitoring data remains in the configured SQL Server environment.

Detailed architecture: [docs/ARCHITECTURE.md](docs/ARCHITECTURE.md)

## Demo edition

The installable Demo is intended for technical evaluation.

| Demo limit / capability | Value |
|---|---:|
| Evaluation period | 30 days |
| Registered processes | Up to 3 |
| Workers / integrations | 1 |
| CSV export | Enabled |
| Dashboard and REST API | Enabled |
| Real execution processing | Enabled |
| After expiration | Read-only |

The process and Worker limits apply to registered identifiers, not to a simultaneous-execution count. After expiration, existing history and details remain available while new executions are no longer registered.

The Demo is a Windows x64 self-contained package.

## Latest version

**Workflow Monitor 1.1.2** — September 4, 2026

Version 1.1.2 consolidates the validated Windows installer/uninstaller, branding and packaging hardening of the 1.1.x line.

## Download

The public Demo is distributed through **GitHub Releases** together with its SHA-256 checksum.

[Go to Releases](https://github.com/stimpfldev/WorkflowMonitor/releases)

## Documentation

- [Installation instructions](docs/INSTALLATION.md)
- [Demo scope and limitations](docs/DEMO.md)
- [Architecture](docs/ARCHITECTURE.md)
- [Secure deployment baseline](docs/SECURITY-DEPLOYMENT.md)
- [Security policy](SECURITY.md)
- [Support policy](SUPPORT.md)
- [Legal materials](Legal/README.md)
- [EULA — Español](Legal/EULA-ES.txt)
- [EULA — English](Legal/EULA-EN.txt)
- [Third-party notices](Legal/THIRD-PARTY-NOTICES.txt)
- [Public distribution notice](LICENSE.txt)
- [Release history](CHANGELOG.md)

### Word documentation

- [Manual de instalación y uso — ES 1.1.2](docs/SqlWorkflowMonitor_Manual_de_Instalacion_y_Uso_ES_1.1.2.docx)
- [Installation and User Guide — EN 1.1.2](docs/SqlWorkflowMonitor_Installation_and_User_Guide_EN_1.1.2.docx)
- [Descripción comercial — ES 1.1.2](docs/SqlWorkflowMonitor_Descripcion_Comercial_ES_1.1.2.docx)
- [Product Overview — EN 1.1.2](docs/SqlWorkflowMonitor_Product_Overview_EN_1.1.2.docx)

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

This repository is the **public product and distribution surface** for Workflow Monitor. It intentionally does not contain the private commercial source code, license-generation tooling, internal build scripts, private signing material, issued licenses, or customer-specific packages.

---

### Resumen en español

Workflow Monitor permite registrar y consultar ejecuciones de procesos backend y SQL desde un dashboard web, con API REST, Worker, filtros, métricas de procesamiento, detección de ejecuciones demoradas y exportación CSV.

La edición Demo permite una evaluación técnica durante 30 días, con hasta 3 procesos y 1 Worker/integración. Al vencer permanece en modo de solo lectura. La distribución pública se realiza desde la sección **Releases** de este repositorio.
