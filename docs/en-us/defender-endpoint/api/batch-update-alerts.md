<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/api/batch-update-alerts -->
<!-- Sitemap-Last-Modified: 2025-11-24 -->

# Batch update alerts

## API description

Updates properties of a batch of existing [Alerts](https://learn.microsoft.com/en-us/defender-endpoint/api/alerts).

Submission of **comment** is available with or without updating properties.

Updatable properties are: `status`, `determination`, `classification`, and `assignedTo`.

## Limitations

- You can update alerts that are available in the API. For more information, see [List Alerts](https://learn.microsoft.com/en-us/defender-endpoint/api/get-alerts).
- Rate limitations for this API are 10 calls per minute and 500 calls per hour.

## Permissions

When obtaining a token using user credentials:

- The user needs to have at least the following role permission: 'Alerts investigation'. For more information, see [Create and manage roles](https://learn.microsoft.com/en-us/defender-endpoint/user-roles).
- The user needs to have access to the device associated with the alert, based on device group settings. For more information, see [Create and manage device groups](https://learn.microsoft.com/en-us/defender-endpoint/machine-groups).

One of the following permissions is required to call this API. For more information on how to choose permissions, see [Use Microsoft Defender for Endpoint APIs](https://learn.microsoft.com/en-us/defender-endpoint/api/apis-intro)

| Permission type | Permission | Permission display name |
| --- | --- | --- |
| Application | Alert.ReadWrite.All | 'Read and write all alerts' |
| Delegated \(work or school account\) | Alert.ReadWrite | 'Read and write alerts' |

## HTTP request

```http
POST /api/alerts/batchUpdate
```

## Request headers

| Name | Type | Description |
| --- | --- | --- |
| Authorization | String | Bearer {token}. **Required**. |
| Content-Type | String | application/json. **Required**. |

## Request body

In the request body, supply the IDs of the alerts to be updated and the values of the relevant fields that you wish to update for these alerts.

Existing properties that aren't included in the request body will maintain their previous values or be recalculated based on changes to other property values.

For best performance you shouldn't include existing values that haven't changed.

| Property | Type | Description |
| --- | --- | --- |
| alertIds | List<String> | A list of the IDs of the alerts to be updated. **Required** |
| status | String | Specifies the updated status of the specified alerts. The property values are: 'New', 'InProgress' and 'Resolved'. |
| assignedTo | String | Owner of the specified alerts |
| classification | String | Specifies the specification of the specified alerts. The property values are: `TruePositive`, `Informational, expected activity`, and `FalsePositive`. |
| determination | String | Specifies the determination of the specified alerts.<br><br>Possible determination values for each classification are:  <br><br><br><li> <b>True positive</b>: <code>Multistage attack</code> (MultiStagedAttack), <code>Malicious user activity</code> (MaliciousUserActivity), <code>Compromised account</code> (CompromisedUser) – consider changing the enum name in public API accordingly, <code>Malware</code> (Malware), <code>Phishing</code> (Phishing), <code>Unwanted software</code> (UnwantedSoftware), and <code>Other</code> (Other). </li><br><br><li> <b>Informational, expected activity:</b> <code>Security test</code> (SecurityTesting), <code>Line-of-business application</code> (LineOfBusinessApplication), <code>Confirmed activity</code> (ConfirmedUserActivity) - consider changing the enum name in public API accordingly, and <code>Other</code> (Other). </li><br><br><li>  <b>False positive:</b> <code>Not malicious</code> (Clean) - consider changing the enum name in public API accordingly, <code>Not enough data to validate</code> (InsufficientData), and <code>Other</code> (Other).</li> |
| comment | String | Comment to be added to the specified alerts. |

Note

Around August 29, 2022, previously supported alert determination values \('Apt' and 'SecurityPersonnel'\) will be deprecated and no longer available via the API.

## Response

If successful, this method returns 200 OK, with an empty response body.

## Example

### Request

Here's an example of the request.

```http
POST https://api.security.microsoft.com/api/alerts/batchUpdate
```

```json
{
    "alertIds": ["da637399794050273582_760707377", "da637399989469816469_51697947354"],
    "status": "Resolved",
    "assignedTo": "secop2@contoso.com",
    "classification": "FalsePositive",
    "determination": "Malware",
    "comment": "Resolve my alert and assign to secop2"
}
```
