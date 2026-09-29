<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/onboarding-notification -->
<!-- Sitemap-Last-Modified: 2026-07-29 -->

# Create a notification rule when a local onboarding or offboarding script is used

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

Create a notification rule so that when a local onboarding or offboarding script is used, you are notified.

## Before you begin

You need to have access to:

- Power Automate \(Per-user plan at a minimum\). For more information, see [Power Automate pricing page](https://make.powerautomate.com/pricing/).
- Azure Table or SharePoint List or Library / SQL DB.

## Create the notification flow

Perform the following steps to create the notification flow in Power Automate:

1. Go to the [Power Automate portal](https://make.powerautomate.com/) and sign in.
2. Navigate to **My flows > New > Scheduled - from blank**.

   [![The flow](https://learn.microsoft.com/en-us/defender-endpoint/media/new-flow.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/new-flow.png#lightbox)
3. Build a scheduled flow.

   1. Enter a flow name.
   2. Specify the start and time.
   3. Specify the frequency. For example, every 5 minutes.


   [![The notification flow](https://learn.microsoft.com/en-us/defender-endpoint/media/build-flow.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/build-flow.png#lightbox)

4. Select the + button to add a new action. This action adds an HTTP request to the Defender for Endpoint devices API. You can also replace it with the out-of-the-box **WDATP Connector** \(action: **Machines - Get list of machines**\).

   [![The recurrence and add action](https://learn.microsoft.com/en-us/defender-endpoint/media/recurrence-add.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/recurrence-add.png#lightbox)
5. Enter the following HTTP fields:

   - Method: **GET** as a value to get the list of devices.
   - URI: Enter `https://api.securitycenter.microsoft.com/api/machines`.
   - Authentication: Select **Active Directory OAuth**.
   - Tenant: Sign-in to [https://portal.azure.com](https://portal.azure.com) and navigate to **Microsoft Entra ID > App Registrations** and get the Tenant ID value.
   - Audience: `https://securitycenter.onmicrosoft.com/windowsatpservice\`
   - Client ID: Sign-in to [https://portal.azure.com](https://portal.azure.com) and navigate to **Microsoft Entra ID > App Registrations** and get the Client ID value.
   - Credential Type: Select **Secret**.
   - Secret: Sign-in to [https://portal.azure.com](https://portal.azure.com) and navigate to **Microsoft Entra ID > App Registrations** and get the Tenant ID value.


   [![The HTTP conditions](https://learn.microsoft.com/en-us/defender-endpoint/media/http-conditions.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/http-conditions.png#lightbox)

6. Add a new step by selecting **Add new action** then search for **Data Operations** and select **Parse JSON**.

   [![The data operations entry](https://learn.microsoft.com/en-us/defender-endpoint/media/data-operations.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/data-operations.png#lightbox)
7. Add Body in the **Content** field.

   [![The parse JSON section](https://learn.microsoft.com/en-us/defender-endpoint/media/parse-json.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/parse-json.png#lightbox)
8. Select the **Use sample payload to generate schema** link.  [![The parse JSON with payload](https://learn.microsoft.com/en-us/defender-endpoint/media/parse-json-schema.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/parse-json-schema.png#lightbox)
9. Copy and paste the following JSON snippet:

   ```json
   {
       "type": "object",
       "properties": {
           "@@odata.context": {
               "type": "string"
           },
           "value": {
               "type": "array",
               "items": {
                   "type": "object",
                   "properties": {
                       "id": {
                           "type": "string"
                       },
                       "computerDnsName": {
                           "type": "string"
                       },
                       "firstSeen": {
                           "type": "string"
                       },
                       "lastSeen": {
                           "type": "string"
                       },
                       "osPlatform": {
                           "type": "string"
                       },
                       "osVersion": {},
                       "lastIpAddress": {
                           "type": "string"
                       },
                       "lastExternalIpAddress": {
                           "type": "string"
                       },
                       "agentVersion": {
                           "type": "string"
                       },
                       "osBuild": {
                           "type": "integer"
                       },
                       "healthStatus": {
                           "type": "string"
                       },
                       "riskScore": {
                           "type": "string"
                       },
                       "exposureScore": {
                           "type": "string"
                       },
                       "aadDeviceId": {},
                       "machineTags": {
                           "type": "array"
                       }
                   },
                   "required": [
                       "id",
                       "computerDnsName",
                       "firstSeen",
                       "lastSeen",
                       "osPlatform",
                       "osVersion",
                       "lastIpAddress",
                       "lastExternalIpAddress",
                       "agentVersion",
                       "osBuild",
                       "healthStatus",
                       "rbacGroupId",
                       "rbacGroupName",
                       "riskScore",
                       "exposureScore",
                       "aadDeviceId",
                       "machineTags"
                   ]
               }
           }
       }
   }
   ```

10. Extract the values from the JSON call and check if the onboarded devices is / are already registered at the SharePoint list as an example:

    - If yes, no notification is triggered
    - If no, will register the newly onboarded devices in the SharePoint list and a notification is sent to the Defender for Endpoint admin


    [![The application of the flow to each element](https://learn.microsoft.com/en-us/defender-endpoint/media/flow-apply.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/flow-apply.png#lightbox)


    [![The application of the flow to the Get items element](https://learn.microsoft.com/en-us/defender-endpoint/media/apply-to-each.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/apply-to-each.png#lightbox)

11. Under **Condition**, add the following expression: "length\(body\('Get\_items'\)?\['value'\]\)" and set the condition to equal to 0.

    [![The application of the flow to each condition](https://learn.microsoft.com/en-us/defender-endpoint/media/apply-to-each-value.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/apply-to-each-value.png#lightbox)  [![The condition-1](https://learn.microsoft.com/en-us/defender-endpoint/media/conditions-2.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/conditions-2.png#lightbox)  [![The condition-2](https://learn.microsoft.com/en-us/defender-endpoint/media/condition3.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/condition3.png#lightbox)  [![The Send an email section](https://learn.microsoft.com/en-us/defender-endpoint/media/send-email.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/send-email.png#lightbox)

## Review the alert notification email

The following image is an example of an email notification.

[![The email notification screen](https://learn.microsoft.com/en-us/defender-endpoint/media/alert-notification.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/alert-notification.png#lightbox)

## Tips for filtering and reducing duplicate alerts

Use the following tips when configuring the notification flow:

- In the device query, you can filter by using the lastSeen property only:

  - Every 60 min:

    - Take all devices last seen in the past seven days.

- For each device:

  - If last seen property is on the one hour interval of \[-7 days, -7days + 60 minutes\] -> Alert for offboarding possibility.
  - If first seen is on the past hour -> Alert for onboarding.

With this filtering approach, duplicate alerts are not generated.

There are tenants that have numerous devices. Getting all those devices might require paging.

You can split the device lookup into two queries:

1. For offboarding, take only the one-hour interval of \[-7 days, -7 days + 60 minutes\] using the OData $filter and only notify if the conditions are met.
2. Take all devices last seen in the past hour and check first seen property for them \(if the first seen property is within the past hour, the last seen must also be within the same past-hour window\).
