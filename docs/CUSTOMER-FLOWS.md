# Workflow Monitor — Customer flows

This document summarizes the supported customer-facing paths from first contact through evaluation, purchase, activation and ongoing use.

## 1. Public product overview

A new visitor starts on the public Workflow Monitor site. From there the visitor can review capabilities, screenshots, plans, documentation and the installable Demo.

## 2. Read-only visual Demo

The product supports a public Viewer role intended for a hosted read-only visual Demo. This access must be enabled only on the dedicated public Demo deployment. Viewer access is separated from administrator access and cannot use the API credentials reserved for Workers/integrations.

## 3. Installable 30-day Demo

1. Download the Demo ZIP from the official GitHub Release.
2. Verify the published SHA-256 checksum.
3. Extract the ZIP and run `WorkflowMonitorSetup.exe` as Administrator.
4. Select the local SQL Server instance and define the local administrator password.
5. Open Workflow Monitor locally and evaluate the Demo workflow.
6. The Demo supports up to 3 registered processes and 1 Worker/integration for 30 days.
7. After expiration, existing information remains available in read-only mode.

## 4. Professional or Enterprise purchase

1. Select Professional or Enterprise.
2. Select monthly, quarterly, semiannual or annual billing.
3. Enter the customer name and email and accept the privacy policy and purchase terms.
4. Continue to Mercado Pago.
5. After payment confirmation, return to the Workflow Monitor purchase-status page.
6. Link the purchase to the Workflow Monitor installation that will receive the license.

An Installation ID is not required before payment.

## 5. Linking the paid license to an installation

If Workflow Monitor is already installed:

1. Open that installation.
2. Go to `/installation`.
3. Copy the Installation ID.
4. Paste it into the purchase-status page.

If Workflow Monitor is not installed yet:

1. Download and install the official Demo first.
2. Open Workflow Monitor and go to `/installation`.
3. Copy the Installation ID.
4. Return to the purchase-status page and paste it there.

The commercial system then issues the signed license for that installation and prepares the customer-specific package.

## 6. Commercial delivery

When fulfillment is complete, the purchase-status page exposes a private time-limited download link. If SMTP delivery is enabled, the same type of private download link can also be sent to the customer email address.

Commercial customer packages are not published in the public GitHub repository.

## 7. Ongoing subscription lifecycle

Mercado Pago subscription events can update the commercial subscription state, including active, paused and cancelled states. The public product remains locally installed; commercial entitlement is represented by the signed license issued for the corresponding installation and billing period.

## Customer-facing URL conventions

Public URLs should remain short and semantic. Paths such as `/planes`, `/installation`, `/demo`, `/retorno` and `/entrega` are normal application routes. Internal hosting folder names, provider implementation details and development-only terminology should not be exposed in customer-facing links or copy.
