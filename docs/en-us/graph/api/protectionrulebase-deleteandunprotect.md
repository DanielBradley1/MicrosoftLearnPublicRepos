<!-- Source: https://learn.microsoft.com/en-us/graph/api/protectionrulebase-deleteandunprotect?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-22 -->

# protectionRuleBase: deleteAndUnprotect

Namespace: microsoft.graph

Delete and unprotect all the artifacts protected by a dynamic [rule](https://learn.microsoft.com/en-us/graph/api/resources/protectionrulebase?view=graph-rest-1.0). This action is only applicable to dynamic rules.

The following points apply when you delete a dynamic rule and unprotect all artifacts it protects.

- The rule moves to the `deleteRequested` status when this action is performed on a dynamic rule.
- Unprotecting artifacts and deleting rules are asynchronous operations, and they might not complete immediately.
- This action resets the `dynamicRule` protection source. If the artifact is also protected by another protection source, it's only protected by that source afterward.
- No operation is allowed on a dynamic rule once a rule is in the `deleteRequested` state.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | BackupRestore-Configuration.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | BackupRestore-Configuration.ReadWrite.All | Not available. |

## HTTP request

```http
POST /solutions/backupRestore/oneDriveForBusinessProtectionPolicies/{oneDriveForBusinessProtectionPolicyId}/driveInclusionRules/{driveProtectionRuleId}/deleteAndUnprotect
POST /solutions/backupRestore/exchangeProtectionPolicies/{exchangeProtectionPolicyId}/mailboxInclusionRules/{mailboxProtectionRuleId}/deleteAndUnprotect
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this action returns a `202 Accepted` response code and a [protectionRuleBase](https://learn.microsoft.com/en-us/graph/api/resources/protectionrulebase?view=graph-rest-1.0) object in the response body.

## Examples

### Example 1: Delete and unprotect a driveInclusionRule associated with a onedriveForBusiness protection policy

The following example shows how to delete a **driveInclusionRule** associated with a [onedriveForBusinessProtectionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/onedriveforbusinessprotectionpolicy?view=graph-rest-1.0) and unprotect the units it protects.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
POST https://graph.microsoft.com/v1.0/solutions/backupRestore/oneDriveForBusinessProtectionPolicies/71633878-8321-4950-bfaf-ed285bdd1461/driveInclusionRules/61633878-8321-4950-bfaf-ed285bdd1461/deleteAndUnprotect
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

await client.api('/solutions/backupRestore/oneDriveForBusinessProtectionPolicies/71633878-8321-4950-bfaf-ed285bdd1461/driveInclusionRules/61633878-8321-4950-bfaf-ed285bdd1461/deleteAndUnprotect')
	.post();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 202 Accepted
Content-Type: application/json

{
  "value": {
    "@odata.type": "https://graph.microsoft.com/v1.0/$metadata#microsoft.graph.protectionRuleBase",
    "id": "61633878-8321-4950-bfaf-ed285bdd1461",
    "status": "deleteRequested",
    "createdDateTime": "2025-01-15T15:07:44.3043505Z",
    "lastModifiedDateTime": "2025-01-15T14:42:12.6779064Z",
    "isAutoApplyEnabled": true,
    "driveExpression": "(memberOf -any (group.id -in ['4e8e9b15-bfc8-40a2-aed0-3f65a22e2bd4']))",
    "createdBy": {
      "user": {
        "identity": "8aaaaec3-5dcb-4b47-9ef9-0dda3e95b9f4"
      }
    },
    "lastModifiedBy": {}
  }
}
```

### Example 2: Delete and unprotect a mailboxInclusionRule associated with an Exchange protection policy

The following example shows how to delete a **mailboxInclusionRule** associated with an [exchangeProtectionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/exchangeprotectionpolicy?view=graph-rest-1.0).

#### Request

The following example shows a request.

- [HTTP](#tabpanel_2_http)
- [JavaScript](#tabpanel_2_javascript)

```http
POST https://graph.microsoft.com/v1.0/solutions/backupRestore/exchangeProtectionPolicies/6b0991b9-e7d4-4794-86fa-2a3f2a4e3177/mailboxInclusionRules/52147fb9-2682-47bc-a8f6-6c38c1ff498d/deleteAndUnprotect
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

await client.api('/solutions/backupRestore/exchangeProtectionPolicies/6b0991b9-e7d4-4794-86fa-2a3f2a4e3177/mailboxInclusionRules/52147fb9-2682-47bc-a8f6-6c38c1ff498d/deleteAndUnprotect')
	.post();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 202 Accepted
Content-Type: application/json

{
  "value": {
    "@odata.type": "https://graph.microsoft.com/v1.0/$metadata#microsoft.graph.protectionRuleBase",
    "id": "52147fb9-2682-47bc-a8f6-6c38c1ff498d",
    "status": "deleteRequested",
    "createdDateTime": "2025-01-15T15:07:44.3043505Z",
    "lastModifiedDateTime": "2025-01-15T14:42:12.6779064Z",
    "isAutoApplyEnabled": true,
    "mailboxExpression": "(memberOf -any (group.id -in ['4e8e9b15-bfc8-40a2-aed0-3f65a22e2bd4']))",
    "createdBy": {
        "user": {
            "identity": "8aaaaec3-5dcb-4b47-9ef9-0dda3e95b9f4"
        }
    },
    "lastModifiedBy": {},
    "error": {}
  }
}
```
