<!-- Source: https://learn.microsoft.com/en-us/entra/msal/dotnet/advanced/monitoring -->
<!-- Sitemap-Last-Modified: 2025-05-20 -->

# Monitoring applications using MSAL.NET

To ensure authentication services using MSAL.NET are running correctly, MSAL provides many ways to monitor its behavior so that issues can be identified and addressed before they occur in production. The incorrect use of MSAL \(as it relates to token lifecycle and cache\) doesn't lead to immediate failures, however sometimes they'll bubble up under high traffic scenarios after the app is in production for a period of time.

For example, if only one instance of a [confidential client application](https://learn.microsoft.com/en-us/entra/identity-platform/msal-client-applications#public-client-and-confidential-client-authorization) is used and MSAL isn't configured to serialize the token cache, the cache will grow forever. Another issue arises when creating a new confidential client application and not utilizing the cache which will lead to issues such as throttling from the identity provider. For recommendations on how to utilize MSAL appropriately, see [High Availability](https://learn.microsoft.com/en-us/entra/msal/dotnet/advanced/high-availability).

## Logging

One of the tools MSAL provides to combat production issues is logging errors when MSAL isn't properly configured. It's critical to enable logging whenever possible to monitor logs for errors and help in the diagnosis of problematic events. See [Logging in MSAL.NET](https://learn.microsoft.com/en-us/entra/msal/dotnet/advanced/exceptions/msal-logging) for details.

The following errors will be logged in MSAL:

- When using an authority ending in `/common` or `/organizations` for client credential authentication \([AcquireTokenForClient\(IEnumerable<String>\)](https://learn.microsoft.com/en-us/dotnet/api/microsoft.identity.client.confidentialclientapplication.acquiretokenforclient#microsoft-identity-client-confidentialclientapplication-acquiretokenforclient\(system-collections-generic-ienumerable\(\(system-string\)\)\))\).

  - The current authority is targeting the `/common` or `/organizations` endpoint which is not recommended. See [Client credential flows](https://learn.microsoft.com/en-us/entra/msal/dotnet/acquiring-tokens/web-apps-apis/client-credential-flows) for more details.

- When the default internal token cache is used while using confidential client applications.

  - The default token cache provided by MSAL is not designed to be performant when used in confidential client applications. Refer to [Token cache serialization in MSAL.NET](https://learn.microsoft.com/en-us/entra/msal/dotnet/how-to/token-cache-serialization?tabs=aspnetcore) for more details.

## Metrics

In addition to logging, MSAL exposes important metrics in [AuthenticationResult.AuthenticationResultMetadata](https://learn.microsoft.com/en-us/dotnet/api/microsoft.identity.client.authenticationresult.authenticationresultmetadata#microsoft-identity-client-authenticationresult-authenticationresultmetadata). See [Add monitoring around MSAL operations](https://learn.microsoft.com/en-us/entra/msal/dotnet/advanced/high-availability#add-monitoring-around-msal-operations) for more details.

- [DurationTotalInMs](https://learn.microsoft.com/en-us/dotnet/api/microsoft.identity.client.authenticationresultmetadata.durationtotalinms#microsoft-identity-client-authenticationresultmetadata-durationtotalinms) - total time spent in MSAL acquiring a token, including network calls and cache operations. Create an alert on overall high latency \(more than 1 second\). Note that the first ever token acquisition call usually makes an extra HTTP call.
- [DurationInCacheInMs](https://learn.microsoft.com/en-us/dotnet/api/microsoft.identity.client.authenticationresultmetadata.durationincacheinms#microsoft-identity-client-authenticationresultmetadata-durationincacheinms) - time spent loading or saving the token cache, which is customized by the app developer \(for example, save to Redis\). Create an alert on spikes.

  Note

  To understand how to customize token caching, see [Token cache serialization in MSAL.NET](https://learn.microsoft.com/en-us/azure/active-directory/develop/msal-net-token-cache-serialization).
- [DurationInHttpInMs](https://learn.microsoft.com/en-us/dotnet/api/microsoft.identity.client.authenticationresultmetadata.durationinhttpinms#microsoft-identity-client-authenticationresultmetadata-durationinhttpinms) - time spent making HTTP calls to the identity provider. Create an alert on spikes.
- [TokenSource](https://learn.microsoft.com/en-us/dotnet/api/microsoft.identity.client.authenticationresultmetadata.tokensource#microsoft-identity-client-authenticationresultmetadata-tokensource)- indicates the source of the token - typically the cache or the identity provider. Tokens are retrieved from the cache much faster \(for example, ~100 ms versus ~700 ms\). This metric can be used to monitor the cache hit ratio.
- [CacheRefreshReason](https://learn.microsoft.com/en-us/dotnet/api/microsoft.identity.client.authenticationresultmetadata.cacherefreshreason#microsoft-identity-client-authenticationresultmetadata-cacherefreshreason) - specifies the reason for fetching the access token from the identity provider. See [CacheRefreshReason](https://learn.microsoft.com/en-us/dotnet/api/microsoft.identity.client.cacherefreshreason). Use in conjunction with `TokenSource`.
- [TokenEndpoint](https://learn.microsoft.com/en-us/dotnet/api/microsoft.identity.client.authenticationresultmetadata.tokenendpoint#microsoft-identity-client-authenticationresultmetadata-tokenendpoint) - the actual token endpoint URI used to fetch the token. Useful to understand how MSAL resolves the tenant in silent calls and the region in regional calls.

  Note

  Regionalization is available only to internal Microsoft applications.
- [RegionDetails](https://learn.microsoft.com/en-us/dotnet/api/microsoft.identity.client.authenticationresultmetadata.regiondetails#microsoft-identity-client-authenticationresultmetadata-regiondetails) - the details about the region used to make call, such as the region used and any auto-detection error.

  Note

  Regionalization is available only to internal Microsoft applications.

## OpenTelemetry

Starting with MSAL 4.58.0, the library supports [OpenTelemetry](https://opentelemetry.io/) - a set of APIs that enable instrumentation, generation, and collection of telemetry data in a consistent and standardized manner. To get started, ensure that you;

1. Install the latest version of [MSAL.NET](https://www.nuget.org/packages/Microsoft.Identity.Client).
2. Add the [OpenTelemetry](https://www.nuget.org/packages/OpenTelemetry#readme-body-tab) package dependency to your project.
3. Add an exporter dependency, that allows you to export logs, for example, the [Console exporter for OpenTelemetry.NET](https://www.nuget.org/packages/OpenTelemetry.Exporter.Console/1.7.0-alpha.1).

Note

While the console exporter is a good start for local debugging and diagnostics, it's not the best choice for production-deployed applications. We recommend checking out the [official exporter documentation](https://opentelemetry.io/docs/instrumentation/net/exporters/) to learn more about available options. If you are hosting applications on Azure, you may consider ingesting OpenTelemetry data in [Azure Data Explorer](https://learn.microsoft.com/en-us/azure/data-explorer/open-telemetry-connector?tabs=command-line) or [Azure Monitor](https://learn.microsoft.com/en-us/azure/azure-monitor/app/opentelemetry-enable?tabs=aspnetcore).

In your application initialization code, prior to bootstrapping the MSAL authentication client \(e.g., [PublicClientApplication](https://learn.microsoft.com/en-us/dotnet/api/microsoft.identity.client.publicclientapplication) or [ConfidentialClientApplication](https://learn.microsoft.com/en-us/dotnet/api/microsoft.identity.client.confidentialclientapplication)\), declare a new [`MeterProvider`](https://opentelemetry.io/docs/specs/otel/metrics/api/#meterprovider) instance, using the following code.

```csharp
using var meterProvider = Sdk.CreateMeterProviderBuilder()
    .AddMeter("MicrosoftIdentityClient_Common_Meter")
    .AddConsoleExporter()
    .Build();
```

This will initialize the meter provider and use the built-in MSAL.NET meter \(`MicrosoftIdentityClient_Common_Meter`\) that captures a series of counters and histograms. When a console exporter is used, you should see the output being piped directly in the terminal:

![Example of OpenTelemetry outputting metrics to the terminal](https://learn.microsoft.com/en-us/entra/msal/dotnet/media/msal-net-logging/otel.png)

The following section outlines the supported counters and histograms for the default meter.

### Counters

#### `msalsuccess_counter`

Counter to capture aggregation of successful requests in MSAL.

##### Metadata

| Field | Description |
| :--- | :--- |
| `MsalVersion` | Version of MSAL used. |
| `Platform` | .NET SKU used. |
| `ApiId` | ID for the API used for token acquisition. |
| `TokenSource` | Source of token \(e.g., identity provider or cache\). |
| `CacheRefreshReason` | Reason for cache refresh. |
| `CacheLevel` | L1, L2, or Unknown when the custom cache is used but level is not recorded. |

#### `msalfailure_counter`

Counter to capture aggregation of failed requests in MSAL.

##### Metadata

| Field | Description |
| :--- | :--- |
| `MsalVersion` | Version of MSAL used. |
| `Platform` | .NET SKU used. |
| `ErrorCode` | Microsoft Entra ID error code in case of `MsalServiceException`, `MsalErrorCode` in case of `MsalClientException` or name of the exception in case it isn't an `MsalException`. |
| `ApiId` | ID for the API used for token acquisition. |
| `CacheRefreshReason` | Reason for cache refresh. |

### Histograms

#### `MsalTotalDuration_1a_histogram`

Histogram to capture total latency in milliseconds for token acquisition through MSAL.

##### Metadata

| Field | Description |
| :--- | :--- |
| `MsalVersion` | Version of MSAL used. |
| `Platform` | .NET SKU used. |
| `ApiId` | ID for the API used for token acquisition. |
| `CacheLevel` | L1, L2, or Unknown when the custom cache is used but level is not recorded. |
| `TokenSource` | Source of token \(e.g., identity provider or cache\). |
| `CacheRefreshReason` | Reason for cache refresh. |

#### `MsalDurationInL1CacheInUs_1b_histogram`

Histogram to capture latency when an L1 cache is used. Values are in microseconds for token acquisition through MSAL.

##### Metadata

| Field | Description |
| :--- | :--- |
| `MsalVersion` | Version of MSAL used. |
| `Platform` | .NET SKU used. |
| `ApiId` | ID for the API used for token acquisition. |
| `CacheLevel` | L1, L2, or Unknown when the custom cache is used but level is not recorded. |
| `TokenSource` | Source of token \(e.g., identity provider or cache\). |
| `CacheRefreshReason` | Reason for cache refresh. |

#### `MsalDurationInL2Cache_1a_histogram`

Histogram to capture L2 cache latency in milliseconds for token acquisition through MSAL.

##### Metadata

| Field | Description |
| :--- | :--- |
| `MsalVersion` | Version of MSAL used. |
| `Platform` | .NET SKU used. |
| `ApiId` | ID for the API used for token acquisition. |
| `CacheRefreshReason` | Reason for cache refresh. |

#### `MsalDurationInHttp_1a_histogram`

Histogram to capture HTTP latency in milliseconds for token acquisition through MSAL.

##### Metadata

| Field | Description |
| :--- | :--- |
| `MsalVersion` | Version of MSAL used. |
| `Platform` | .NET SKU used. |
| `ApiId` | ID for the API used for token acquisition. |

### Additional information

For additional information on the use of OpenTelemetry with .NET applications, refer to [.NET observability with OpenTelemetry](https://learn.microsoft.com/en-us/dotnet/core/diagnostics/observability-with-otel).
