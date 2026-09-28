<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-security-getrunhuntingquery?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-08 -->

# security: getRunHuntingQuery

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Query a specified set of event, activity, or entity data supported by Microsoft Defender XDR to proactively look for specific threats in your environment, by using a GET request.

This function is the GET-based companion to the [runHuntingQuery](https://learn.microsoft.com/en-us/graph/api/security-security-runhuntingquery?view=graph-rest-beta) action. It accepts a query in [Kusto Query Language \(KQL\)](https://learn.microsoft.com/en-us/azure/data-explorer/kusto/query/) as a URL parameter, executes it against the [advanced hunting schema](https://learn.microsoft.com/en-us/microsoft-365/security/defender/advanced-hunting-schema-tables?view=o365-worldwide&preserve-view=true), and returns the same [huntingQueryResults](https://learn.microsoft.com/en-us/graph/api/resources/security-huntingqueryresults?view=graph-rest-beta) shape as the POST action. Use this function in scenarios that can't issue authenticated POST requests, such as Power BI dashboards that authenticate through `Web.Contents`.

Find out more about [hunting for threats across devices, emails, apps, and identities](https://learn.microsoft.com/en-us/microsoft-365/security/defender/advanced-hunting-query-emails-devices?view=o365-worldwide&preserve-view=true). Learn about [KQL](https://learn.microsoft.com/en-us/azure/data-explorer/kusto/query/).

For information on using advanced hunting in the [Microsoft Defender portal](https://learn.microsoft.com/en-us/microsoft-365/security/defender/microsoft-365-defender-portal?view=o365-worldwide&preserve-view=true), see [Proactively hunt for threats with advanced hunting in Microsoft Defender XDR](https://learn.microsoft.com/en-us/microsoft-365/security/defender/advanced-hunting-overview?view=o365-worldwide&preserve-view=true).

Note

Because the query is passed in the URL, callers whose query string exceeds infrastructure URI limits receive a `414 URI Too Long` response. Use the [runHuntingQuery](https://learn.microsoft.com/en-us/graph/api/security-security-runhuntingquery?view=graph-rest-beta) POST action for long queries.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | ThreatHunting.Read.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | ThreatHunting.Read.All | Not available. |

Important

The signed-in user also needs one of the following roles:

- A [Microsoft Defender XDR Unified role-based access control \(RBAC\) role](https://learn.microsoft.com/en-us/microsoft-365/security/defender/manage-rbac) that grants advanced hunting access.
- A [Microsoft Entra ID role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) that provides only the least privilege necessary: Security Reader, Global Reader, Security Operator, or Security Administrator.

## HTTP request

```http
GET /security/getRunHuntingQuery(query='{query}',timespan='{timespan}',workspaceId={workspaceId})
```

## Function parameters

In the request URL, provide the following query parameters with values.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| query | String | Required. The hunting query in Kusto Query Language \(KQL\). For more information, see [KQL quick reference](https://learn.microsoft.com/en-us/azure/data-explorer/kql-quick-reference). The value must be percent-encoded when called directly over REST. |
| timespan | String | Optional. The interval of time over which to query data, in ISO 8601 format. The default value is 30 days. If a time filter is specified in both the query and the **timespan** parameter, the shorter time span is applied. |
| workspaceId | Guid | Optional. The GUID of a specific Log Analytics workspace to target. If omitted, the service uses the caller's primary workspace. If the workspace isn't found or not accessible, the service falls back to the caller's primary workspace. |

The following examples show the possible formats for the `timespan` parameter:

- **Date/Date**: "2026-02-01T08:00:00Z/2026-02-15T08:00:00Z" - Start and end dates.
- **Duration/endDate**: "P30D/2026-02-15T08:00:00Z" - A period before the end date.
- **Start/duration**: "2026-02-01T08:00:00Z/P30D" - Start date and duration.
- **ISO8601 duration**: "P30D" - Duration from now backwards.
- **Single date/time**: "2026-02-01T08:00:00Z" - Start time with end time defaulted to the current time.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this function returns a `200 OK` response code and a [microsoft.graph.security.huntingQueryResults](https://learn.microsoft.com/en-us/graph/api/resources/security-huntingqueryresults?view=graph-rest-beta) in the response body.

## Examples

### Example 1: Run a hunting query with GET

#### Request

The following example specifies a KQL query that:

- Looks into the [AlertInfo](https://learn.microsoft.com/en-us/microsoft-365/security/defender/advanced-hunting-alertinfo-table?view=o365-worldwide&preserve-view=true) table in the advanced hunting schema.
- Projects two columns \(`Timestamp`, `Title`\).
- Limits the output to two records.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```msgraph
GET https://graph.microsoft.com/beta/security/getRunHuntingQuery(query='AlertInfo%20%7C%20project%20Timestamp%2C%20Title%20%7C%20take%202',timespan='P1D')
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let huntingQueryResults = await client.api('/security/getRunHuntingQuery(query='AlertInfo | project Timestamp, Title | take 2',timespan='P1D')')
	.version('beta')
	.get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#microsoft.graph.security.huntingQueryResults",
    "schema": [
        {
            "name": "Timestamp",
            "type": "DateTime"
        },
        {
            "name": "Title",
            "type": "String"
        }
    ],
    "results": [
        {
            "Timestamp": "2026-03-10T08:31:15.128Z",
            "Title": "Suspicious PowerShell command line"
        },
        {
            "Timestamp": "2026-03-10T08:29:41.017Z",
            "Title": "Credential dumping attempt detected"
        }
    ]
}
```

### Example 2: Run a hunting query against a specific workspace

#### Request

The following example shows a GET request that targets a specific Log Analytics workspace by passing the optional **workspaceId** parameter.

- [HTTP](#tabpanel_2_http)
- [JavaScript](#tabpanel_2_javascript)

```msgraph
GET https://graph.microsoft.com/beta/security/getRunHuntingQuery(query='AlertInfo%20%7C%20project%20Timestamp%2C%20Title%20%7C%20take%202',timespan='P1D',workspaceId=00000000-0000-0000-0000-000000000001)
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let huntingQueryResults = await client.api('/security/getRunHuntingQuery(query='AlertInfo | project Timestamp, Title | take 2',timespan='P1D',workspaceId=00000000-0000-0000-0000-000000000001)')
	.version('beta')
	.get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#microsoft.graph.security.huntingQueryResults",
    "schema": [
        {
            "name": "Timestamp",
            "type": "DateTime"
        },
        {
            "name": "Title",
            "type": "String"
        }
    ],
    "results": [
        {
            "Timestamp": "2026-03-10T08:31:15.128Z",
            "Title": "Suspicious PowerShell command line"
        },
        {
            "Timestamp": "2026-03-10T08:29:41.017Z",
            "Title": "Credential dumping attempt detected"
        }
    ]
}
```
