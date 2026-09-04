<p>
  <img src="../assets/workflow-monitor-mark.svg" alt="Workflow Monitor" width="56" />
</p>

# Workflow Monitor Demo — Installation

## Before you start

You need:

- Windows x64
- Access to a SQL Server instance
- Administrator permissions during installation
- A modern web browser

The Demo package is self-contained. A separate .NET runtime is not required.

## Install

1. Download the latest Demo ZIP from the repository **Releases** page.
2. Optionally verify the ZIP against the published SHA-256 checksum.
3. Extract the ZIP to a temporary folder.
4. Run `WorkflowMonitorSetup.exe`.
5. If Microsoft Defender SmartScreen appears for the unsigned installer, review the publisher information and choose **Run anyway** only if the package was downloaded from this repository and its checksum matches the published value.
6. Enter the SQL Server instance. For the default local SQL Server instance, use `.`.
7. Define the administrator password. The username is `admin` and the password must contain at least 12 characters.
8. Complete the installation.
9. Open Workflow Monitor from the completion screen or browse to the local URL shown by the installer.

## Installed components

The Demo installs under:

```text
C:\Program Files\Workflow Monitor
```

and registers two Windows services:

```text
SqlWorkflowMonitor Web
SqlWorkflowMonitor Worker
```

Workflow data folders are created under:

```text
C:\SqlWorkflowMonitor\Data
```

The reusable example file is installed at:

```text
C:\SqlWorkflowMonitor\Data\Samples\customers.csv
```

To test processing, copy the sample file into:

```text
C:\SqlWorkflowMonitor\Data\Input
```

The Demo Worker checks for input periodically, so processing may take up to approximately 60 seconds.

## Uninstall

Use Windows **Installed apps** and uninstall **Workflow Monitor Demo**.

The uninstaller allows you to choose whether the `SqlWorkflowMonitor` database is preserved or removed.

When the database-preservation option is used, the application services, installation files and Windows registration are removed while the database remains available in SQL Server.

## Microsoft Defender SmartScreen

The current 1.1.2 Demo installer is not code-signed with a trusted Windows code-signing certificate. Windows can therefore show a SmartScreen warning after the package is downloaded from the Internet.

Always download the Demo from this official repository and verify the published SHA-256 checksum before installation.
