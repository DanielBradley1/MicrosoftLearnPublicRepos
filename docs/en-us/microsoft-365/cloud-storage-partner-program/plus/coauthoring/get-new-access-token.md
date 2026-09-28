<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/coauthoring/get-new-access-token -->
<!-- Sitemap-Last-Modified: 2022-07-06 -->

# GetNewAccessToken overview

You *must* set the new `EndPoints` property in response to the existing [GetNewAccessToken](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/bootstrapper/getnewaccesstoken) request. The contents of this property should be a nested JSON-formatted object. The object should have the following properties, with values that exactly match what would be returned in response to a [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-csppp) request:

- `RealTimeChannelEndpointUrl`
- `OfficeCollaborationServiceEndpointUrl`

## Sample response

The following sample response includes the new JSON properties:

```json
{
  "Bootstrap": {
    "EcosystemUrl": "http://.../wopi*/ecosystem?access_token=",
    "UserId": "User ID",
    "SignInName": "user@contoso.com",
    "UserFriendlyName": "User Name"
  },
  "AccessTokenInfo": {
    "AccessToken": "1234567890abcdef",
    "AccessTokenExpiry": 1234567890
  },
  "EndPoints": {
    "RealTimeChannelEndpointUrl": "http://rtc",
    "OfficeCollaborationServiceEndpointUrl": "http://ocs"
  }
}
```

## Next steps

- Learn what's new in the [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-csppp) coauthoring extensions.
- Learn what's new in the [WOPI locks](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/coauthoring/wopi-locks) coauthoring extensions.
