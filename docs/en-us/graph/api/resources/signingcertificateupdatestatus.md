<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/signingcertificateupdatestatus?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# signingCertificateUpdateStatus resource type

Namespace: microsoft.graph

Provides status and timestamp of the last update of the signing certificate.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| certificateUpdateResult | String | Status of the last certificate update. Read-only. For a list of statuses, see [certificateUpdateResult status](#certificateupdateresult-status). |
| lastRunDateTime | DateTimeOffset | Date and time in ISO 8601 format and in UTC time when the certificate was last updated. Read-only. |

### certificateUpdateResult status

| Value | Description |
| :--- | :--- |
| success | The attempt was successful. |
| unknownError | Do not know the reason for failure. |
| internalServerError | Something went wrong on our side. |
| noValidExistingCertFound | No valid existing signing certificate was found. |
| noStsAuthUrlFound | No STS Auth Url was found. |
| noFederationProtocolFound | No federation protocol was found. |
| noNewCertificateFound | No new certificate was found. |
| couldNotAccessRemoteHost | Could not reach the provider to get the new certificates. |
| connectionError | There was a connection error |
| xmlParsingError | Failed to parse the XML |
| badRequest | Received BadRequest error from the fed metadata request. |
| unauthorized | Received Unauthorized error from the fed metadata request. |
| forbidden | Received Forbidden error from the fed metadata request. |
| notFound | Received NotFound error from the fed metadata request. |
| providerError | Received InternalServerError from the provider. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.signingCertificateUpdateStatus",
  "certificateUpdateResult": "String",
  "lastRunDateTime": "String (timestamp)"
}
```
