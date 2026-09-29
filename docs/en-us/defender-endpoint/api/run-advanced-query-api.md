<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/api/run-advanced-query-api -->
<!-- Sitemap-Last-Modified: 2026-07-28 -->

# Advanced hunting API

Warning

The Microsoft Defender for Endpoint advanced hunting API is old and has limited capabilities. A more comprehensive version of the advanced hunting API that can query more tables is already available in the **[Microsoft Graph security API](https://learn.microsoft.com/en-us/graph/api/resources/security-api-overview)**. For more information, see **[Advanced hunting using Microsoft Graph security API](https://learn.microsoft.com/en-us/graph/api/resources/security-api-overview#advanced-hunting)**.

The Microsoft Defender for Endpoint advanced hunting API is transitioning to the Microsoft Graph security API, which includes advanced hunting capabilities. The Microsoft Graph security API provides broader data coverage, improved consistency, and better scalability for automation and security workflows. Retirement began in January 2026. After retirement completes, the Microsoft Defender for Endpoint advanced hunting API no longer functions. For the retirement timeline, see [MC1220762](https://admin.microsoft.com/Adminportal/Home#/MessageCenter/:/messages/MC1220762). For more information to help with your migration, see **[Use the Microsoft Graph security API](https://learn.microsoft.com/en-us/graph/api/resources/security-api-overview)**.

Note

If you're a US Government customer, use the URIs listed in [Microsoft Defender for Endpoint for US Government customers](https://learn.microsoft.com/en-us/defender-endpoint/gov#api).

Tip

For better performance, instead of using api.security.microsoft.com, use a server closer to your geolocation:

- us.api.security.microsoft.com
- eu.api.security.microsoft.com
- uk.api.security.microsoft.com
- au.api.security.microsoft.com
- swa.api.security.microsoft.com
- ina.api.security.microsoft.com
- aea.api.security.microsoft.com

## Limitations

- You can only run a query on data from the last 30 days.
- The results include a maximum of 100,000 rows.
- The number of executions is limited per tenant:

  - API calls: Up to 45 calls per minute, and up to 1,500 calls per hour.
  - Execution time: 10 minutes of running time every hour and 3 hours of running time a day.

- The maximal execution time of a single request is 200 seconds.
- `429` response represents reaching quota limit either by number of requests or by CPU. Read response body to understand what limit was reached.
- The maximum query result size of a single request can't exceed 50 MB. If exceeded, an HTTP 400 Bad Request with the message "Query execution has exceeded the allowed result size. Optimize your query by limiting the number of results and try again" occurs.

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Use Microsoft Defender for Endpoint APIs](https://learn.microsoft.com/en-us/defender-endpoint/api/apis-intro)

| Permission type | Permission | Permission display name |
| --- | --- | --- |
| Application | AdvancedQuery.Read.All | `Run advanced queries` |
| Delegated \(work or school account\) | AdvancedQuery.Read | `Run advanced queries` |

Note

When obtaining a token using user credentials:

- The user needs to have the `View Data` role assigned in Microsoft Entra ID.
- The user needs to have access to the device, based on device group settings \(See [Create and manage device groups](https://learn.microsoft.com/en-us/defender-endpoint/machine-groups) for more information\).

  Device group creation is supported in Defender for Endpoint Plan 1 and Plan 2.

## HTTP request

```http
POST https://api.security.microsoft.com/api/advancedqueries/run
```

## Request headers

| Header | Value |
| --- | --- |
| Authorization | Bearer {token}. **Required**. |
| Content-Type | application/json |

## Request body

In the request body, supply a JSON object with the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| Query | Text | The query to run. **Required**. |

## Response

If successful, this method returns 200 OK, and *QueryResponse* object in the response body.

## Example

### Request example

Here's an example of the request.

```http
POST https://api.security.microsoft.com/api/advancedqueries/run
```

```json
{"Query":"DeviceProcessEvents |where InitiatingProcessFileName =~ 'powershell.exe' |where ProcessCommandLine contains 'appdata'|project Timestamp, FileName, InitiatingProcessFileName, DeviceId|limit 2"}
```

### Response example

Here's an example of the response.

Note

The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```json
{
    "Schema": [
        {
            "Name": "Timestamp",
            "Type": "DateTime"
        },
        {
            "Name": "FileName",
            "Type": "String"
        },
        {
            "Name": "InitiatingProcessFileName",
            "Type": "String"
        },
        {
            "Name": "DeviceId",
            "Type": "String"
        }
    ],
    "Results": [
        {
            "Timestamp": "2020-02-05T01:10:26.2648757Z",
            "FileName": "csc.exe",
            "InitiatingProcessFileName": "powershell.exe",
            "DeviceId": "10cbf9182d4e95660362f65cfa67c7731f62fdb3"
        },
        {
            "Timestamp": "2020-02-05T01:10:26.5614772Z",
            "FileName": "csc.exe",
            "InitiatingProcessFileName": "powershell.exe",
            "DeviceId": "10cbf9182d4e95660362f65cfa67c7731f62fdb3"
        }
    ]
}
```

## Related articles

- [Use the Microsoft Graph security API - Microsoft Graph \| Microsoft Learn](https://learn.microsoft.com/en-us/graph/api/resources/security-api-overview)
- [Microsoft Defender for Endpoint APIs introduction](https://learn.microsoft.com/en-us/defender-endpoint/api/apis-intro)
- [Advanced Hunting from Portal](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-query-language)
- [Advanced Hunting using PowerShell](https://learn.microsoft.com/en-us/defender-endpoint/api/run-advanced-query-sample-powershell)

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender for Endpoint Tech Community](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/bd-p/MicrosoftDefenderATP).
