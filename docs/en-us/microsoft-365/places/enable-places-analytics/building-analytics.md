<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/places/enable-places-analytics/building-analytics -->
<!-- Sitemap-Last-Modified: 2026-08-05 -->

# Building analytics

Work plan settings that allow employees to indicate their intent to come into the office, combined with actual building occupancy data, offer real estate and facility managers a valuable tool to understand, analyze, and optimize building space use.

By comparing work plan data, which reflects employee intentions, with actual occupancy data, you can identify discrepancies between planned and real space usage.

Here are the signals used in building analytics:

- **Building use based on intent to come into the office** Building analytics uses employee work plans to assess intent-driven space use.
- **Building use based on actual occupancy** Building analytics uses badge data to infer the number of employees present in a building, providing a measure of actual building occupancy.
- **People data** Microsoft Places analytics makes use of people profile API data sourced from Microsoft Entra ID data \(or\) through external connectors to analyze employees assigned to a specific building and employees under a specific leader. This data helps in mapping users to a specific building, improving the data coverage for building analytics.

**Building analytics signal**

**Building utilization based on intent to use**

Building analytics uses work plan data to track the intended building occupancy and expected hybrid trends, providing insight into employee preferences on office visits.

The source for work plan data comes from the Flexible Work Hours \(FWH\) setting available for users in Microsoft Places and in the Outlook app. The work plan data is dependent on the availability of the people data \(from people profile datasets\). People data helps with mapping employees who set work plans without choosing buildings as their assigned building in people data.

**Building utilization based on actual occupancy**

Building analytics uses occupancy data to detect the actual presence of people in buildings. Currently, we support the following building occupancy data:

- Badge access data

Note

For the building analytics dashboards to show accurate values, people data must be mapped to the buildings onboarded to Microsoft Places.

In the next section, we'll cover details about people data onboarding along with building occupancy data onboarding.

**Onboard people data**

**General information**

Microsoft Places analytics uses the people profile API data to associate users to a specific location/building. People profile data generally pulls data from Microsoft Entra ID and, if you added connectors to bring people data to Microsoft 365 applications, then the relevant data is reflected in people profile dataset.

- Assigned headcount in building analytics is derived from the employee to building mapping.
- For the leader filter features to function accurately employee manager mapping should be available in people profile dataset.

**Data format**

Microsoft Places analytics looks for specific set of fields in people profile dataset to create mapping between employees, their assigned buildings, and their managers.

- **OfficeLocation** This is the people profile API property used by Places to associate an employee to a building.

Note

This property must match with the building name set in Places Directory to create the mapping accurately.

- **Manager** This is the people profile API property used by Places to associate users to their leaders/managers.

To learn more about profile API here Data format, see [Use the Profile API in Microsoft Graph to retrieve information about yourself or another user](https://learn.microsoft.com/en-us/graph/api/resources/profile-example).

**Data updates to Microsoft Entra ID**

To match people profile data with attendance data, their Microsoft Entra ID location should be updated. It can be done using one of the following methods.

**Azure portal**

- **Access the Azure portal**: Go to the Azure portal and sign in with your credentials.
- **Navigate to the Azure Active Directory**: In the left-hand navigation pane, select **Azure Active Directory**.
- **Find the user**: Under **Manage**, select **Users**, and then search for the user whose location you want to update.
- **Edit user information**: Select the user's name to open their profile, then select **Edit** to update their information.
- **Update the location**: In the **Job info** section, you can update the user's location details. Make sure to save your changes.
- **Update manager**: In the **Job info** section, you can update the user's manager details. Make sure to save your changes.

To learn more about updating Microsoft Entra ID data, see [Add or update a user's profile information and settings in the Microsoft Entra admin center](https://learn.microsoft.com/en-us/entra/fundamentals/how-to-manage-user-profile-info).

**Update Microsoft Entra ID attributes using a PowerShell script**

**PowerShell**

```powershell
# Connect to Azure AD
Connect-AzureAD
```

**Update user location**

**PowerShell**

```powershell
Update-AzADUser -UPNOrObjectId user@domain.com -OfficeLocation “18/2111”
```

For more information, see [Update-AzADUser](https://learn.microsoft.com/en-us/powershell/module/az.resources/update-azaduser).

**Update Microsoft Entra ID attributes using Graph API**

Start by understanding the user resource type. For more information, see [User resource type](https://learn.microsoft.com/en-us/graph/api/resources/user).

- Sign in to Graph Explore. For more information, see [Graph Explorer](https://learn.microsoft.com/en-us/graph/graph-explorer/graph-explorer-overview).
- Invoke Update user. For more information, see [Update user](https://learn.microsoft.com/en-us/graph/api/user-update).

**Sample:**

**PowerShell**

```http
PATCH https://graph.microsoft.com/v1.0/users/{id}
Content-type: application/json

{
  "officeLocation": "18/2111"
}
```

**Data validation and troubleshooting**

- Verify that the headcount property in the Microsoft Places analytics dashboard shows the same number of users who have been assigned that building.
- The leader filters in the Building analytics page of Places analytics and should have the right leader's data filled in.
- If the changes are being made by updating user location or manager, it should be reflected in Places analytics in 3 to 4 days.

**Security and privacy considerations**

Microsoft Places analytics always aggregates the data points to show building use numbers. Users can't identify information about any specific, individual employees. Microsoft Places uses the people profile data used by other Microsoft 365 applications.

**Onboard badge data**

You can use existing badge access systems to enhance Places Analytics report on building occupancy dashboards.

**Process to enable badge data**

- Step 1: Add badge-access devices to Microsoft Places \(optional, but highly recommended\).
- Step 2: Upload badge data telemetry to Microsoft Places.

Note

Prior to onboarding badge data, ensure that People data has been configured and that people have been assigned to the building. Badge data is validated against the People data. The system filters out the badge data of users who aren't assigned to Microsoft Places.

**Step 1: Add badge-access devices to Microsoft Places**

The first step involves uploading badge access device metadata and mapping devices to a PlaceId in Microsoft Places. This step helps to contextualize the badge signals when it reaches Microsoft Places. You can add badge access devices to Microsoft Places using two options:

- **Option 1**: Using PowerShell cmdlets
- **Option 2**: Using Microsoft Graph APIs

**Option 1: Using PowerShell cmdlets**

PowerShell cmdlets are available to manage devices in Microsoft Places. To learn more about Microsoft Places cmdlets, see the [Microsoft Places cmdlets module for PowerShell](https://www.powershellgallery.com/packages/MicrosoftPlaces/0.32.0-alpha).

Note

To run cmdlets, you must have the TenantPlacesManagement role assigned.

**Device-data formats for cmdlets**

| **Column** | **Description** | **Notes** | **Example** |
| --- | --- | --- | --- |
| **DeviceId** \(required\) | The unique identifier of the device \(recommended: Manufacturer\_DeviceUniqueId\). | Must match the ID of the telemetry sent. | Manuf1\_3455 |
| **DisplayName** | The display name of the device. | You can use a friendly name if applicable. | Manuf1\_3455 |
| **Description** | The description of the device. |  |  |
| **MacAddress** | The Mac address of the device. | Supplier provided \(if available\). |  |
| **Manufacturer** \(required\) | The manufacturer of the device. | Provided by the IT admin. | Manuf1 |
| **IPV4Address** | The IPV4Address of the device. | Supplier provided \(if available\). |  |
| **IPV6Address** | The IPV6Address of the device. | Supplier provided \(if available\). |  |
| **PlaceId** | The PlaceId to which your device is mapped in Places. | The IT admin maps DeviceID to the DisplayName field from a list of rooms. | 76fe540f-01a9-425e-acd5-5d7d1da44fbf |
| **Tags** | A list of custom tags associated with the device to help with search. |  | \["IsVirtual\_False", "Building\_121"\] |
| **Sensor.SensorId** | The unique identifier of a sensor within the device. | Must come in the standard telemetry payload. | Badge |
| **Sensor.DisplayName** | The display Name of the sensor. | You can use a friendly name \(if applicable\). | Paperclip |
| **Sensor.SensorType** \(required\) | The type of sensor. | A validated list \(see examples\). | Badge |
| **Sensor.PlaceId** | The unique identifier of the place served by the sensor \(you only need to provide this information if the sensor is in a different place than the device's location\). |  | 76fe540f-01a9-425e-acd5-5d7d1da44fbf |

**Add badge-access device to Microsoft Places using cmdlets**

| **Cmdlet name** | **Description** | **Parameters** |
| --- | --- | --- |
| New-PlaceDevice | Creates a new device. | DeviceId \(required\), DisplayName, Description, MACAddress, Manufacturer \(required\), IPV4Address, IPV6Address, PlaceId \(required\), TagsSensors \(required\) |
| Remove-PlaceDevice | Deletes a device. | ID \(required\) |
| Set-PlaceDevice | Updates a device. | ID \(required\), DeviceId \(required\), DisplayName, Description, MACAddress, Manufacturer \(required\), IPV4Address, IPV6Address, PlaceId, Tags, Sensors \(required\) |
| Get-PlaceDevice | Gets a device. | Id, Filter, Top |

**Steps: Using PowerShell cmdlets**

- Open **PowerShell 7** \(not as an administrator\).
- Install Microsoft Places by running the following **Windows PowerShell** cmdlet. For more information about Microsoft Places installation, see the [Microsoft Places PowerShell Gallery](https://www.powershellgallery.com/packages/MicrosoftPlaces/0.32.0-alpha).

**PowerShell**

```powershell
Install-Module -Name MicrosoftPlaces -AllowPrerelease -Force
```

- Import the Microsoft Places module by running the following **Windows PowerShell** cmdlet.

**PowerShell**

```powershell
Import-Module -Name MicrosoftPlaces
```

- After installing and importing the module, connect to the Microsoft Places module by running the following **Microsoft Places** PowerShell cmdlet.

**PowerShell**

```powershell
Connect-MicrosoftPlaces
```

- Use New-PlaceDevice cmdlet to add badge access device.

**PowerShell**

```powershell
New-PlaceDevice -DeviceId "contoso_9D6816" -DisplayName "Contoso 9D6816 Device" -Description "Contoso 9D6816 Device" -MACAddress "00:0A:95:9D:68:16" -Manufacturer "Contoso" -IPV4Address "192.168.1.100" -IPV6Address "2001:db8::ff00:42:8329" -PlaceId "acfa3bc0- 2b83-425b-8910-84a0250e9671" -Tags "BuildingA" -Sensors (New-Object MicrosoftPlaces.PlacesDevices.Sensor -Property @{SensorType="badge"})
```

Note

The Sensors parameter in this example is an object of type MicrosoftPlaces.PlacesDevices.Sensor having fields mentioned in the sample.

- Use Get-PlaceDevice to view list of devices. By default, it returns 10 devices. To return more devices, add the -top parameter as shown in this example.

**PowerShell**

```powershell
Get-PlaceDevice -top 100
```

- Use Set-PlaceDevice to update a device with existing ID.

**PowerShell**

```powershell
Set-PlaceDevice -Id "e5a216ff-1d32-4647-8dab-a2523ee5796e" -DeviceId "contoso_7D6816" -DisplayName "Contoso 7D6816 Device" -Description "Contoso 9D6816 Device" -MACAddress "00:0A:95:9D:68:16" -Manufacturer "Contoso" -IPV4Address "192.168.1.100" -IPV6Address "2001:db8::ff00:42:8329" -PlaceId "acfa3bc0- 2b83-425b-8910-84a0250e9671" -Tags "BuildingA" -Sensors (New-Object MicrosoftPlaces.PlacesDevices.Sensor -Property @{SensorType="badge"})
```

Note

Provide details of all the parameters \(both mandatory and optional\) while updating a device. In the absence of a parameter value, it resets the value to default empty value.

- Use Remove-PlaceDevice to delete a device.

**PowerShell**

```powershell
Remove-PlaceDevice -Id "e5a216ff-1d32-4647-8dab-a2523ee5796e"
```

**Steps: Using the Microsoft Graph API**

To build an application to automate registering and onboarding badge-access devices, APIs are available through Microsoft Graph. To use APIs, follow these steps.

- Create an app registration in Microsoft Entra. To learn more about the PlaceDeviceRead.All and PlaceDevice.ReadWrite.All permissions, see the [Microsoft Graph Permissions Reference](https://learn.microsoft.com/en-us/graph/permissions-reference).
- Build and deploy an application to sync device information across Microsoft Places and your partners.

**Device-data formats used in the Microsoft Graph API**

| **Column** | **Description** | **Notes** | **Example** |
| --- | --- | --- | --- |
| **DeviceId** \(required\) | The unique identifier of the device \(recommended: Manufacturer\_DeviceUniqueId\). | Must match the ID of the telemetry sent. | Manuf1\_3455 |
| **DisplayName** | The display name of the device. | You can use a friendly name, if applicable. | Manuf1\_3455 |
| **Description** | The description of the device. |  |  |
| **MacAddress** | The Mac address of the device. | Supplier provided \(if available\). |  |
| **Manufacturer** \(required\) | The manufacturer of the device. | Provided by the IT admin. | Manuf1 |
| **IPV4Address** | The IPV4Address of the device. | Supplier provided, if available. |  |
| **IPV6Address** | The IPV6Address of the device. | Supplier provided, if available. |  |
| **PlaceId** \(required\) | The PlaceId to which your device is mapped in Microsoft Places. | The IT admin maps DeviceID to the DisplayName field from a list of rooms. | 76fe540f-01a9-425e-acd5-5d7d1da44fbf |
| **Tags** | A list of custom tags associated with the device to help with search. |  | \["IsVirtual\_False", "Building\_121"\] |
| **Sensor.SensorId** \(required\) | The unique identifier of a sensor within the device. | Must come in the standard telemetry payload. | Badge |
| **Sensor.DisplayName** | The display Name of the sensor. | You can use a friendly name \(if applicable\). | Paperclip |
| **Sensor.SensorType** \(required\) | The type of sensor. | A validated list \(see examples\). | Badge |
| **Sensor.PlaceId** | The unique identifier of the place served by the sensor \(you only need to provide this information if the sensor is in a different place than the device's location\). |  | 76fe540f-01a9-425e-acd5-5d7d1da44fbf |

To learn more about sensor devices, see the following Microsoft Graph APIs:

- **View badge access devices**: [List sensorDevices](https://learn.microsoft.com/en-us/graph/api/workplace-list-sensordevices).

**PowerShell**

```http
GET https://graph.microsoft.com/beta/workplace/sensorDevices
```

- **Create new badge access devices**: [Create workplaceSensorDevice](https://learn.microsoft.com/en-us/graph/api/workplace-post-sensordevices).

**PowerShell**

```http
POST https://graph.microsoft.com/beta/workplace/sensorDevices
```

```json
{
    "deviceId": "contoso_7D6816",
    "displayName": "Contoso 7D6816 Device",
    "description": "Contoso 7D6816 Device",
    "macAddress": "00:0A:95:9D:68:16",
    "manufacturer": "Contoso",
    "ipV4Address": "192.168.1.100",
    "ipV6Address": "2001:db8::ff00:42:8329",
    "placeId": "acfa3bc0- 2b83-425b-8910-84a0250e9671",
    "tags": [
        "BuildingA"
    ],
    "sensors": [
        {
            "sensorId": "Badge",
            "displayName": null,
            "sensorType": "badge",
            "placeId": "acfa3bc0- 2b83-425b-8910-84a0250e9671"
        }
    ]
}
```

- **View a specific device**: [Get workplaceSensorDevice](https://learn.microsoft.com/en-us/graph/api/workplacesensordevice-get).

**PowerShell**

```http
GET https://graph.microsoft.com/beta/workplace/sensorDevices/052062b9-38f6-48d4-a638-05a72c79419b
```

- **Update existing badge-access devices**: [Update workplaceSensorDevice](https://learn.microsoft.com/en-us/graph/api/workplacesensordevice-update).

**PowerShell**

```http
PATCH https://graph.microsoft.com/beta/workplace/sensorDevices/052062b9-38f6-48d4-a638-05a72c79419b
```

```json
{
    "deviceId": "contoso_7D6816",
    "displayName": "Contoso 7D6816 Device",
    "description": "Contoso 7D6816 Device",
    "macAddress": "00:0A:95:9D:68:16",
    "manufacturer": "Contoso2",
    "ipV4Address": "192.168.1.100",
    "ipV6Address": "2001:db8::ff00:42:8329",
    "placeId": "acfa3bc0- 2b83-425b-8910-84a0250e9671",
    "tags": [
         "BuildingA"
     ],
    "sensors": [
        {
            "sensorId": "Badge",
            "displayName": null,
            "sensorType": "badge",
            "placeId": "acfa3bc0- 2b83-425b-8910-84a0250e9671"
        }
    ]
}
```

- **To delete a device**: [Delete workplaceSensorDevice](https://learn.microsoft.com/en-us/graph/api/workplacesensordevice-delete).

**PowerShell**

```http
DELETE https://graph.microsoft.com/beta/workplace/sensorDevices/052062b9-38f6-48d4-a638-05a72c79419b

GET https://graph.microsoft.com/beta/workplace/sensorDevices/052062b9-38f6-48d4-a638-05a72c79419b
```

**Upload badge data telemetry to Microsoft Places**

Upload data from your badge-entry system to generate building occupancy dashboards in Places Analytics.

- The DeviceId is used to match the badge event to a specific building. In the absence of a DeviceId, LocationHint is used. We strongly recommend you onboard your devices to accurately map building occupancy.
- LocationHint must match the building name in Microsoft Places directory if you haven't onboarded devices to Microsoft Places.
- Users from Badge data are validated against People data \(from the profile API\) to make it available in the Building analytics page.

**Option 1: Using the Push-Dataset cmdlet**

These steps are required to push badge data to Microsoft Places:

- Download badge data from existing systems.
- Prepare CSV file as per the badge-data format in the following section.
- Push prepared CSV data to Microsoft Places.

**Prepare the CSV file**

**Badge-data format**: Use the following schema when uploading badge information.

| Column | Type | Description |
| --- | --- | --- |
| DeviceId | String | Optional. The device ID indicates which device generated the signal. |
| EventType | String | The action of the badge, which depends on the sensor type. The value can be BadgeIn. |
| UserID | String | Optional. The badged user ID. |
| UserName | String | Optional. The badged username. |
| UserEmail | String | The badged user email address. |
| LocationHint | String | Building name. Location from where badge signal in recorded. |
| IngestionTime | Timestamp | The timestamp of the badge signal, which indicates when the event occurred. |

- Skip the CSV column headers while uploading this data.
- CSV column values should be in order with the schema mentioned earlier.
- User's Location to Places Mapping Logic:

If the DeviceId isn't available, but LocationHint is available, map LocationHint with PlaceName in the people directory, and filters out which doesn't map.

If both LocationHint and DeviceId are available, map LocationHint with PlaceName in the people directory. If it doesn't map, then map with PlaceIdFromDeviceInventory, else filters out which doesn't map.

**CSV sample file content:**

The following sample shows two entries in a CSV file.

**PowerShell**

```text
BadgeEntry1_BENGALURU (BANGALORE)-FERNS_MIRPL,BadgeIn,167b4de9-05c8-422e-916e-9d5be5b381b2,AlexW,AlexW@SkelligeIsland.OnMicrosoft.com,BENGALURU (BANGALORE)-FERNS_MIRPL,2024-06-28T09:36:05.144Z

BadgeEntry1_BENGALURU (BANGALORE)-FERNS_MIRPL,BadgeIn,167b4de9-05c8-422e-916e-9d5be5b381b2,AllanD,AllanD@SkelligeIsland.OnMicrosoft.com,BENGALURU (BANGALORE)-FERNS_MIRPL,2024-06-28T10:36:05.144Z
```

**Push badge data signal to Microsoft Places using cmdlets**

To learn more about Microsoft Places cmdlets, see the [Microsoft Places cmdlets module for PowerShell](https://www.powershellgallery.com/packages/MicrosoftPlaces/0.32.0-alpha).

Note

To run Microsoft Places cmdlets, you must have the TenantPlacesManagement role assigned.

- Open **PowerShell 7** \(not as an administrator\).
- Install Microsoft Places by running the following **Windows PowerShell** cmdlet. For more information on Microsoft Places installation, see the [Microsoft Places PowerShell Gallery](https://www.powershellgallery.com/packages/MicrosoftPlaces/0.32.0-alpha).

**PowerShell**

```powershell
Install-Module -Name MicrosoftPlaces -AllowPrerelease -Force
```

- Import the Microsoft Places module by running the following **Windows PowerShell** cmdlet.

**PowerShell**

```powershell
Import-Module -Name MicrosoftPlaces
```

- Connect to the Microsoft Places module by running the following **Places PowerShell** cmdlet.

**PowerShell**

```powershell
Connect-MicrosoftPlaces
```

- Upload the badge dataset from the location on your device \(using the folder and path\) by running the following **Microsoft Places** PowerShell cmdlet.

**PowerShell**

```powershell
Push-Dataset -Type BadgeSwipe -Path C:\\sensordata\\
```

This is a CreateOrOverwrite operation. For example, new badge data gets overwritten to the current day folder.

**Option 2: Automate using the Microsoft Graph API**

The following steps are required to push badge data to Microsoft Places using the Graph API:

- Download badge data from existing systems.
- Prepare the API request using the badge-data format in the following section.

**PowerShell**

```http
POST https://graph.microsoft.com/beta/workplace/sensorDevices/ingestTelemetry

{
    "telemetry": [
        {
            "deviceId": "BadgeEntry1_BANGALORE-FERNS_MIRPL",
            "sensorType": "badge",
            "eventValue": {
                "eventType": "badgeIn",
                "user": {
                    "id": "167b4de9-05c8-422e-916e-9d5be5b381b2",
                    "displayName": "AlexW",
                    "email": "AlexW@SkelligeIsland.OnMicrosoft.com"
                }
             },
             "locationHint": "BENGALURU (BANGALORE)-FERNS_MIRPL",
             "timestamp": "2024-06-28T09:36:05.144Z"
        }
    ]
}
```

- Run the API to push the data to Microsoft Places.

**Badge data signal-data format**

| Parameter | Type | Description |
| --- | --- | --- |
| telemetry \(required\) | [workplaceSensorDeviceTelemetry](https://learn.microsoft.com/en-us/graph/api/resources/workplacesensordevicetelemetry), collectionText | A collection of the telemetry data collected and reported by a sensor on a badge device. |
| deviceId | String | The user-defined unique identifier of the device provided at the time of creation. Don't use the system generated identifier of the device. |
| locationHint | String | The additional information to indicate the location of the device. |
| timestamp \(required\) | DateTimeOffset | the date and time when the sensor measured and reported its value. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2024 is 2024-01-01T00:00:00Z. |
| sensorType \(required\) | [workplaceSensorType](https://learn.microsoft.com/en-us/graph/api/resources/workplacesensor) | The type of sensor. The possible values are: badge. |
| eventValue \(required\) | [workplaceSensorEventValue](https://learn.microsoft.com/en-us/graph/api/resources/workplacesensoreventvalue) | The extra values associated with badge signals. |
| eventValue.eventType \(required\) | [workplaceSensorEventType](https://learn.microsoft.com/en-us/graph/api/resources/workplacesensoreventvalue) | The type of possible sensor event value. The possible values are: badgeIn. |
| eventValue.user \(required\) | [emailIdentity](https://learn.microsoft.com/en-us/graph/api/resources/emailidentity) | The unique identifier of a user. It can be an email or a Microsoft Entra ID. |
| eventValue.user.displayName | String | Display name of the user. Inherited from [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity). |
| eventValue.user.email \(required\) | String | Email address of the user. |
| eventValue.user.id | String | The unique identifier for the user. Inherited from [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity). |

**Push badge data signal to Microsoft Places using Microsoft Graph API**

To build an application to automate, upload of telemetry, APIs are available through Microsoft Graph. To use APIs, follow these steps.

- Create an app registration in Microsoft Entra.

To learn more about the PlaceDeviceRead.All and PlaceDevice.ReadWrite.All permissions, see the [Microsoft Graph Permissions Reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

- Build and deploy an application to sync telemetry across Microsoft Places and your partners.
- Use the IngestTelemetry API to push badge data to Microsoft Places.

For more information, see [workplaceSensorDevice](https://learn.microsoft.com/en-us/graph/api/workplacesensordevice-ingesttelemetry).

**Example:**

**PowerShell**

```http
POST https://graph.microsoft.com/beta/workplace/sensorDevices/ingestTelemetry

{
    "telemetry": [
        {
            "deviceId": "BadgeEntry1_BANGALORE-FERNS_MIRPL",
            "sensorType": "badge",
            "eventValue": {
            "eventType": "badgeIn",
                "user": {
                    "id": "167b4de9-05c8-422e-916e-9d5be5b381b2",
                    "displayName": "AlexW",
                    "email": "AlexW@SkelligeIsland.OnMicrosoft.com"
                }
             },
            "locationHint": "BENGALURU (BANGALORE)-FERNS_MIRPL",
            "timestamp": "2024-06-28T09:36:05.144Z"
        }
    ]
}
```

**Data validation and troubleshooting building analytics**

- Make sure the onboarded user email id matches with user email ID in Microsoft Entra ID.
- Make sure the user location matches with user location in Microsoft Entra ID.
- You should be able to view Building occupancy based dashboard light up within 48 hours once you onboard the badge data.

**Security and privacy considerations for building analytics**

- Uploaded badge data retention is 28 days. Aggregated processed data is stored for 90 days.
- Data is stored in privacy compliant Azure data lake.
- Leaders having fewer than 10 members under them aren't shown in the leader hierarchy due to privacy risks.

Days with fewer than 10 members coming to buildings aren't shown in actual building occupancy dashboards due to privacy risks.
