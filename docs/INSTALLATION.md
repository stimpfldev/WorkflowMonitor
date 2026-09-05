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
2. Verify the ZIP against the published SHA-256 checksum.
3. Extract the ZIP to a temporary folder.
4. Run `WorkflowMonitorSetup.exe`.
5. If Microsoft Defender SmartScreen displays **Windows protected your PC**, follow the guidance in the SmartScreen section below.
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

The current Workflow Monitor Demo installer is distributed **without an Authenticode digital signature from a trusted Windows code-signing certificate**. Because the executable is unsigned and may not yet have established Microsoft SmartScreen reputation, Windows can display the message **Windows protected your PC** when `WorkflowMonitorSetup.exe` is launched after being downloaded from the Internet.

This warning does **not by itself mean that Microsoft Defender detected malware**. SmartScreen also warns about unsigned or low-reputation applications. The warning is expected for the current unsigned Workflow Monitor installer.

Before continuing:

1. Download Workflow Monitor only from the official `stimpfldev/WorkflowMonitor` GitHub repository.
2. Verify that the SHA-256 checksum of the downloaded Demo ZIP matches the checksum published with the corresponding GitHub Release.
3. Do not run copies obtained from unrelated websites or unverified sources.

If the package came from the official repository and its SHA-256 checksum matches the published value, you can continue in the SmartScreen dialog using:

**More info → Run anyway**

The digital-signing limitation is documented openly so users can distinguish an expected unsigned-publisher warning from an antivirus malware detection. A future signed distribution may reduce or eliminate this warning depending on Microsoft SmartScreen reputation policies.
