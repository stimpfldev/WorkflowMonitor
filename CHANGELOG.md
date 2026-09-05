<p>
  <img src="assets/workflow-monitor-mark.svg" alt="Workflow Monitor" width="56" />
</p>

# Changelog

## 1.1.3 — 2026-09-05

- Corrected Spanish CSV export for reliable opening in Excel while preserving accented text.
- Confirmed installer product/display version as 1.1.3.
- Finalized the validated Windows installer/uninstaller and packaging hardening for the 1.1.3 Demo.
- Updated installation guidance for the current unsigned Authenticode distribution and Microsoft Defender SmartScreen behavior.
- Refreshed public screenshots, walkthrough, Demo documentation and formal Word documentation for the 1.1.3 release.

## 1.1.2 — 2026-09-04

- Permanent installation under `C:\Program Files\Workflow Monitor`.
- Reliable uninstall cleanup with optional database preservation or removal.
- SQL Server instance persisted from installation and reused during uninstall.
- Installer and uninstaller branding loaded without locking image files.
- Improved launcher lifecycle to avoid premature Windows compatibility warnings.
- Reusable sample CSV installed under `C:\SqlWorkflowMonitor\Data\Samples`.
- Installer completion-screen and authenticated-dashboard visual cleanup.
- Shared packaging improvements applied to Professional and Enterprise generation where applicable.

## 1.1.x

The 1.1.x line provides the current Windows local monitoring workflow with Web/API, Worker integration, SQL Server persistence, bilingual UI, execution metrics, filters and CSV export.
