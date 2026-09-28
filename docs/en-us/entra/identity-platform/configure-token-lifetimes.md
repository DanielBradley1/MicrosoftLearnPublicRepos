<!-- Source: https://learn.microsoft.com/en-us/entra/identity-platform/configure-token-lifetimes -->
<!-- Sitemap-Last-Modified: 2026-08-28 -->

# Configure token lifetime policies

This article explains how to configure token lifetime policies for access, SAML, and ID tokens issued by the Microsoft identity platform. Learn how to set token lifetimes for all apps in your organization, specific apps, or multi-tenant applications to improve security and authentication management. You might want to increase the token lifetime so that a script will run for more than an hour. Many Microsoft libraries and applications, such as Microsoft Graph PowerShell SDK, proactively refresh access tokens as needed and you don't need to make changes to the access token policy. For more information, see [configurable token lifetimes](https://learn.microsoft.com/en-us/entra/identity-platform/configurable-token-lifetimes). To control how frequently users are required to sign in, use [Conditional Access sign-in frequency](https://learn.microsoft.com/en-us/entra/identity/conditional-access/howto-conditional-access-session-lifetime) instead.

## Prerequisites

To get started, download the latest [Microsoft Graph PowerShell SDK](https://learn.microsoft.com/en-us/powershell/microsoftgraph/installation).

## Create a policy and assign it to an app

In the following steps, you'll create a policy that sets the lifetime of the access/ID tokens to 4 hours and assign the policy to an app.

```powershell
Install-Module Microsoft.Graph

Connect-MgGraph -Scopes  "Policy.ReadWrite.ApplicationConfiguration","Policy.Read.All","Application.ReadWrite.All"

# Create a token lifetime policy
$params = @{
  Definition = @('{"TokenLifetimePolicy":{"Version":1,"AccessTokenLifetime":"04:00:00"}}') 
    DisplayName = "WebPolicyScenario"
  IsOrganizationDefault = $false
}
$tokenLifetimePolicyId=(New-MgPolicyTokenLifetimePolicy -BodyParameter $params).Id

# Display the policy
Get-MgPolicyTokenLifetimePolicy -TokenLifetimePolicyId $tokenLifetimePolicyId

# Assign the token lifetime policy to an app
$params = @{
  "@odata.id" = "https://graph.microsoft.com/v1.0/policies/tokenLifetimePolicies/$tokenLifetimePolicyId"
}

$applicationObjectId="aaaaaaaa-0000-1111-2222-bbbbbbbbbbbb"

New-MgApplicationTokenLifetimePolicyByRef -ApplicationId $applicationObjectId -BodyParameter $params

# List the token lifetime policy on the app
Get-MgApplicationTokenLifetimePolicy -ApplicationId $applicationObjectId

# Remove the policy from the app
Remove-MgApplicationTokenLifetimePolicyByRef -ApplicationId $applicationObjectId -TokenLifetimePolicyId $tokenLifetimePolicyId

# Delete the policy
Remove-MgPolicyTokenLifetimePolicy -TokenLifetimePolicyId $tokenLifetimePolicyId
```

## Create a policy and assign it to a service principal

In the following steps, you'll create a policy that sets the lifetime of the access/ID tokens to 8 hours and assign the policy to a service principal.

1. Create a token lifetime policy.

   ```http
   POST https://graph.microsoft.com/v1.0/policies/tokenLifetimePolicies
   Content-Type: application/json
   {
       "definition": [
           "{\"TokenLifetimePolicy\":{\"Version\":1,\"AccessTokenLifetime\":\"08:00:00\"}}"
       ],
       "displayName": "Contoso token lifetime policy",
       "isOrganizationDefault": false
   }
   ```

2. Assign the policy to a service principal.

   ```http
   POST https://graph.microsoft.com/v1.0/servicePrincipals/00001111-aaaa-2222-bbbb-3333cccc4444/tokenLifetimePolicies/$ref
   Content-Type: application/json
   {
     "@odata.id":"https://graph.microsoft.com/v1.0/policies/tokenLifetimePolicies/00aa00aa-bb11-cc22-dd33-44ee44ee44ee"
   }
   ```

3. List the policies on the service principal.

   ```http
   GET https://graph.microsoft.com/v1.0/servicePrincipals/00001111-aaaa-2222-bbbb-3333cccc4444/tokenLifetimePolicies
   ```

4. Remove the policy from the service principal.

   ```http
   DELETE https://graph.microsoft.com/v1.0/servicePrincipals/00001111-aaaa-2222-bbbb-3333cccc4444/tokenLifetimePolicies/00aa00aa-bb11-cc22-dd33-44ee44ee44ee/$ref
   ```

## View existing policies in a tenant

To see all policies that have been created in your organization, run the [Get-MgPolicyTokenLifetimePolicy](https://learn.microsoft.com/en-us/powershell/module/microsoft.graph.identity.signins/get-mgpolicytokenlifetimepolicy) cmdlet. Any results that define refresh or session token properties \(such as `MaxInactiveTime`, `MaxAgeSingleFactor`, `MaxAgeMultiFactor`\) contain legacy settings that are no longer honored. These properties were retired on January 30, 2021. Consider updating or removing these policies to avoid confusion.

1. Run the `Get-MgPolicyTokenLifetimePolicy` to see all policies that have been created in your organization.

   ```powershell
   Get-MgPolicyTokenLifetimePolicy
   ```

2. Run [List appliesTo](https://learn.microsoft.com/en-us/graph/api/tokenlifetimepolicy-list-appliesto) with any of your policy IDs to see which apps are linked to a specific policy that you identified.

   ```powershell
   GET https://graph.microsoft.com/v1.0/policies/tokenLifetimePolicies/4d2f137b-e8a9-46da-a5c3-cc85b2b840a4/appliesTo
   ```

## Next step

[Learn about authentication session management](https://learn.microsoft.com/en-us/entra/identity/conditional-access/howto-conditional-access-session-lifetime)
