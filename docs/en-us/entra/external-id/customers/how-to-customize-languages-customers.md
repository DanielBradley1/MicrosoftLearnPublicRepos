<!-- Source: https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-customize-languages-customers -->
<!-- Sitemap-Last-Modified: 2026-04-24 -->

# Customize browser language for authentication experience

**Applies to**: ![Green circle with a white check mark symbol that indicates the following content applies to external tenants.](https://learn.microsoft.com/en-us/entra/external-id/media/common/applies-to-yes.png) External tenants \([learn more](https://learn.microsoft.com/en-us/entra/external-id/tenant-configurations)\)

Tip

This article applies to user flows in external tenants. For information about workforce tenants, see [Language customization in Microsoft Entra External ID](https://learn.microsoft.com/en-us/entra/external-id/user-flow-customize-language).

This article explains how to customize the browser language for your app's authentication experience. By personalizing the sign-in process based on browser language, you can deliver a tailored experience for your users and override default branding settings.

## Prerequisites

- If you haven't already created your own Microsoft Entra external tenant, create one now.
- [Register an application](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-register-app).
- [Create a user flow](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-user-flow-sign-up-sign-in-customers).
- Review the file size requirements for each image you want to add. You might need to use a photo editor to create the right-sized images. The preferred image type for all images is PNG, but JPG is accepted.

## Add browser language under Company branding

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least an [Organizational Branding Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#organizational-branding-administrator).
2. If you have access to multiple tenants, use the **Settings** icon ![](https://learn.microsoft.com/en-us/entra/external-id/customers/media/common/admin-center-settings-icon.png) in the top menu to switch to the external tenant you created earlier from the **Directories + subscriptions** menu.
3. Browse to **Company branding** > **Browser language customizations** > **Add browser language**.

   [![Screenshot of Company branding with Browser language customizations and the Add browser language action.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-customize-languages-customers/company-branding-add-browser-language.png)](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-customize-languages-customers/company-branding-add-browser-language.png#lightbox)
4. On the **Basics** tab, under **Language specific UI Customization**, select the browser language you want to customize from the menu.

   [![Screenshot of the language selector on the Basics tab for browser language customization.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-customize-languages-customers/language-selection.png)](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-customize-languages-customers/language-selection.png#lightbox)

The following languages are supported in the external tenant:

- Arabic \(Saudi Arabia\)
- Basque \(Basque\)
- Bulgarian \(Bulgaria\)
- Catalan \(Catalan\)
- Chinese \(China\)
- Chinese \(Hong Kong SAR\)
- Croatian \(Croatia\)
- Czech \(Czechia\)
- Danish \(Denmark\)
- Dutch \(Netherlands\)
- English \(United States\)
- Estonian \(Estonia\)
- Finnish \(Finland\)
- French \(France\)
- Galician \(Galician\)
- German \(Germany\)
- Greek \(Greece\)
- Hebrew \(Israel\)
- Hungarian \(Hungary\)
- Italian \(Italy\)
- Japanese \(Japan\)
- Kazakh \(Kazakhstan\)
- Korean \(Korea\)
- Latvian \(Latvia\)
- Lithuanian \(Lithuania\)
- Norwegian Bokmål \(Norway\)
- Polish \(Poland\)
- Portuguese \(Brazil\)
- Portuguese \(Portugal\)
- Romanian \(Romania\)
- Russian \(Russia\)
- Serbian \(Latin, Serbia\)
- Slovak \(Slovakia\)
- Slovenian \(Slovenia\)
- Spanish \(Spain\)
- Swedish \(Sweden\)
- Thai \(Thailand\)
- Turkish \(Türkiye\)
- Ukrainian \(Ukraine\)

1. Customize the elements on the **Basics**, **Layout**, **Header**, **Footer**, **Sign-in form**, and **Text** tabs. For detailed instructions, see [Customize the branding and end-user experience](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-customize-branding-customers).
2. When you're finished, select the **Review** tab and go over all your language customizations. Then select **Add** to save your changes, or **Previous** to continue editing.

## Add language customization to a user flow

Language customization in the external tenant lets your user flow accommodate different languages to suit your customer's needs. You can use languages to modify the strings displayed to your customers as part of the attribute collection process during sign-up.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least an [Organizational Branding Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#organizational-branding-administrator).
2. If you have access to multiple tenants, use the **Settings** icon ![](https://learn.microsoft.com/en-us/entra/external-id/customers/media/common/admin-center-settings-icon.png) in the top menu to switch to the external tenant you created earlier from the **Directories + subscriptions** menu.
3. Browse to **Entra ID** > **External Identities** > **User flows**.
4. Select the user flow that you want to enable for translations.
5. Select **Languages**.
6. On the **Languages** page for the user flow, select the language that you want to customize.
7. Expand **Sign up and sign in**.
8. Select **Download defaults** \(or **Download overrides** if you have previously edited this language\).

   [![Screenshot that shows how to add languages under a user flow.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-customize-languages-customers/language-customization-flow.png)](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-customize-languages-customers/language-customization-flow.png#lightbox)

The downloaded file is in JSON format and includes both built-in and custom attributes, as well as other page-level and error strings:

```http
{
	"AttributeCollection_Description": "Wir benötigen nur ein paar weitere Informationen, um Ihr Konto einzurichten.",
	"AttributeCollection_Title": "Details hinzufügen",
	"Attribute_City": "Ort",
	"Attribute_Country": "Land/Region",
	"Attribute_DisplayName": "Anzeigename",
	"Attribute_Email": "E-Mail-Adresse",
	"Attribute_Generic_ConfirmationLabel": "{0} erneut eingeben",
	"Attribute_GivenName": "Vorname",
	"Attribute_JobTitle": "Position",
	"Attribute_Password": "Kennwort",
	"Attribute_Password_MismatchErrorString": "Kennwörter stimmen nicht überein.",
	"Attribute_PostalCode": "Postleitzahl",
	"Attribute_State": "Bundesland/Kanton",
	"Attribute_StreetAddress": "Straße",
	"Attribute_Surname": "Nachname",
	"SignIn_Description": "Melden Sie sich an, um auf {0} zuzugreifen.",
	"SignIn_Title": "Anmelden",
	"SignUp_Description": "Registrieren Sie sich, um auf {0} zuzugreifen.",
	"SignUp_Title": "Konto erstellen",
	"SisuOtc_Title": "Code eingeben",
	"Attribute_extension_a235ca9a0a7c4d33bd69e07bed81c8b1_Shoesize": "Shoe size"
}  
```

You can modify any or all of these attributes in the downloaded file. For example, you can modify the built-in attribute, **City** and the custom attribute, **Shoesize**:

```http
{
	"AttributeCollection_Description": "Wir benötigen nur ein paar weitere Informationen, um Ihr Konto einzurichten.",
	"AttributeCollection_Title": "Details hinzufügen",
	"Attribute_City": "Ort2",
	"Attribute_Country": "Land/Region",
	"Attribute_DisplayName": "Anzeigename",
	"Attribute_Email": "E-Mail-Adresse",
	"Attribute_Generic_ConfirmationLabel": "{0} erneut eingeben",
	"Attribute_GivenName": "Vorname",
	"Attribute_JobTitle": "Position",
	"Attribute_Password": "Kennwort",
	"Attribute_Password_MismatchErrorString": "Kennwörter stimmen nicht überein.",
	"Attribute_PostalCode": "Postleitzahl",
	"Attribute_State": "Bundesland/Kanton",
	"Attribute_StreetAddress": "Straße",
	"Attribute_Surname": "Nachname",
	"SignIn_Description": "Melden Sie sich an, um auf {0} zuzugreifen.",
	"SignIn_Title": "Anmelden",
	"SignUp_Description": "Registrieren Sie sich, um auf {0} zuzugreifen.",
	"SignUp_Title": "Konto erstellen",
	"SisuOtc_Title": "Code eingeben",
	"Attribute_extension_a235ca9a0a7c4d33bd69e07bed81c8b1_Shoesize": "Schuhgröße"
}  
```

9. After making the necessary changes, you can upload the new overrides file. The changes are saved to your user flow automatically. The override appears under the **Configured** tab.
10. To double-check your changes, select the language under the **Configured** tab and expand the **Sign up and sign in** option. You can view your customized language file by selecting **Download overrides**. To remove your customized override file, select **Remove overrides**.

[![Screenshot that shows how to remove or download the modified JSON file.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-customize-languages-customers/remove-download-override-file.png)](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-customize-languages-customers/remove-download-override-file.png#lightbox)

11. Go to the sign-in page of your external tenant. Make sure you have the right locale and market in your URLs, for example: `ui_locales=de-DE` and `mkt=de-DE`. The updated attributes on the sign-up page appear as follows:

![Screenshot of the modified sign-up page attributes.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-customize-languages-customers/customized-attributes.png)

Important

In the external tenant, we have two options to add custom text to the sign-up and sign-in experience. The function is available under each user flow during language customization and under [Company Branding](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-customize-branding-customers). Although we have two ways to customize strings \(via Company branding and via User flows\), both ways modify the same JSON file. The most recent change made either via User flows or via Company branding always overrides the previous one.

## Right-to-left language support

Languages that are read right-to-left, such as Arabic and Hebrew, are displayed in the opposite direction compared to languages that are read left-to-right. The external tenant supports right-to-left functionality and features for languages that work in a right-to-left environment for entering, and displaying data. Right-to-left readers can interact in a natural reading manner.

[![Screenshot showing the right-to-left language support.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-customize-languages-customers/right-to-left-language-support.png)](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-customize-languages-customers/right-to-left-language-support.png#lightbox)

## Remove the browser language customization

When no longer needed, you can remove the language customization from your external tenant in the admin center or with the Microsoft Graph API.

### Remove the language customization in the admin center

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com).
2. Browse to **Company branding** > **Browser language customizations**
3. Select the language you want to delete and then select **Delete** and **OK**.

   [![Screenshot of the browser language customizations tab and the delete button.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-customize-languages-customers/company-branding-delete-browser-language.png)](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-customize-languages-customers/company-branding-delete-browser-language.png#lightbox)

### Remove the language customization with the Microsoft Graph API

1. Sign in to the [MS Graph explorer](https://developer.microsoft.com/en-us/graph/graph-explorer) with your external tenant account: `https://developer.microsoft.com/en-us/graph/graph-explorer?tenant=<your-tenant-name.onmicrosoft.com>`.
2. Query the default branding object using the Microsoft Graph API: `https://graph.microsoft.com/v1.0/organization/<your-tenant-ID>/branding/localizations`. To confirm that you're signed in to your external tenant, verify the tenant name on the right side of the screen.
3. [Remove the localized branding object](https://learn.microsoft.com/en-us/graph/api/organizationalbrandinglocalization-delete).

   [![Screenshot of MS Graph API with CIAM tenant logged in.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-customize-branding-customers/msgraph-ciam-branding.png)](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-customize-branding-customers/msgraph-ciam-branding.png#lightbox)
4. Wait a few minutes for the changes to take effect.

## Next steps

- [Customize the branding and end-user experience](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-customize-branding-customers)
