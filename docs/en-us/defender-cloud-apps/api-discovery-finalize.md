<!-- Source: https://learn.microsoft.com/en-us/defender-cloud-apps/api-discovery-finalize -->
<!-- Sitemap-Last-Modified: 2024-10-23 -->

# Finalize file upload - cloud discovery API

After the file content upload successfully completes, notify us in order to begin the processing of the file.

## HTTP request

```rest
POST /api/v1/discovery/done_upload/
```

## Request BODY parameters

| Parameter | Description |
| --- | --- |
| uploadUrl | The URL that was returned in the initial call requesting file upload. |
| inputStreamName | The name of the data source from which data is coming in \(to see the list of names, in the portal, go to **Settings** > **Automatic log upload**\). |
| uploadAsSnapshot | Upload the data as a snapshot report instead of uploading to a continuous report. If this parameter is set, then the report will be created with the name specified in inputStreamName. |

## Example

### Request

Here is an example of the request.

```rest
curl -XPOST -H "Authorization:Token <your_token_key>" -H "Content-Type: application/json" "https://<tenant_id>.<tenant_region>.portal.cloudappsecurity.com/api/v1/discovery/done_upload/" -d {\"uploadUrl\":\"<initiate_file_upload_response_url>\",\"inputStreamName\":\"<inputStreamName>\"}
```

If you run into any problems, we're here to help. To get assistance or support for your product issue, please [open a support ticket](https://learn.microsoft.com/en-us/defender-xdr/contact-defender-support).
