<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/places/powershell/turn-off-places -->
<!-- Sitemap-Last-Modified: 2025-01-30 -->

# How to turn off Microsoft Places

Microsoft Places may be automatically available through your Microsoft 365 subscription. However, you may want to disable Places features for specific users, or for your entire organization.

## Turn off Microsoft Places for your entire organization

To turn off Microsoft Places for everyone in your organization, you'll need to turn off Places Core features using tenant settings, then disable the Places Enhanced service plan for all users in your organization.

### Step 1: Turn off core features

Use the Set-PlacesSettings cmdlet as follows:

1. Launch Powershell 7 as an administrator.
2. Ensure you have the most updated Places module by running this cmdlet:

   ```powershell
   Install-Module -Name MicrosoftPlaces -Force
   ```

3. Connect to Microsoft Places.

   ```powershell
   Connect-MicrosoftPlaces 
   ```

4. Disable core features for all user.

   ```powershell
   Set-PlacesSettings -EnablePlacesWebApp 'Default:false'
   Set-PlacesSettings -EnableBuildings 'Default:false' 
   ```

### Step 2: Disable the Places Enhanced service plan

Places Enhanced relies on the **“f8566154-2a62-48cb-a0ab-d4d25be26e51"** service plan. You can disable it in bulk using Microsoft Graph PowerShell scripts.

First, you'll need to install and import the Microsoft Graph module in order to manage licenses using Microsoft Graph.

```powershell
Install-Module Microsoft.Graph -Scope CurrentUser
Import-Module Microsoft.Graph
```

See [Connect to Microsoft 365 with Powershell](https://learn.microsoft.com/en-us/microsoft-365/enterprise/connect-to-microsoft-365-powershell) to find more information on installing and connecting to Microsoft Graph.

Then, follow these steps to disable the service plan:

1. Connect to Microsoft Graph using the User.ReadWrite.All scope.

   ```powershell
   Connect-Graph -Scopes "User.ReadWrite.All", "Application.Read.All"
   ```

2. Get all of the users.

   ```powershell
   $users = Get-MgUser -All
   ```

3. Get the skuId for which Places\_Enhanced is part of.

   ```powershell
   $skuId = (Get-MgUserLicenseDetail -UserId <userId that has Places_Enhanced> | Where-Object {$_.ServicePlans.ServicePlanName -contains "PLACES_ENHANCED" }).SkuId
   ```

4. Define the service plan ID for the plan you wish to disable.

   ```powershell
   $newDisablePlans= @(“f8566154-2a62-48cb-a0ab-d4d25be26e51")
   ```

5. Disable the plans for each user by running the script below:

   ```powershell
   foreach ($user in $users) { 

       $userUPN = $user.UserPrincipalName 
       if ($userUPN -ne "") { 
               $userLicense = Get-MgUserLicenseDetail -UserId $userUPN 
               $disabledPlans = $userLicense.ServicePlans | Where-Object { $_.ProvisioningStatus -eq "Disabled" } | Select-Object -ExpandProperty ServicePlanId 
               $allDisabledPlans = $disabledPlans + $newDisablePlans | Sort-Object -Unique 
               $addLicenses = @(@{ 
                   SkuId         = $skuId 
                   DisabledPlans = $allDisabledPlans  
               }) 

               Set-MgUserLicense -UserId $userUPN -AddLicenses $addLicenses -RemoveLicenses @() 

           }  
   } 
   ```

Note

The Places Enhanced service plan is automatically added when you assign Teams Premium to a user. You'll need to run through these steps again to disable the service plan, each time you assign new Teams Premium licenses to users in your organization.

## Turning off Microsoft Places for specific users

To turn off Microsoft Places for specific users in your organization, you'll turn off Places Core features, then disable the Places Enhanced service plan for these users.

Important

If you plan to use a standard security group, your configuration may not work as expected. To ensure proper functionality, the security group must be set as a mail-enabled security group.

### Step 1: Turn off core features for specific users

Follow the instructions in [Set-PlacesSettings](https://learn.microsoft.com/en-us/microsoft-365/places/powershell/set-placessettings) to turn off **EnablePlacesWebApp** and **EnableBuildings** for specific users.

### Step 2: Remove the Places Enhanced service plan from specific users

First, create a txt file \(e.g. “users.txt”\) with the UPN of users you're targeting. Format the txt file so you have one UPN per line. Then, launch PowerShell as an administrator, and run through the following steps:

1. Connect to Microsoft Graph with user read write scope:

   ```powershell
   Connect-Graph -Scopes User.ReadWrite.All
   ```

2. Set the file path to your txt file you created in Step 1.

   ```powershell
   $users = “<path_to_your_file>”
   ```

3. Get the skuID for which Places\_Enhanced is part of:

   ```powershell
   $skuId = (Get-MgUserLicenseDetail -UserId <UserId that has Places_Enhanced> | Where-Object { $_.ServicePlans.ServicePlanName -contains "PLACES_ENHANCED" }).SkuId
   ```

4. Define the service plan ID for the plan you wish to disable.

   ```powershell
   $newDisablePlans= @(“f8566154-2a62-48cb-a0ab-d4d25be26e51")
   ```

5. Disable the plans for each user by running the following script:

   ```powershell
   Get-Content -Path $users| ForEach-Object {  

       $userUPN = $_.Trim() 
       if ($userUPN -ne "") { 
               $userLicense = Get-MgUserLicenseDetail -UserId $userUPN 
               $disabledPlans = $userLicense.ServicePlans | Where-Object { $_.ProvisioningStatus -eq "Disabled" } | Select-Object -ExpandProperty ServicePlanId 
               $allDisabledPlans = $disabledPlans + $newDisablePlans | Sort-Object -Unique 
               $addLicenses = @(@{ 
                   SkuId         = $skuId 
                   DisabledPlans = $allDisabledPlans  
               }) 

               Set-MgUserLicense -UserId $userUPN -AddLicenses $addLicenses -RemoveLicenses @() 

           }  
   }
   ```

If you only have a few users you would like to remove the service plan from, you can also disable the Places Enhanced service plan via the Microsoft 365 admin center.

1. Navigate to the Microsoft 365 admin center.
2. Select **Active users** under the **Users** tab.
3. Click on the user you wish to disable Places for.
4. Go to **Licenses and apps** and expand the **Apps** section.
5. Look for the **Places Enhanced** service plan and uncheck it.
6. Save changes and repeat for other users.

Note

You may find another service plan called “Places Core.” This service plan is deprecated and can be ignored.

## Troubleshooting

If you see errors connecting to Microsoft Graph, see [Connect to Microsoft 365 with Powershell](https://learn.microsoft.com/en-us/microsoft-365/enterprise/connect-to-microsoft-365-powershell) to find more information on installing and connecting to Microsoft Graph.

If you see a 403, Authorization Request Denied error while running the Graph commands, double check that you have connected to Graph using the necessary scopes. You can see which permission scope you need for each Graph command using the [Find-MgGraphCommand](https://learn.microsoft.com/en-us/powershell/microsoftgraph/find-mg-graph-command).
