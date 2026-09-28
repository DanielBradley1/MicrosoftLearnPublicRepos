<!-- Source: https://learn.microsoft.com/en-us/entra/identity/app-provisioning/inbound-provisioning-api-custom-attributes -->
<!-- Sitemap-Last-Modified: 2026-08-06 -->

# Extend API-driven provisioning to sync custom attributes

By default, API-driven provisioning apps support processing attributes that are part of the standard SCIM Core User and Enterprise User schema. Your system of record may have custom attributes that you may want to include as part of API-driven provisioning. This advanced tutorial describes how to extend your API-driven provisioning app to process additional custom attributes.

Note

Before trying this advanced scenario, we recommend verifying that your out-of-the-box provisioning app configuration works as expected using one of the following API clients [Graph Explorer](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/inbound-provisioning-api-graph-explorer), [cURL](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/inbound-provisioning-api-curl-tutorial).

## Example scenario

You have configured API-driven provisioning app. You're provisioning app is successfully consuming the attributes that are part of the standard SCIM Core User and Enterprise User schema and provisioning users in Microsoft Entra ID. You now want to send two custom attributes `HireDate` and `JobCode` from your HR system to the inbound provisioning API endpoint. You'd like to map these two custom attributes to Microsoft Entra attributes `employeeHireDate` and `jobTitle`.

## Step 1 - Extend the provisioning app schema

In this step, we'll add the two attributes "HireDate" and "JobCode" that are not part of the standard SCIM schema to the provisioning app and use them in the provisioning data flow.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least an [Application Administrator](https://go.microsoft.com/fwlink/?linkid=2247823).
2. Browse to **Entra ID** > **Enterprise apps**.
3. Open your API-driven provisioning app.
4. Open the **Provisioning** blade.
5. Click on the **Edit Provisioning** button.
6. Expand the **Mappings** section and click on the attribute mapping link.  


   <span class="mx-imgBorder">
   <a href="https://learn.microsoft.com/en-us/entra/identity/app-provisioning/media/inbound-provisioning-api-custom-attributes/edit-attribute-mapping.png#lightbox" data-linktype="relative-path">
   <img src="https://learn.microsoft.com/en-us/entra/identity/app-provisioning/media/inbound-provisioning-api-custom-attributes/edit-attribute-mapping.png" alt="Screenshot of edit attribute mapping." data-linktype="relative-path">
   </a>
   </span>

7. On the **Attribute Mapping** page, select the **Advanced Options** dropdown and then select **Edit target User attributes**.

   <span class="mx-imgBorder">
   <a href="https://learn.microsoft.com/en-us/entra/identity/app-provisioning/media/inbound-provisioning-api-custom-attributes/edit-api-attribute-list.png#lightbox" data-linktype="relative-path">
   <img src="https://learn.microsoft.com/en-us/entra/identity/app-provisioning/media/inbound-provisioning-api-custom-attributes/edit-api-attribute-list.png" alt="Screenshot of edit API attribute list." data-linktype="relative-path">
   </a>
   </span>

8. Scroll down to the end of the **Edit Attribute List** page.
9. Add the following two attributes to the list as SCIM schema extensions. You can use your own SCIM schema namespace.  
   `urn:ietf:params:scim:schemas:extension:contoso:1.0:User:HireDate`  
   `urn:ietf:params:scim:schemas:extension:contoso:1.0:User:JobCode`  


   <span class="mx-imgBorder">
   <a href="https://learn.microsoft.com/en-us/entra/identity/app-provisioning/media/inbound-provisioning-api-custom-attributes/add-custom-attributes.png#lightbox" data-linktype="relative-path">
   <img src="https://learn.microsoft.com/en-us/entra/identity/app-provisioning/media/inbound-provisioning-api-custom-attributes/add-custom-attributes.png" alt="Screenshot of adding custom attributes." data-linktype="relative-path">
   </a>
   </span>

10. **Save** your changes

Note

If you'd like to add only a few additional attributes to the provisioning app, use Microsoft Entra admin center to extend the schema. If you'd like to add more custom attributes \(let's say 20+ attributes\), then we recommend using the [`UpdateSchema` mode of the CSV2SCIM PowerShell script](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/inbound-provisioning-api-powershell#extending-provisioning-job-schema) which automates the above manual process.

## Step 2 - Map the custom attributes

Let's now add these extensions to the provisioning app attribute mapping.

1. Click on the **Add New Mapping** link on the **Attribute mapping** page.  [![Screenshot of add new mapping.](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/media/inbound-provisioning-api-custom-attributes/add-new-mapping.png)](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/media/inbound-provisioning-api-custom-attributes/add-new-mapping.png#lightbox)
2. Map the `urn:ietf:params:scim:schemas:extension:contoso:1.0:User:HireDate` attribute to `employeeHireDate`. Click **OK**.  
   [![Screenshot of hire date mapping.](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/media/inbound-provisioning-api-custom-attributes/hire-date-mapping.png)](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/media/inbound-provisioning-api-custom-attributes/hire-date-mapping.png#lightbox)
3. Next, select the existing mapping for `title` and click on it to edit the mapping.
4. Edit the attribute mapping to an expression that will include the `urn:ietf:params:scim:schemas:extension:contoso:1.0:User:JobCode` as part of the `jobTitle` Microsoft Entra attribute.

   ```
     Join("", [title], "(", [urn:ietf:params:scim:schemas:extension:contoso:1.0:User:JobCode], ")")
   ```


   [![Screenshot of job title mapping.](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/media/inbound-provisioning-api-custom-attributes/job-title-mapping.png)](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/media/inbound-provisioning-api-custom-attributes/job-title-mapping.png#lightbox)


   With this expression mapping, if the `title` is "Tour Lead" and `JobCode`is "TL-1001", then the Microsoft Entra attribute `jobTitle` will be set to "Tour Lead \(TL-1001\)".

5. Save the attribute mappings.

## Step 3 - Upload bulk request with custom attributes

1. Open your API client \(Graph Explorer / cURL\).
2. Copy-paste the [bulk request with custom attributes](#bulk-request-with-custom-attributes).
3. Send the bulk request to your provisioning API endpoint URL.  


   <span class="mx-imgBorder">
   <a href="https://learn.microsoft.com/en-us/entra/identity/app-provisioning/media/inbound-provisioning-api-custom-attributes/upload-bulk-request.png#lightbox" data-linktype="relative-path">
   <img src="https://learn.microsoft.com/en-us/entra/identity/app-provisioning/media/inbound-provisioning-api-custom-attributes/upload-bulk-request.png" alt="Screenshot of bulk upload request." data-linktype="relative-path">
   </a>
   </span>

4. After some time, you can check the provisioning logs to verify the attribute change.  


   <span class="mx-imgBorder">
   <a href="https://learn.microsoft.com/en-us/entra/identity/app-provisioning/media/inbound-provisioning-api-custom-attributes/verify-provisioning-logs.png#lightbox" data-linktype="relative-path">
   <img src="https://learn.microsoft.com/en-us/entra/identity/app-provisioning/media/inbound-provisioning-api-custom-attributes/verify-provisioning-logs.png" alt="Screenshot of provisioning logs." data-linktype="relative-path">
   </a>
   </span>

5. You can also verify the change in the Microsoft Entra user profile. The value for `Employee hire date` reflects your tenant time zone.  


   <span class="mx-imgBorder">
   <a href="https://learn.microsoft.com/en-us/entra/identity/app-provisioning/media/inbound-provisioning-api-custom-attributes/verify-user-profile.png#lightbox" data-linktype="relative-path">
   <img src="https://learn.microsoft.com/en-us/entra/identity/app-provisioning/media/inbound-provisioning-api-custom-attributes/verify-user-profile.png" alt="Screenshot of user profile." data-linktype="relative-path">
   </a>
   </span>

## Appendix

### Bulk request with custom attributes

The bulk request includes the custom attributes configured in the steps above.

**Request body**

```http
{
    "schemas": ["urn:ietf:params:scim:api:messages:2.0:BulkRequest"],
    "Operations": [
    {
        "method": "POST",
        "bulkId": "701984",
        "path": "/Users",
        "data": {
            "schemas": ["urn:ietf:params:scim:schemas:core:2.0:User",
            "urn:ietf:params:scim:schemas:extension:enterprise:2.0:User",
            "urn:ietf:params:scim:schemas:extension:contoso:1.0:User"],
            "externalId": "701984",
            "userName": "bjensen@example.com",
            "name": {
                "formatted": "Ms. Barbara J Jensen, III",
                "familyName": "Jensen",
                "givenName": "Barbara",
                "middleName": "Jane",
                "honorificPrefix": "Ms.",
                "honorificSuffix": "III"
            },
            "displayName": "Babs Jensen",
            "nickName": "Babs",
            "emails": [
            {
              "value": "bjensen@example.com",
              "type": "work",
              "primary": true
            }
            ],
            "addresses": [
            {
              "type": "work",
              "streetAddress": "234300 Universal City Plaza",
              "locality": "Hollywood",
              "region": "CA",
              "postalCode": "91608",
              "country": "USA",
              "formatted": "100 Universal City Plaza\nHollywood, CA 91608 USA",
              "primary": true
            }
            ],
            "phoneNumbers": [
            {
              "value": "555-555-5555",
              "type": "work"
            }
            ],
            "userType": "Employee",
            "title": "Tour Guide",
            "preferredLanguage": "en-US",
            "locale": "en-US",
            "timezone": "America/Los_Angeles",
            "active":true,
            "urn:ietf:params:scim:schemas:extension:enterprise:2.0:User": {
                "employeeNumber": "701984",
                "costCenter": "4130",
                "organization": "Universal Studios",
                "division": "Theme Park",
                "department": "Tour Operations",
                "manager": {
                  "value": "89607",
                  "displayName": "John Smith"
                 }
            },
            "urn:ietf:params:scim:schemas:extension:contoso:1.0:User": {
                "HireDate": "2021-05-01T00:00:00-05:00",
                "JobCode": "TG-1001"
            }            
        }
    },
    {
        "method": "POST",
        "bulkId": "701985",
        "path": "/Users",
        "data": {
            "schemas": ["urn:ietf:params:scim:schemas:core:2.0:User",
            "urn:ietf:params:scim:schemas:extension:enterprise:2.0:User",
            "urn:ietf:params:scim:schemas:extension:contoso:1.0:User"],
            "externalId": "701985",
            "userName": "Kjensen@example.com",
            "name": {
                "formatted": "Ms. Kathy J Jensen, III",
                "familyName": "Jensen",
                "givenName": "Kathy",
                "middleName": "Jane",
                "honorificPrefix": "Ms.",
                "honorificSuffix": "III"
            },
            "displayName": "Kathy Jensen",
            "nickName": "Kathy",
            "emails": [
            {
              "value": "kjensen@example.com",
              "type": "work",
              "primary": true
            }
            ],
            "addresses": [
            {
              "type": "work",
              "streetAddress": "100 Oracle City Plaza",
              "locality": "Hollywood",
              "region": "CA",
              "postalCode": "91618",
              "country": "USA",
              "formatted": "100 Oracle City Plaza\nHollywood, CA 91618 USA",
              "primary": true
            }
            ],
            "phoneNumbers": [
            {
              "value": "555-555-5545",
              "type": "work"
            }
            ],
            "userType": "Employee",
            "title": "Tour Lead",
            "preferredLanguage": "en-US",
            "locale": "en-US",
            "timezone": "America/Los_Angeles",
            "active":true,
            "urn:ietf:params:scim:schemas:extension:enterprise:2.0:User": {
              "employeeNumber": "701984",
              "costCenter": "4130",
              "organization": "Universal Studios",
              "division": "Theme Park",
              "department": "Tour Operations",
              "manager": {
                "value": "701984",
                "displayName": "Barbara Jensen"
             }
            },
            "urn:ietf:params:scim:schemas:extension:contoso:1.0:User": {
                "HireDate": "2022-07-15T00:00:00-05:00",
                "JobCode": "TL-1003"
            }            
        }
    }
],
    "failOnErrors": null
}
```

## Next steps

- [Troubleshoot issues with the inbound provisioning API](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/inbound-provisioning-api-issues)
- [Frequently asked questions about API-driven inbound provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/inbound-provisioning-api-faqs)
- [Quick start using PowerShell](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/inbound-provisioning-api-powershell)
- [Quick start using Azure Logic Apps](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/inbound-provisioning-api-logic-apps)
