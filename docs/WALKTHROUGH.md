<p>
  <img src="../assets/workflow-monitor-mark.svg" alt="Workflow Monitor" width="56" />
</p>

# Workflow Monitor Demo — Quick walkthrough

This walkthrough shows the validated local Demo flow on Windows.

## 1. Install and sign in

1. Download the Demo ZIP from the official GitHub Release.
2. Verify the published SHA-256 checksum.
3. Extract the ZIP and run `WorkflowMonitorSetup.exe` as Administrator.
4. If Windows SmartScreen warns about the unsigned installer, follow the guidance in [INSTALLATION.md](INSTALLATION.md).
5. Complete the installation and open the local login page.
6. Sign in with the administrator account created during installation.

## 2. Monitor executions

The execution monitor shows the Demo status, registered process and Worker limits, execution counters, filters, CSV export and execution history.

![Workflow Monitor execution monitor](../assets/screenshots/dashboard.png)

## 3. Run the sample Worker flow

The installer provides a reusable sample file at:

```text
C:\SqlWorkflowMonitor\Data\Samples\customers.csv
```

Copy it to:

```text
C:\SqlWorkflowMonitor\Data\Input\customers.csv
```

The Demo Worker checks the input folder every 60 seconds. After processing, refresh the dashboard. A successful **Customer import / Importación de clientes** execution should appear.

## 4. Review execution details

Open **View detail / Ver detalle** to inspect execution status, timestamps, duration, errors and processing metrics.

![Workflow Monitor execution detail](../assets/screenshots/execution-detail.png)

## 5. Filter execution history

Use the status, process and date filters to narrow the execution list. Sorting, pagination and CSV export remain available for the filtered result.

![Workflow Monitor filtered executions](../assets/screenshots/filtered-executions.png)

## 6. Export CSV

Select **Export CSV / Exportar CSV** to download the current filtered execution list. Spanish and English exports are supported, including accented Spanish text when opened directly in Microsoft Excel.

## Demo limits

- 30-day technical evaluation
- Up to 3 registered processes
- 1 Worker/integration
- CSV export enabled
- Read-only access to recorded history after expiration

For complete installation and security guidance, see [INSTALLATION.md](INSTALLATION.md) and [SECURITY-DEPLOYMENT.md](SECURITY-DEPLOYMENT.md).
