<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/api/get-remediation-exposed-devices-activities -->
<!-- Sitemap-Last-Modified: 2025-11-24 -->

# List exposed devices of one remediation activity

Important

Some information in this article relates to a prereleased product which may be substantially modified before it's commercially released. Microsoft makes no warranties, expressed or implied, with respect to the information provided here.

## API Description

Returns information about exposed devices for the specified remediation task.

[Learn more about remediation activities](https://learn.microsoft.com/en-us/defender-vulnerability-management/tvm-remediation).

## List exposed devices associated with a remediation task \(id\)

**URL:** GET: /api/remediationTasks/{id}/machineReferences

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Use Microsoft Defender for Endpoint APIs for details.](https://learn.microsoft.com/en-us/defender-endpoint/api/apis-intro)

| Permission type | Permission | Permission display name |
| --- | --- | --- |
| Application | RemediationTasks.Read.All | 'Read Threat and Vulnerability Management vulnerability information' |
| Delegated \(work or school account\) | RemediationTask.Read.Read | 'Read Threat and Vulnerability Management vulnerability information' |

## Properties details

| Property \(id\) | Data type | Description | Example |
| --- | --- | --- | --- |
| id | String | Device ID | w2957837fwda8w9ae7f023dba081059dw8d94503 |
| computerDnsName | String | Device name | PC-SRV2012R2Foo.UserNameVldNet.local |
| osPlatform | String | Device operating system | WindowsServer2012R2 |
| rbacGroupName | String | Name of the device group this device is associated with | Servers |

## Example

### Request example

```http
GET https://api.security.microsoft.com/api/remediationtasks/aaaabbbb-0000-cccc-1111-dddd2222eeee/machinereferences
```

### Response example

```json
{
    "@odata.context": "https://api.security.microsoft.com/api/$metadata#MachineReferences",
    "value": [
        {
            "id": "3cb5df6bb3640a2d37ad09fcd357b182d684fafc",
            "computerDnsName": "ComputerPII_2ea21b2d97c9df23c143ad9e3e454cb674232529.DomainPII_21eed80b086e79bdfa178eabfa25e8be9acfa346.corp.contoso.com",
            "osPlatform": "WindowsServer2016",
            "rbacGroupName": "UnassignedGroup",

        },
        {
            "id": "3d9b1ca53e8f077199c7dcbfc9dbfa78f9bf1918",
            "computerDnsName": "ComputerPII_001d606fc149567c192747f48fae304b43c0ddba.DomainxPII_21eed80b086e79bdfa178eabfa25e8be9acfa346.corp.contoso.com",
            "osPlatform": "WindowsServer2012R2",
            "rbacGroupName": "UnassignedGroup",

        },
        {
            "id": "3db8b27e6172951d7ea2e2d75945abec56feaf82",
            "computerDnsName": "ComputerPII_ce60cfbjj4b82a091deb5eae560332bba99a9bd7.DomainPII_0bc1aee0fa396d175e514bd61a9e7a5b2b07ee8e.corp.contoso.com",
            "osPlatform": "WindowsServer2016",
            "rbacGroupName": "UnassignedGroup",

        },
        {
            "id": "3bad326dcda5b53fab47408cd4a7080f3f3cc8ab",
            "computerDnsName": "ComputerPII_b6b35960dd6539d1d1cef5ada02e235e7b357408.DomainPII_21eed80b089e76bdfa178eadfa25e8de9acfa346.corp.contoso.com",
            "osPlatform": "WindowsServer2012R2",
            "rbacGroupName": "UnassignedGroup",

        }
]
}
```
