# Workflow Monitor — Customer flows

This document summarizes the supported customer-facing paths from first contact through evaluation, purchase, activation and ongoing use.

## 1. Public product overview

A new visitor starts on the public Workflow Monitor site. From there the visitor can review capabilities, screenshots, plans, documentation, the installable Demo and, when deployed, the hosted read-only visual Demo.

## 2. Read-only visual Demo

The product supports a public Viewer role intended only for a dedicated hosted visual Demo. Viewer access is separate from administrator access, cannot use Worker/API credentials and cannot open `/installation`.

The hosted visual Demo must use its own deployment and non-sensitive demonstration data. It is not a customer installation and its Installation ID is never exposed.

## 3. Installable 30-day Demo

1. Download the Demo ZIP from the official GitHub Release.
2. Verify the published SHA-256 checksum.
3. Extract the ZIP and run `WorkflowMonitorSetup.exe` as Administrator.
4. Select the local SQL Server instance and define the local administrator password.
5. Open Workflow Monitor locally and evaluate the Demo workflow.
6. The Demo supports up to 3 registered processes and 1 Worker/integration for 30 days.
7. After expiration, existing information remains available in read-only mode and new executions are rejected.

The Demo installation creates a persistent Installation ID used later if that same installation is upgraded to a paid edition.

## 4. Professional or Enterprise purchase

1. Select Professional or Enterprise.
2. Select monthly, quarterly, semiannual or annual billing.
3. Enter the customer name and email and accept the privacy policy and purchase terms.
4. Continue to Mercado Pago.
5. After payment confirmation, return to the Workflow Monitor purchase-status page.
6. Link the purchase to the Workflow Monitor installation that will receive the license.

An Installation ID is not required before payment.

## 5. Linking and upgrading an installation

If Workflow Monitor is already installed, including an existing Demo:

1. Open that installation.
2. Go to `/installation`.
3. Copy the Installation ID.
4. Paste it into the purchase-status page.
5. Download the private activation package after it is generated.
6. Run the included activation command as Administrator.

The activator installs only the signed commercial license and restarts the required services. It does not recreate the SQL database, so the existing history and configuration remain in place.

If Workflow Monitor is not installed yet, install the official Demo first and then follow the same activation steps. The paid delivery is an activation package, not a second copy of the Demo.

## 6. Commercial delivery and recovery

When fulfillment is complete, the purchase-status page exposes a private time-limited signed download link. When SMTP is enabled, the same type of delivery link is sent to the customer email address.

If the customer closes the browser or loses the page, `/recuperar` accepts the checkout email address. The response is deliberately generic and does not reveal whether a purchase exists. When a recoverable purchase exists, the system emails a continuation link.

Commercial activation packages are never published in the public GitHub repository.

## 7. Ongoing subscription lifecycle

Mercado Pago subscription events update the commercial state, including active, paused and cancelled states.

For an approved recurring payment, Workflow Monitor records the payment identity so the same payment cannot renew a license twice. A later distinct approved payment queues a renewed license for the same Installation ID. If the current license has remaining paid time, the new period extends from its existing expiration date; otherwise it extends from the current time.

Pausing or cancelling future billing does not invalidate a license already issued for a paid period. That license remains technically valid until its signed expiration date. No new renewal is generated without a new approved payment.

### Installation replacement

Standard plans cover one licensed installation. Moving the paid entitlement to a different machine is not automatic because the license is cryptographically bound to the Installation ID. For a legitimate installation replacement or migration, contact **contacto@federicostimpfl.com.ar** for a support-assisted reissue. The old installation is not automatically transferable to multiple machines.

## Customer-facing URL conventions

Public URLs should remain short and semantic. Paths such as `/planes`, `/installation`, `/demo`, `/retorno`, `/recuperar` and `/entrega` are normal application routes. Internal hosting folder names, provider implementation details and development-only terminology should not be exposed in customer-facing links or copy.
