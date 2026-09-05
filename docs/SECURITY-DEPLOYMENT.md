# Secure deployment baseline

Workflow Monitor is intended for controlled on-premises or private-network deployment. The default production package listens only on `127.0.0.1:5080`.

## Required configuration

The installer configures the local Web/API and Worker services. For manual or customized deployments, the equivalent settings must be provided explicitly.

Web/API security configuration includes:

- SQL Server connection string
- API key with at least 32 characters
- administrator username
- administrator password hash and salt

Worker configuration includes:

- Workflow Monitor API base URL
- API key
- SQL Server connection string
- Worker identity
- CSV input, processed, and error folders

The application validates required security values at startup. The Worker rejects plain HTTP API URLs for non-loopback hosts.

## HTTPS and remote access

For a single-machine installation, loopback HTTP between trusted local components is acceptable when the port is not exposed externally.

For remote access:

1. Keep Kestrel bound to loopback when possible.
2. Place IIS, nginx, Apache, or another controlled reverse proxy in front of the application.
3. Terminate TLS at the proxy using a trusted certificate.
4. Restrict network access and configure the final host name in `AllowedHosts`.
5. Enable HTTPS requirements only when the deployment has a valid HTTPS endpoint or correctly forwards the original scheme.
6. Trust forwarded headers only from explicitly trusted proxies.

Do not expose the default loopback HTTP endpoint directly to an untrusted network.

## SQL Server

Production templates use encrypted SQL Server connections and do not trust an unverified server certificate.

Use a dedicated least-privilege service identity. Database creation and migration permissions should be separated from normal runtime permissions where operationally possible.

Back up the database before upgrades or schema changes.

## Included protections

Workflow Monitor includes, among other controls:

- PBKDF2-SHA-256 administrator password verification
- constant-time password-hash and API-key comparison
- HttpOnly and SameSite cookies
- login and API rate limiting
- anti-forgery protection for browser POST operations
- Content Security Policy and defensive browser headers
- safe Problem Details responses without stack traces
- CSV size and row limits
- parameterized SQL access and stored procedures

## Windows services and filesystem

The installer creates the Workflow Monitor Web/API and Worker services and uses controlled application/data directories.

Operational CSV folders are:

```text
C:\SqlWorkflowMonitor\Data\Input
C:\SqlWorkflowMonitor\Data\Processed
C:\SqlWorkflowMonitor\Data\Error
```

Do not grant broad write permissions to unrelated users or services.

## Sensitive material

Never publish or commit:

- administrator passwords, password hashes, or salts from real installations
- API keys
- connection-string passwords
- private signing keys
- issued commercial `.lic` files
- customer connection strings or production identifiers
- customer CSV files or production logs

The public verification key used to validate signed licenses is not secret and may be distributed with the product.

## Demo deployments

The Demo uses the same fundamental security boundaries as the commercial product, but remains an evaluation edition. Demo limits do not replace normal Windows, SQL Server, firewall, TLS, backup, and access-control practices.
