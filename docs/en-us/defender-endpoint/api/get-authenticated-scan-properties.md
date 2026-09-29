<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/api/get-authenticated-scan-properties -->
<!-- Sitemap-Last-Modified: 2025-12-18 -->

# Authenticated scan properties

Learn more about [Network authenticated scans](https://learn.microsoft.com/en-us/defender-endpoint/network-devices).

Important

Some information in this article relates to a prereleased product which may be substantially modified before it's commercially released. Microsoft makes no warranties, expressed or implied, with respect to the information provided here.

## Properties

| Property | Data type | Description |
| --- | --- | --- |
| id | String | Scan ID. |
| scanType | Enum | The type of scan. Possible value is: `Network`. |
| scanName | String | Name of the scan. |
| isActive | Boolean | Status of whether the scan actively running. |
| orgId | String | Related organization ID. |
| intervalInHours | Int | The interval at which the scan runs. |
| createdBy | String | Unique identity of the user that created the scan. |
| targetType | String | The target type in the target field. Possible types are `IP Address` or `Hostname`. Default value is IP Address. |
| target | String | A comma separated list of targets to scan, either IP addresses or hostnames. |
| scanAuthenticationParams | Object | An object representing the authentication parameters, see [Authentication parameters object properties](#authentication-parameters-object-properties) for expected fields. This property is mandatory when creating a new scan and is optional when updating a scan. |
| scannerAgent | Object | An object representing the scanner agent, contains the machine Id of the scanning device. |

### Authentication parameters object properties

| Property | Data type | Description |
| --- | --- | --- |
| @odata.type | Enum | The scan type authentication parameters. Possible value is: `#microsoft.windowsDefenderATP.api.SnmpAuthParams` for the `Network` scan type. |
| type | Enum | The authentication method. Possible values vary based on @odata.type property.  <br>- If @odata.type is `SnmpAuthParams`, possible values are `CommunityString`, `NoAuthNoPriv`, `AuthNoPriv`, `AuthPriv`. |
| KeyVaultUrl | String \(Optional\) | An optional property that specifies from which KeyVault the scanner should retrieve credentials. If KeyVault is specified there's no need to specify username, password. |
| KeyVaultSecretName | String \(Optional\) | An optional property that specifies KeyVault secret name from which the scanner should retrieve credentials. If KeyVault is specified there's no need to specify username, password. |
| Username | String \(Optional\) | Username when choosing `SnmpAuthParams` with any type other than `CommunityString`. |
| CommunityString | String \(Optional\) | Community string to use when choosing `SnmpAuthParams` with `CommunityString` |
| AuthProtocol | String \(Optional\) | Auth protocol to use with `SnmpAuthParams` and `AuthNoPriv` or `AuthPriv`. Possible values are `MD5`, `SHA1`. |
| AuthPassword | String \(Optional\) | Auth password to use with `SnmpAuthParams` and `AuthNoPriv` or `AuthPriv`. |
| PrivProtocol | String \(Optional\) | Priv protocol to use with `SnmpAuthParams` and `AuthPriv`. Possible values are `DES`, `3DES`, `AES`. |
| PrivPassword | String \(Optional\) | Priv password to use with `SnmpAuthParams` and `AuthPriv`. |
