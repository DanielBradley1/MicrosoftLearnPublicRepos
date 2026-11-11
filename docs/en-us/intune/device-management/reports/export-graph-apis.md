<!-- Source: https://learn.microsoft.com/en-us/intune/device-management/reports/export-graph-apis -->
<!-- Sitemap-Last-Modified: 2026-11-09 -->

# Export Intune Reports Using Graph APIs

You can export all reports that are migrated to the Intune reporting infrastructure from a single top-level export API. Use the Microsoft Graph API to make the HTTP call. Microsoft Graph is a RESTful web API that you can use to access Microsoft Cloud service resources.

Note

For information about making REST API calls, including tools for interacting with Microsoft Graph, see [Use the Microsoft Graph API](https://learn.microsoft.com/en-us/graph/use-the-api).

Microsoft Intune exports reports by using the following Microsoft Graph API endpoint:

```http
https://graph.microsoft.com/beta/deviceManagement/reports/exportJobs
https://graph.microsoft.com/v1.0/deviceManagement/reports/exportJobs
```

## Example devices report request and response

When you make the request, include a `reportName` parameter in the request body that corresponds to the report you want to export. The following example shows an export request for the **Devices** report. Use the POST HTTP method in your request. The POST method creates a new resource or performs an action.

### Request example

The following request contains the HTTP method used in the request to Microsoft Graph.

```http
{
    "reportName": "Devices",
    "filter":"(OwnerType eq '1')",
    "localizationType": "LocalizedValuesAsAdditionalColumn",
    "format": "json",
    "select": [
        "DeviceName",
        "managementAgent",
        "ownerType",
        "complianceState",
        "OS",
        "OSVersion",
        "LastContact",
        "UPN",
        "DeviceId"
    ]
}
```

Note

To retrieve data, select specific columns, such as those specified in the preceding example. Don't build automation around default columns of any report export. Build your automation to explicitly select relevant columns.

### Response example

Based on the preceding POST request, Graph returns a response message. The response message contains the data you requested or the result of the operation.

```http
{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#deviceManagement/reports/exportJobs/$entity",
    "id": "Devices_05e62361-783b-4cec-b635-0aed0ecf14a3",
    "reportName": "Devices",
    "filter":"(OwnerType eq '1')",
    "localizationType": "LocalizedValuesAsAdditionalColumn",
    "select": [
        "DeviceName",
        "managementAgent",
        "ownerType",
        "complianceState",
        "OS",
        "OSVersion",
        "LastContact",
        "UPN",
        "DeviceId"
    ],
    "format": "csv",
    "snapshotId": null,
    "status": "notStarted",
    "url": null,
    "requestDateTime": "2020-08-19T03:43:32.1405758Z",
    "expirationDateTime": "0001-01-01T00:00:00Z"
}
```

You can use the `id` field to query the status of the export with a GET request.

For example: `https://graph.microsoft.com/beta/deviceManagement/reports/exportJobs('Devices_05e62361-783b-4cec-b635-0aed0ecf14a3')` or `https://graph.microsoft.com/beta/deviceManagement/reports/exportJobs/Devices_05e62361-783b-4cec-b635-0aed0ecf14a3`

You need to continue calling this URL until you get a response with a `status: completed` attribute. It looks like the following example:

```http
{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#deviceManagement/reports/exportJobs/$entity",
    "id": "Devices_05e62361-783b-4cec-b635-0aed0ecf14a3",
    "reportName": "Devices",
    "filter":"(OwnerType eq '1')",
    "localizationType": "LocalizedValuesAsAdditionalColumn",
    "select": [
        "DeviceName",
        "managementAgent",
        "ownerType",
        "complianceState",
        "OS",
        "OSVersion",
        "LastContact",
        "UPN",
        "DeviceId"
    ],
    "format": "csv",
    "snapshotId": null,
    "status": "completed",
    "url": "https://amsua0702repexpstorage.blob.core.windows.net/cec055a4-97f0-4889-b790-dc7ad0d12c29/Devices_05e62361-783b-4cec-b635-0aed0ecf14a3.zip?sv=2019-02-02&sr=b&sig=%2BP%2B4gGiZf0YzlQRuAV5Ji9Beorg4nnOtP%2F7bbFGH7GY%3D&skoid=1db6df02-4c8b-4cb3-8394-7ac2390642f8&sktid=72f988bf-86f1-41af-91ab-2d7cd011db47&skt=2020-08-19T03%3A48%3A32Z&ske=2020-08-19T09%3A44%3A23Z&sks=b&skv=2019-02-02&se=2020-08-19T09%3A44%3A23Z&sp=r",
    "requestDateTime": "2020-08-19T03:43:32.1405758Z",
    "expirationDateTime": "2020-08-19T09:44:23.8540289Z"
}
```

You can then directly download the compressed CSV from the `url` field.

## Report parameters

There are five main parameters you can submit in your request body to define the export request:

- `reportName`: Required. This parameter is the name of the report you want to specify.
- `filter`: Not required for most reports. The filter parameter is a string.
- `select`: Not required. Specify which columns from the report you want. Only valid column names relevant to the report you're calling are accepted.
- `format`: Not required. By default, the data is output in `csv` format. Specify `json` to output the file in JSON format.
- `localizationType`: This parameter controls localization behavior for the report. Possible values are `LocalizedValuesAsAdditionalColumn` and `ReplaceLocalizableValues`.

## Localization behavior

The `localizationType` parameter controls localization behavior for the report. The possible values for this parameter are `LocalizedValuesAsAdditionalColumn` and `ReplaceLocalizableValues`.

### LocalizedValuesAsAdditionalColumn report value

This value for the `localizationType` parameter is the default value. It's inserted automatically if the `localizationType` parameter isn't specified. This value specifies that Intune provides two columns for each localizable column.

- *enum value*: The *enum value* column contains either a raw string, or a set of numbers that don't change, regardless of locale. This column is under the original column name, as in the example.
- *localized string value*: This column is the original column name with `_loc` appended. It contains string values that are human readable, and locale conditional, as in the example.

#### Example

| OS | OS\_loc |
| :--- | :--- |
| 1 | Windows |
| 1 | Windows |
| 1 | Windows |
| 2 | iOS |
| 3 | Android |
| 4 | Mac |

### ReplaceLocalizableValues report value

ReplaceLocalizableValues report value will only return one column per localized attribute. This column contains the original column name with the localized values.

#### Example

| OS |
| :--- |
| Windows |
| Windows |
| Windows |
| iOS |
| Android |
| Mac |

For columns without localized values, only a single column with the true column name and the true column values are returned.

Important

The `localizationType` parameter is relevant for any export experience hosted by Intune's reporting infrastructure with a few exceptions. The`Devices` and `DevicesWithInventory` report types won't honor the `localizationType` parameter due to legacy compatibility requirements.

## API throttling conditions

To ensure that the `exportJobs` API doesn't have too many concurrent requests, which would impact the API's response rate, the following throttling limits are applied.

- **The APIs will support up to 100 requests per tenant per minute**: This support covers all users and apps in a tenant. Any additional requests initiated by either users or apps in the tenant within the same minute are throttled.

  - If the APIs are initiated by a user, up to 8 requests are allowed by the same user within a minute. Subsequent requests by the same user within the same minute are throttled.
  - If the APIs are initiated by an app, then up to 48 requests are allowed by the same app within a minute. Subsequent requests by the same app within the same minute are throttled.

## Related content

- [Microsoft Graph documentation](https://learn.microsoft.com/en-us/graph/)
- [Intune reports](https://learn.microsoft.com/en-us/intune/device-management/reports/overview)
