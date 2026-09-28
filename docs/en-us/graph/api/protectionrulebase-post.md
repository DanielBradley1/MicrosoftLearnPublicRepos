<!-- Source: https://learn.microsoft.com/en-us/graph/api/protectionrulebase-post?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-10-08 -->

# Create protectionRuleBase

Namespace: microsoft.graph

Create a new [protection rule](https://learn.microsoft.com/en-us/graph/api/resources/protectionrulebase?view=graph-rest-1.0) associated with a [protection policy](https://learn.microsoft.com/en-us/graph/api/resources/protectionpolicybase?view=graph-rest-1.0). You can use this method to create a [mailboxProtectionRule](https://learn.microsoft.com/en-us/graph/api/resources/mailboxprotectionrule?view=graph-rest-1.0), [driveProtectionRule](https://learn.microsoft.com/en-us/graph/api/resources/driveprotectionrule?view=graph-rest-1.0), or [siteProtectionRule](https://learn.microsoft.com/en-us/graph/api/resources/siteprotectionrule?view=graph-rest-1.0).

An inclusion rule indicates that a protection policy should contain protection units that match the specified rule criteria. The initial status of a protection rule upon creation is `active`. After the rule is applied, the state is either `completed` or `completedWithErrors`.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | BackupRestore-Configuration.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | BackupRestore-Configuration.ReadWrite.All | Not available. |

## HTTP request

```http
POST /solutions/backupRestore/sharePointProtectionPolicies/{sharePointProtectionPolicyId}/siteInclusionRules
POST /solutions/backupRestore/oneDriveForBusinessProtectionPolicies/{oneDriveForBusinessProtectionPolicyId}/driveInclusionRules
POST /solutions/backupRestore/exchangeProtectionPolicies/{exchangeProtectionPolicyId}/mailboxInclusionRules
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

In the request body, supply a JSON representation of the [protectionRuleBase](https://learn.microsoft.com/en-us/graph/api/resources/protectionrulebase?view=graph-rest-1.0) object.

### Properties to create a new siteInclusionRule

You can specify the following properties when you create a **siteInclusionRule**.

| Property | Type | Description |
| :--- | :--- | :--- |
| siteExpression | String | Contains the [site expression](https://learn.microsoft.com/en-us/graph/api/resources/siteprotectionrule?view=graph-rest-1.0#siteexpression-examples). Required. |

### Properties to create a new driveInclusionRule

You can specify the following properties when you create a **driveInclusionRule**.

| Property | Type | Description |
| :--- | :--- | :--- |
| driveExpression | String | Contains the [drive expression](https://learn.microsoft.com/en-us/graph/api/resources/driveprotectionrule?view=graph-rest-1.0#driveexpression-examples). Required. |

### Properties to create a new mailboxInclusionRule

You can specify the following properties when you create a **mailboxInclusionRule**.

| Property | Type | Description |
| :--- | :--- | :--- |
| mailboxExpression | String | Contains the [mailbox expression](https://learn.microsoft.com/en-us/graph/api/resources/mailboxprotectionrule?view=graph-rest-1.0#mailboxexpression-examples). Supports `memberOf` and `group.id` properties. Required |

## Response

If successful, this method returns a `201 Created` response code and a [protectionRuleBase](https://learn.microsoft.com/en-us/graph/api/resources/protectionrulebase?view=graph-rest-1.0) object in the response body.

For a list of possible error responses, see [Backup Storage API error responses](https://learn.microsoft.com/en-us/graph/backup-storage-error-codes).

## Examples

### Example 1: Create a new siteInclusionRule associated with a SharePoint protection policy

The following example shows how to create a new **siteInclusionRule** associated with a [sharePointProtectionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/sharepointprotectionpolicy?view=graph-rest-1.0).

#### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
POST https://graph.microsoft.com/v1.0/solutions/backupRestore/sharePointProtectionPolicies/71633878-8321-4950-bfaf-ed285bdd1461/siteInclusionRules 
Content-Type: application/json

{
    "siteExpression": "((displayName -contains 'Finance')  -or  (displayName -contains 'Legal'))"
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const siteProtectionRule = {
    siteExpression: '((displayName -contains \'Finance\')  -or  (displayName -contains \'Legal\'))'
};

await client.api('/solutions/backupRestore/sharePointProtectionPolicies/71633878-8321-4950-bfaf-ed285bdd1461/siteInclusionRules')
	.post(siteProtectionRule);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 201 Created
Content-Location: https://graph.microsoft.com/v1.0/solutions/backupRestore/sharePointProtectionPolicies/71633878-8321-4950-bfaf-ed285bdd1461/siteInclusionRules('61633878-8321-4950-bfaf-ed285bdd1461')

{
   "@odata.type": "#microsoft.graph.siteProtectionRule",
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
   "isAutoApplyEnabled": false,
   "siteExpression": "((displayName -contains 'Finance')  -or  (displayName -contains 'Legal'))"
}
```

### Example 2: Create a new driveInclusionRule associated with a OneDriveForBusiness protection policy

The following example shows how to create a new **driveInclusionRule** associated with a [oneDriveForBusinessProtectionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/onedriveforbusinessprotectionpolicy?view=graph-rest-1.0).

#### Request

The following example shows a request.

- [HTTP](#tabpanel_2_http)
- [JavaScript](#tabpanel_2_javascript)

```http
POST https://graph.microsoft.com/v1.0/solutions/backupRestore/oneDriveForBusinessProtectionPolicies/71633878-8321-4950-bfaf-ed285bdd1461/driveInclusionRules 
Content-Type: application/json

{
    "driveExpression": "(memberOf -any (group.id -in ['c318eb4a-ea72-42bd-8f0b-d0bbf794bec7']))"
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const driveProtectionRule = {
    driveExpression: '(memberOf -any (group.id -in [\'c318eb4a-ea72-42bd-8f0b-d0bbf794bec7\']))'
};

await client.api('/solutions/backupRestore/oneDriveForBusinessProtectionPolicies/71633878-8321-4950-bfaf-ed285bdd1461/driveInclusionRules')
	.post(driveProtectionRule);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 201 Created
Content-Location: https://graph.microsoft.com/v1.0/solutions/backupRestore/oneDriveForBusinessProtectionPolicies/71633878-8321-4950-bfaf-ed285bdd1461/driveInclusionRules('61633878-8321-4950-bfaf-ed285bdd1461')

{
   "@odata.type": "#microsoft.graph.driveProtectionRule",
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
   "isAutoApplyEnabled": false,
   "driveExpression": "(memberOf -any (group.id -in ['c318eb4a-ea72-42bd-8f0b-d0bbf794bec7']))"
}
```

### Example 3: Create a new mailboxInclusionRule associated with an Exchange protection policy

The following example shows how to create a new **mailboxInclusionRule** associated with an [exchangeProtectionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/exchangeprotectionpolicy?view=graph-rest-1.0).

#### Request

The following example shows a request.

- [HTTP](#tabpanel_3_http)
- [JavaScript](#tabpanel_3_javascript)

```http
POST https://graph.microsoft.com/v1.0/solutions/backupRestore/exchangeProtectionPolicies/71633878-8321-4950-bfaf-ed285bdd1461/mailboxInclusionRules

{
   "mailboxExpression": "(memberOf -any (group.id -in ['f218eb4a-ea72-42bd-8f0b-d0bbf794bec7']))"
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const mailboxProtectionRule = {
   mailboxExpression: '(memberOf -any (group.id -in [\'f218eb4a-ea72-42bd-8f0b-d0bbf794bec7\']))'
};

await client.api('/solutions/backupRestore/exchangeProtectionPolicies/71633878-8321-4950-bfaf-ed285bdd1461/mailboxInclusionRules')
	.post(mailboxProtectionRule);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-Location: https://graph.microsoft.com/v1.0/solutions/backupRestore/exchangeProtectionPolicies/71633878-8321-4950-bfaf-ed285bdd1461/mailboxInclusionRules('61633878-8321-4950-bfaf-ed285bdd1461')

{
   "@odata.type": "#microsoft.graph.mailboxProtectionRule",
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
   "isAutoApplyEnabled": false,
   "mailboxExpression": "(memberOf -any (group.id -in ['f218eb4a-ea72-42bd-8f0b-d0bbf794bec7']))"
}
```
