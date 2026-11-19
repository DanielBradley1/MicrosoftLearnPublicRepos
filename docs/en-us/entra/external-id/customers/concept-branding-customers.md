<!-- Source: https://learn.microsoft.com/en-us/entra/external-id/customers/concept-branding-customers -->
<!-- Sitemap-Last-Modified: 2026-06-17 -->

# Customize Microsoft Entra External ID authentication branding

After creating an external tenant, you can customize the Microsoft-hosted pages customers use to sign in, sign up, or sign out. The tenant comes with neutral branding that you can tailor to your company's needs. Add a background image or color, favicon, layout, header, and footer, or upload custom CSS. These settings customize the hosted authentication pages, not your application's interface. For more information, see [Customize the neutral branding in your external tenant](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-customize-branding-customers).

**Applies to external tenants:** Feature support varies by authentication approach and API or SDK version. Compare Microsoft-hosted authentication, Embedded native authentication, and Bring Your Own UX \(BYO UX\) in the [authentication approach overview](https://learn.microsoft.com/en-us/entra/external-id/customers/concept-choose-authentication-approach). Check feature availability in the [authentication support matrix](https://learn.microsoft.com/en-us/entra/external-id/customers/concept-supported-features-customers#authentication-approach-supportability).

If the custom company branding fails to load, the sign-in page reverts to the neutral branding.

The following list and image outline the elements of the neutral branding sign-in experience:

1. Background image and color.
2. Favicon.
3. Banner logo.
4. Footer as a page layout element.
5. Footer links, such as **Privacy & cookies** and **Terms of use**, and troubleshooting details available from the ellipsis menu.

   [![Screenshot of a neutral sign-in page with numbered branding elements.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-customize-branding-customers/ciam-neutral-branding.png)](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-customize-branding-customers/ciam-neutral-branding.png#lightbox)

As a comparison, here’s how the [default Microsoft sign-in experience](https://learn.microsoft.com/en-us/entra/fundamentals/how-to-customize-branding) in a Microsoft Entra ID tenant looks:

[![Screenshot of the Microsoft Entra ID default Microsoft branding.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-customize-branding-customers/microsoft-branding.png)](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-customize-branding-customers/microsoft-branding.png#lightbox)

## Preview customization options

The [modern UX and customization overview](https://learn.microsoft.com/en-us/entra/external-id/customization-overview) covers the Fluent experience, Basic and Advanced styling, and custom HTML with optional JavaScript. These new capabilities are configured through application branding themes; this section doesn't extend them to default company branding. Microsoft retains control of authentication fields and actions.

These capabilities are scheduled to become available in preview on December 7, 2026, for external tenants with the preview enabled. The existing company-branding procedures continue to apply to default branding.

## Text customization

You can customize text for built-in attributes, such as Given Name, Surname, City, and Postal Code, on Microsoft-hosted sign-up and sign-in pages. Customize strings under **Company Branding** or through language customization in **User flows**. Both options modify the same JSON file, so the most recent change overrides the previous one.

## Language customization

Customize branding elements for users who sign in with a specific browser language. Elements you don't customize retain their defaults. Add language customizations under **Company Branding** or for a specific user flow under **User flows**. For supported languages and instructions, see [Customize the language of the authentication experience](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-customize-languages-customers).

## Microsoft Graph APIs

You can also manage company branding and configure all assets programmatically.

- For the default branding, use the [organizationalBranding resource type](https://learn.microsoft.com/en-us/graph/api/resources/organizationalbranding) and its associated methods.
- To customize branding based on locale, use the [organizationalBrandingLocalization resource type](https://learn.microsoft.com/en-us/graph/api/resources/organizationalbrandinglocalization) and its associated methods.

## Next steps

- [Customize the user experience for your customers](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-customize-branding-customers)
- [Customize the language of the authentication experience](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-customize-languages-customers)
