<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/api/update-alert -->
<!-- Sitemap-Last-Modified: 2025-11-24 -->

# Update alert

## API description

Updates properties of existing [Alert](https://learn.microsoft.com/en-us/defender-endpoint/api/alerts).

Submission of **comment** is available with or without updating properties.

Updatable properties are: `status`, `determination`, `classification`, and `assignedTo`.

## Limitations

- You can update alerts that available in the API. For more information, see [List Alerts](https://learn.microsoft.com/en-us/defender-endpoint/api/get-alerts).
- Rate limitations for this API are 100 calls per minute and 1,500 calls per hour.

## Permissions

When obtaining a token using user credentials:

- The user needs to have at least the following role permission: 'Alerts investigation'. For more information, see [Create and manage roles](https://learn.microsoft.com/en-us/defender-endpoint/user-roles).
- The user needs to have access to the device associated with the alert, based on device group settings. For more information, see [Create and manage device groups](https://learn.microsoft.com/en-us/defender-endpoint/machine-groups).

One of the following permissions is required to call this API. For more information on how to choose permissions, see [Use Microsoft Defender for Endpoint APIs](https://learn.microsoft.com/en-us/defender-endpoint/api/apis-intro)

| Permission type | Permission | Permission display name |
| --- | --- | --- |
| Application | Alerts.ReadWrite.All | 'Read and write all alerts' |
| Delegated \(work or school account\) | Alert.ReadWrite | 'Read and write alerts' |

## HTTP request

```http
PATCH /api/alerts/{id}
```

## Request headers

| Name | Type | Description |
| --- | --- | --- |
| Authorization | String | Bearer {token}. **Required**. |
| Content-Type | String | application/json. **Required**. |

## Request body

In the request body, supply the values for the relevant fields that should be updated.

Existing properties that aren't included in the request body will maintain their previous values or be recalculated based on changes to other property values.

For best performance, you shouldn't include existing values that haven't change.

| Property | Type | Description |
| --- | --- | --- |
| Status | String | Specifies the current status of the alert. The property values are: 'New', 'InProgress' and 'Resolved'. |
| assignedTo | String | Owner of the alert |
| Classification | String | Specifies the specification of the alert. The property values are: `TruePositive`, `InformationalExpectedActivity`, and `FalsePositive`. |
| Determination | String | Specifies the determination of the alert.<br><br>Possible determination values for each classification are:  <br><br><br><li> <b>True positive</b>: <code>Multistage attack</code> (MultiStagedAttack), <code>Malicious user activity</code> (MaliciousUserActivity), <code>Compromised account</code> (CompromisedUser) – consider changing the enum name in public API accordingly, <code>Malware</code> (Malware), <code>Phishing</code> (Phishing), <code>Unwanted software</code> (UnwantedSoftware), and <code>Other</code> (Other). </li><br><br><li> <b>Informational, expected activity:</b> <code>Security test</code> (SecurityTesting), <code>Line-of-business application</code> (LineOfBusinessApplication), <code>Confirmed activity</code> (ConfirmedActivity) - consider changing the enum name in public API accordingly, and <code>Other</code> (Other). </li><br><br><li>  <b>False positive:</b> <code>Not malicious</code> (NotMalicious) - consider changing the enum name in public API accordingly, <code>Not enough data to validate</code> (InsufficientData), and <code>Other</code> (Other).</li> |
| Comment | String | Comment to be added to the alert. |

Note

Around August 29, 2022, previously supported alert determination values \('Apt' and 'SecurityPersonnel'\) will be deprecated and no longer available via the API.

## Response

If successful, this method returns 200 OK, and the [alert](https://learn.microsoft.com/en-us/defender-endpoint/api/alerts) entity in the response body with the updated properties. If alert with the specified ID wasn't found - 404 Not Found.

## Example

### Request

Here's an example of the request.

```http
PATCH https://api.security.microsoft.com/api/alerts/121688558380765161_2136280442
```

```json
{
    "status": "Resolved",
    "assignedTo": "secop2@contoso.com",
    "classification": "FalsePositive",
    "determination": "Malware",
    "comment": "Resolve my alert and assign to secop2"
}
```
