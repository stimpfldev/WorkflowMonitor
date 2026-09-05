# Secure deployment baseline

Workflow Monitor is designed primarily for controlled Windows and SQL Server environments. The default package keeps the Web/API endpoint on loopback so that remote access must be enabled deliberately.

## Default binding

The packaged Web/API host binds to:

```text
http://127.0.0.1:5080
```

This is suitable for local use on the same Windows host. Do not expose this plain-HTTP endpoint directly to an untrusted network.

## Remote access

For remote browser or integration access, use one of these approaches:

1. Keep Kestrel on loopback and place a trusted TLS reverse proxy in front of it.
2. Configure a valid HTTPS endpoint directly in Kestrel with an appropriate certificate and private-key protection.

The reverse proxy or HTTPS endpoint should terminate TLS, restrict network exposure, and preserve only the headers required by the application.

## Authentication

- Dashboard access uses the configured local administrator account.
- Workers and integrations authenticate with `X-Api-Key`.
- Credentials and API keys must be unique, non-empty, and stored outside source control.
- Do not embed real secrets in screenshots, support tickets, scripts committed to Git, or public configuration examples.

## SQL Server

- Use only the minimum SQL permissions required by the installed services.
- Prefer encrypted SQL Server connections for non-local deployments.
- Do not use `TrustServerCertificate=True` as a production substitute for a properly trusted certificate unless the environment has an explicit, documented reason.
- Back up the database before product upgrades or schema changes.

## Windows services and filesystem

The installer creates the Workflow Monitor Web/API and Worker services and uses controlled application/data directories. Do not grant broad write permissions to unrelated users or services.

Operational CSV folders should remain dedicated to the Worker:

```text
C:\SqlWorkflowMonitor\Data\Input
C:\SqlWorkflowMonitor\Data\Processed
C:\SqlWorkflowMonitor\Data\Error
```

## Public exposure

The health endpoint is intended to expose availability only. Administrative screens, execution data, API operations, SQL Server, installer logs, and application data directories should not be published directly to the Internet.

## Sensitive material

Never publish or commit:

- administrator passwords or derived reusable credentials;
- API keys;
- private signing keys;
- issued commercial `.lic` files;
- customer connection strings or production identifiers;
- customer CSV files or production logs.

The public verification key used to validate signed licenses is not secret and may be distributed with the product.

## Demo deployments

The Demo uses the same security boundaries as the commercial product, but remains an evaluation edition. Demo limits do not replace normal Windows, SQL Server, firewall, TLS, backup, and access-control practices.
