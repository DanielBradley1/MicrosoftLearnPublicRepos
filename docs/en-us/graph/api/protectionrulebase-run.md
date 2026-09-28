<!-- Source: https://learn.microsoft.com/en-us/graph/api/protectionrulebase-run?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-22 -->

# protectionRuleBase: run

Namespace: microsoft.graph

Activate a [protection rule](https://learn.microsoft.com/en-us/graph/api/resources/protectionrulebase?view=graph-rest-1.0).

Upon activating the protection rule, the status transitions to `active`.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | BackupRestore-Configuration.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | BackupRestore-Configuration.ReadWrite.All | Not available. |

## HTTP request

```http
POST /solutions/backupRestore/sharePointProtectionPolicies/{sharePointProtectionPolicyId}/siteInclusionRules/{siteProtectionRuleId}/run
POST /solutions/backupRestore/oneDriveForBusinessProtectionPolicies/{oneDriveForBusinessProtectionPolicyId}/driveInclusionRules/{driveProtectionRuleId}/run
POST /solutions/backupRestore/exchangeProtectionPolicies/{exchangeProtectionPolicyId}/mailboxInclusionRules/{mailboxProtectionRuleId}/run
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this action returns a `200 OK` response code and a [protectionRuleBase](https://learn.microsoft.com/en-us/graph/api/resources/protectionrulebase?view=graph-rest-1.0) object in the response body.

## Examples

### Example 1: Activate a siteInclusionRule associated with a SharePoint protection policy

The following example shows how to activate a **siteInclusionRule** associated with a [sharePointProtectionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/sharepointprotectionpolicy?view=graph-rest-1.0) object.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
POST https://graph.microsoft.com/v1.0/solutions/backupRestore/sharePointProtectionPolicies/71633878-8321-4950-bfaf-ed285bdd1461/siteInclusionRules/61633878-8321-4950-bfaf-ed285bdd1461/run
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

await client.api('/solutions/backupRestore/sharePointProtectionPolicies/71633878-8321-4950-bfaf-ed285bdd1461/siteInclusionRules/61633878-8321-4950-bfaf-ed285bdd1461/run')
	.post();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 202 Accepted
Content-Type: application/json
Content-Location: https://graph.microsoft.com/v1.0/solutions/backupRestore/sharePointProtectionPolicies/71633878-8321-4950-bfaf-ed285bdd1461/siteInclusionRules('61633878-8321-4950-bfaf-ed285bdd1461')

{
   "@odata.type": "#microsoft.graph.protectionRuleBase",
   "id":"61633878-8321-4950-bfaf-ed285bdd1461",
   "status" : "active",
   "createdBy":{
      "application":{
         "id":"1fec8e78-bce4-4aaf-ab1b-5451cc387264"
      },
      "user":{
         "id":"845457dc-4bb2-4815-bef3-8628ebd1952e"
      }
   },
   "createdDateTime":"2015-06-19T12:01:03.45Z",
   "lastModifiedBy":{
      "application":{
         "id":"1fec8e78-bce4-4aaf-ab1b-5451cc387264"
      },
      "user":{
         "id":"845457dc-4bb2-4815-bef3-8628ebd1952e"
      }
   },
   "lastModifiedDateTime":"2015-06-19T12:01:03.45Z",
   "isAutoApplyEnabled": false
}
```

### Example 2: Activate a driveInclusionRule associated with an OneDriveForBusiness protection policy

The following example shows how to activate a **driveInclusionRule**associated with an [oneDriveForBusinessProtectionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/onedriveforbusinessprotectionpolicy?view=graph-rest-1.0) object.

### Request

The following example shows a request.

- [HTTP](#tabpanel_2_http)
- [JavaScript](#tabpanel_2_javascript)

```http
POST https://graph.microsoft.com/v1.0/solutions/backupRestore/oneDriveForBusinessProtectionPolicies/71633878-8321-4950-bfaf-ed285bdd1461/driveInclusionRules/61633878-8321-4950-bfaf-ed285bdd1461/run
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

await client.api('/solutions/backupRestore/oneDriveForBusinessProtectionPolicies/71633878-8321-4950-bfaf-ed285bdd1461/driveInclusionRules/61633878-8321-4950-bfaf-ed285bdd1461/run')
	.post();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 202 Accepted
Content-Type: application/json
Content-Location: https://graph.microsoft.com/v1.0/solutions/backupRestore/oneDriveForBusinessProtectionPolicies/71633878-8321-4950-bfaf-ed285bdd1461/driveInclusionRules('61633878-8321-4950-bfaf-ed285bdd1461')

{
   "@odata.type": "#microsoft.graph.protectionRuleBase",
   "id":"61633878-8321-4950-bfaf-ed285bdd1461",
   "status" : "active",
   "createdBy":{
      "application":{
         "id":"1fec8e78-bce4-4aaf-ab1b-5451cc387264"
      },
      "user":{
         "id":"845457dc-4bb2-4815-bef3-8628ebd1952e"
      }
   },
   "createdDateTime":"2015-06-19T12:01:03.45Z",
   "lastModifiedBy":{
      "application":{
         "id":"1fec8e78-bce4-4aaf-ab1b-5451cc387264"
      },
      "user":{
         "id":"845457dc-4bb2-4815-bef3-8628ebd1952e"
      }
   },
   "lastModifiedDateTime":"2015-06-19T12:01:03.45Z",
   "isAutoApplyEnabled": false
}
```

### Example 3: Activate a mailboxInclusionRule associated with an Exchange protection policy

The following example shows how to activate a **mailboxInclusionRule** associated with an [exchangeProtectionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/exchangeprotectionpolicy?view=graph-rest-1.0) object.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_3_http)
- [JavaScript](#tabpanel_3_javascript)

```http
POST https://graph.microsoft.com/v1.0/solutions/backupRestore/exchangeProtectionPolicies/{exchangeProtectionPolicyId}/mailboxInclusionRules/{mailboxProtectionRuleId}/run
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

await client.api('/solutions/backupRestore/exchangeProtectionPolicies/{exchangeProtectionPolicyId}/mailboxInclusionRules/{mailboxProtectionRuleId}/run')
	.post();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 202 Accepted
Content-Type: application/json
Content-Location: https://graph.microsoft.com/v1.0/solutions/backupRestore/exchangeProtectionPolicies/{exchangeProtectionPolicyId}/mailboxInclusionRules/{mailboxProtectionRuleId}

{
   "@odata.type": "#microsoft.graph.protectionRuleBase",
   "id":"41633878-8321-4950-bfaf-ed285bdd1461",
   "status" : "active",
   "createdBy":{
      "application":{
         "id":"1fec8e78-bce4-4aaf-ab1b-5451cc387264"
      },
      "user":{
         "id":"845457dc-4bb2-4815-bef3-8628ebd1952e"
      }
   },
   "createdDateTime":"2015-06-19T12:01:03.45Z",
   "lastModifiedBy":{
      "application":{
         "id":"1fec8e78-bce4-4aaf-ab1b-5451cc387264"
      },
      "user":{
         "id":"845457dc-4bb2-4815-bef3-8628ebd1952e"
      }
   },
   "lastModifiedDateTime":"2015-06-19T12:01:03.45Z",
   "isAutoApplyEnabled": false
}
```
