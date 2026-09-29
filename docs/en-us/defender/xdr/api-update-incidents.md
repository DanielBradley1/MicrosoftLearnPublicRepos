<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/api-update-incidents -->
<!-- Sitemap-Last-Modified: 2025-04-25 -->

# Update incidents API

Note

**Try our new APIs using MS Graph security API**. Find out more at: [Use the Microsoft Graph security API - Microsoft Graph \| Microsoft Learn](https://learn.microsoft.com/en-us/graph/api/resources/security-api-overview). For information about the new *update incident* API using MS Graph security API, see [Update incident](https://learn.microsoft.com/en-us/graph/api/security-incident-update).

Important

Some information relates to prereleased product which may be substantially modified before it's commercially released. Microsoft makes no warranties, express or implied, with respect to the information provided here.

## API description

Updates properties of existing incident. Updatable properties are: `status`, `determination`, `classification`, `assignedTo`, `tags`, and `comments`.

### Quotas, resource allocation, and other constraints

1. You can make up to 50 calls per minute or 1,500 calls per hour before you hit the throttling threshold.
2. You can set the `determination` property only if `classification` is set to TruePositive.

If your request is throttled, it returns a `429` response code. The response body indicates the time when you can begin making new calls.

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Access the Microsoft Defender APIs](https://learn.microsoft.com/en-us/defender-xdr/api-access).

| Permission type | Permission | Permission display name |
| --- | --- | --- |
| Application | Incident.ReadWrite.All | Read and write all incidents |
| Delegated \(work or school account\) | Incident.ReadWrite | Read and write incidents |

Note

When obtaining a token using user credentials, the user needs to have permission to update the incident in the portal.

## HTTP request

```HTTP
PATCH /api/incidents/{id}
```

## Request headers

| Name | Type | Description |
| --- | --- | --- |
| Authorization | String | Bearer {token}. **Required**. |
| Content-Type | String | application/json. **Required**. |

## Request body

In the request body, supply the values for the fields that should be updated. Existing properties that aren't included in the request body maintain their values, unless they have to be recalculated due to changes to related values. For best performance, you should omit existing values that didn't change.

| Property | Type | Description |
| --- | --- | --- |
| status | Enum | Specifies the current status of the incident. Possible values are: `Active`, `Resolved`, `InProgress`, and `Redirected`. |
| assignedTo | string | Owner of the incident. |
| classification | Enum | Specification of the incident. Possible values are: `TruePositive` \(True positive\), `InformationalExpectedActivity` \(Informational, expected activity\), and `FalsePositive` \(False Positive\). |
| determination | Enum | Specifies the determination of the incident.<br><br>Possible determination values for each classification are:  <br><br><br><li> <b>True positive</b>: <code>MultiStagedAttack</code> (Multi staged attack), <code>MaliciousUserActivity</code> (Malicious user activity), <code>CompromisedAccount</code> (Compromised account) – consider changing the enum name in public api accordingly, <code>Malware</code> (Malware), <code>Phishing</code> (Phishing), <code>UnwantedSoftware</code> (Unwanted software), and <code>Other</code> (Other). </li><br><br><li> <b>Informational, expected activity:</b> <code>SecurityTesting</code> (Security test), <code>LineOfBusinessApplication</code> (Line-of-business application), <code>ConfirmedActivity</code> (Confirmed activity) - consider changing the enum name in public api accordingly, and <code>Other</code> (Other). </li><br><br><li>  <b>False positive:</b> <code>Clean</code> (Not malicious) - consider changing the enum name in public api accordingly, <code>NoEnoughDataToValidate</code> (Not enough data to validate), and <code>Other</code> (Other).</li> |
| tags | string list | List of Incident tags. |
| comment | string | Comment to be added to the incident. |

Note

Around August 29, 2022, previously supported alert determination values \('Apt' and 'SecurityPersonnel'\) will be deprecated and no longer available via the API.

## Response

If successful, this method returns `200 OK`. The response body contains the incident entity with updated properties. If an incident with the specified ID wasn't found, the method returns `404 Not Found`.

## Example

### Request example

Here's an example of the request.

```HTTP
 PATCH https://api.security.microsoft.com/api/incidents/{id}
```

### Request data example

```json
{
    "status": "Resolved",
    "assignedTo": "secop2@contoso.com",
    "classification": "TruePositive",
    "determination": "Malware",
    "tags": ["Yossi's playground", "Don't mess with the Zohan"],
    "comment": "pen testing"
}
```

## Related articles

- [Use the Microsoft Graph security API - Microsoft Graph \| Microsoft Learn](https://learn.microsoft.com/en-us/graph/api/resources/security-api-overview)
- [Access the Microsoft Defender XDR APIs](https://learn.microsoft.com/en-us/defender-xdr/api-access)
- [Learn about API limits and licensing](https://learn.microsoft.com/en-us/legal/microsoft-365/api-terms)
- [Understand error codes](https://learn.microsoft.com/en-us/defender-xdr/api-error-codes)
- [Incident APIs](https://learn.microsoft.com/en-us/defender-xdr/api-incident)
- [List incidents](https://learn.microsoft.com/en-us/defender-xdr/api-list-incidents)
- [Incidents overview](https://learn.microsoft.com/en-us/defender-xdr/incidents-overview)

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender XDR Tech Community](https://techcommunity.microsoft.com/t5/microsoft-365-defender/bd-p/MicrosoftThreatProtection).
