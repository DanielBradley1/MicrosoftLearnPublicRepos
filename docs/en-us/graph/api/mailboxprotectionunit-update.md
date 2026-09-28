<!-- Source: https://learn.microsoft.com/en-us/graph/api/mailboxprotectionunit-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-04-07 -->

# Update mailboxProtectionUnit

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Update the properties of a [mailboxProtectionUnit](https://learn.microsoft.com/en-us/graph/api/resources/mailboxprotectionunit?view=graph-rest-beta) object.

Note

This API is currently available only through the Microsoft Graph PowerShell SDK.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | BackupRestore-Configuration.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
PATCH /backupRestore/mailboxProtectionUnits/{mailboxProtectionUnitId}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

This API supports updates only to the **billingPolicyId** property, and only for protection units removed from backup policies \(**policyId** is an empty string `""` or `null`\).

In the request body, provide a JSON representation of the following property.

| Property | Type | Description |
| :--- | :--- | :--- |
| billingPolicyId | String | Optional. The unique identifier of the billing policy assigned to the protection unit. You can update this property only when **policyId** is `null` or an empty string \(`""`\). |

> **Note:** If **policyId** has a value, the protection unit is attached to a protection policy and **billingPolicyId** can't be updated.

## Response

If successful, this method returns a `200 OK` response code and an updated [mailboxProtectionUnit](https://learn.microsoft.com/en-us/graph/api/resources/mailboxprotectionunit?view=graph-rest-beta) object in the response body.

For a list of possible error responses, see [Backup Storage API error responses](https://learn.microsoft.com/en-us/graph/backup-storage-error-codes).

## Examples

### Example 1: Update the billing policy when the protection unit isn't attached to a protection policy

The following example shows how to update the **billingPolicyId** property when the protection unit isn't attached to a protection policy.

#### Request

The following example shows a request.

```msgraph
PATCH https://graph.microsoft.com/beta/backupRestore/mailboxProtectionUnits/MjUyZTc3ZDEtM2IyYS00ZGMwLTkzYTMtMjkxZDI3NWZlY2YzXzM=
Content-Type: application/json

{
  "billingPolicyId": "fa3d95b5-2878-4de7-94f5-157f4b7607aa"
}
```

#### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.mailboxProtectionUnit",
  "id": "MjUyZTc3ZDEtM2IyYS00ZGMwLTkzYTMtMjkxZDI3NWZlY2YzXzM=",
  "directoryObjectId": "bb1b5307-d650-49cf-88cf-05eaf1b3bb33",
  "displayName": "Exo admin",
  "email": "exoadmin@contoso.com",
  "mailboxType": "user",
  "policyId": "",
  "billingPolicyId": "fa3d95b5-2878-4de7-94f5-157f4b7607aa",
  "createdDateTime": "2026-02-04T06:24:19.5736657Z",
  "createdBy": {
    "user": {
      "identity": "6294dedc-d456-4c78-9b2f-b4bae765fb09"
    }
  },
  "status": "unprotected",
  "protectionSources": "none",
  "lastModifiedDateTime": "2026-02-24T06:44:53.6014453Z",
  "lastModifiedBy": {
    "user": {
      "identity": "6294dedc-d456-4c78-9b2f-b4bae765fb09"
    }
  },
  "offboardRequestedDateTime": "0001-01-01T00:00:00Z"
}
```

### Example 2: Update the billing policy when the protection unit is attached to a protection policy

The following example shows the response you get if you try to update the **billingPolicyId** property when the protection unit is attached to a protection policy.

#### Request

The following example shows a request.

```http
PATCH https://graph.microsoft.com/beta/backupRestore/mailboxProtectionUnits/NmFmNTQ2NTUtNTkwYS00YWU2LThkMDQtODRmNDI0OGMwZjU0XzE=
Content-Type: application/json

{
  "billingPolicyId": "f65f082d-a073-4451-9a3b-2355956f2cd7"
}
```

#### Response

The following example shows the response.

```http
HTTP/1.1 403 Operation Not Allowed
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.publicError",
  "code": "OperationNotAllowed",
  "message": "Only protection units removed from backup policies are allowed for this API.",
  "target": "billingPolicyId",
  "details": [],
  "innerError": {
    "@odata.type": "#microsoft.graph.publicError",
    "code": "OperationNotAllowed",
    "message": "The protection unit is attached to a backup policy.",
    "target": "policyId",
    "details": [],
    "innerError": null
  }
}
```

## Related content

- [mailboxProtectionUnit](https://learn.microsoft.com/en-us/graph/api/resources/mailboxprotectionunit?view=graph-rest-beta)
