<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/monitor-apps?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-09-25 -->

# Monitor apps \(preview\)

\[This article is prerelease documentation and is subject to change.\]

Apps provide visibility at three levels:

| Level | Description |
| --- | --- |
| [App telemetry](#app-telemetry) | Runtime metrics from your running app, which you forward to Application Insights or any monitoring tool you choose. |
| [Platform monitoring](#platform-monitoring) | Build and deploy health from the CLI, plus tenant-wide usage analytics and operational health in the Microsoft 365 admin center. |
| [CLI telemetry](#cli-telemetry) | Anonymized usage and diagnostic data from the `ms` CLI itself, which you can turn off. |

## App telemetry

The Microsoft Copilot Managed Runtime SDK reports runtime metrics, such as session load performance and network request summaries, to a logger you provide. You decide where those metrics go. [Azure Monitor Application Insights](https://learn.microsoft.com/en-us/azure/azure-monitor/app/app-insights-overview) is a common choice, but the same pattern works for any monitoring tool. The platform delivers the metric payloads; your logger implementation decides how to handle them.

Note

The app captures telemetry only after it loads successfully. Startup failures, such as an app blocked from loading, don't appear here. They surface in platform monitoring.

### Set up Application Insights

1. [Create an **Application Insights** resource](https://learn.microsoft.com/en-us/azure/azure-monitor/app/create-workspace-resource#create-an-application-insights-resource) in the [Azure portal](https://portal.azure.com/) and copy its connection string.
2. Install the Application Insights web SDK in your project.

   ```bash
   npm install @microsoft/applicationinsights-web
   ```

3. Initialize Application Insights in your app.

   ```typescript
   import { ApplicationInsights } from '@microsoft/applicationinsights-web';

   const appInsights = new ApplicationInsights({
     config: {
       connectionString: 'InstrumentationKey=<YOUR_KEY>;IngestionEndpoint=<YOUR_ENDPOINT>',
     },
   });
   appInsights.loadAppInsights();
   ```

4. Register a logger with the Copilot Managed Runtime SDK so the platform forwards metrics to Application Insights. Register it once.

   ```typescript
   import { setConfig } from '@microsoft/managed-apps';
   import type { Metric } from '@microsoft/managed-apps';

   setConfig({
     logger: {
       logMetric: (value: Metric) => {
         appInsights.trackEvent({ name: value.type }, value.data);
       },
     },
   });
   ```

5. If Content Security Policy \(CSP\) is enforced in your environment, the default policy blocks telemetry from reaching Application Insights, because `connect-src` allows only your app's own origin. Have an administrator add the Application Insights ingestion origins to `connect-src`. See [Configure Content Security Policy \(preview\)](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/content-security-policy?view=o365-worldwide) to identify the blocked origins and update the directive.

### View the data

In your Application Insights resource, open **Monitoring** > **Logs** and query the [`customEvents` table](https://learn.microsoft.com/en-us/azure/azure-monitor/app/data-model-complete#custom-measurements) to see the metrics your app sends. The SDK reports built-in metrics for session load and network requests, and you can log your own events by calling the Application Insights APIs directly at the points you care about.

Important

Avoid logging sensitive or unnecessary data, and always follow your organization's compliance guidelines.

## Platform monitoring

Beyond per-app telemetry, administrators can see every app in the tenant in the Microsoft 365 admin center. They get **operational health metrics with alerting** to detect and resolve problems before they affect users.

These experiences require no setup from the developer. Apps automatically appear in the centralized inventory and monitoring.

[Learn how to add alerts for your apps](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/apps/visibility-monitoring?view=o365-worldwide#create-alerts-for-your-apps)

## CLI telemetry

The `ms` CLI sends anonymized telemetry by default to help improve the product. It captures usage and diagnostic signals, such as which commands run, whether they succeed, and performance and error data. It doesn't collect your source code or your app's data.

Use the [`ms telemetry` commands](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/ms-cli-command-reference?view=o365-worldwide#telemetry) to control collection.

Check the current setting:

```bash
ms telemetry status
```

Turn telemetry off:

```bash
ms telemetry disable
```

Turn it back on:

```bash
ms telemetry enable
```

Both [`enable`](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/ms-cli-command-reference?view=o365-worldwide#ms-telemetry-enable) and [`disable`](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/ms-cli-command-reference?view=o365-worldwide#ms-telemetry-disable) accept two flags that select what they apply to:

- `--remote`: Controls sending telemetry to the service. This flag is the default when no flag is given.
- `--console`: Controls printing telemetry events to your local console, which is useful for seeing exactly what the CLI would emit.

Pass both flags to toggle both targets at once.

### Build and deploy telemetry

Every build the platform runs produces a record you can inspect from the CLI. Use [`ms app build-status`](https://learn.microsoft.com/en-us/microsoft-365/managed-apps/developer/ms-cli-command-reference?view=o365-worldwide#ms-app-build-status) to check the status and outcome of a build:

```bash
ms app build-status --app <name> --commit <sha>
```

If a build failed, the output includes the reason, so you can fix the code and push again. Because each deploy is backed by a build, this is also how you trace what's currently live and roll back to a known-good commit.
