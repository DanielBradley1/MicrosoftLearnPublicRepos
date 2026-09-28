<!-- Source: https://learn.microsoft.com/en-us/entra/external-id/customers/concept-branding-customers -->
<!-- Sitemap-Last-Modified: 2026-06-17 -->

# Customize the look and feel of the authentication experience for the external tenant

Note

The branding customizations described in this article apply to **browser-delegated authentication**, where users sign in through a Microsoft-hosted sign-in page. If you use [native authentication](https://learn.microsoft.com/en-us/entra/external-id/customers/concept-choose-authentication-approach), you build and control the sign-in UI directly in your app, so branding is managed in your application code.

After creating a new external tenant, you can customize the appearance of your web-based applications for customers who sign in, sign up, or sign out to personalize their end-user experience. The external tenant comes with a default neutral branding that doesn’t include any existing Microsoft branding. However, this neutral default branding can be customized to meet your company’s specific needs. You have the flexibility to add a custom background image or color, favicon, layout, header, and footer to your authentication experience. You can add each custom branding property individually to the custom sign-in page, or you can upload a custom CSS. For more information, see [Customize the neutral branding in your external tenant](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-customize-branding-customers).

If the custom company branding fails to load, the sign-in page reverts to the neutral branding.

The following list and image outline the elements of the neutral branding sign-in experience:

1. Background image and color.
2. Favicon.
3. Banner logo.
4. Footer as a page layout element.
5. Footer hyperlinks, for example, Privacy & cookies, Terms of use and troubleshooting details also known as ellipsis in the right bottom corner of the screen.

   [![Screenshot of the neutral branding.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-customize-branding-customers/ciam-neutral-branding.png)](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-customize-branding-customers/ciam-neutral-branding.png#lightbox)

As a comparison, here’s how the [default Microsoft sign-in experience](https://learn.microsoft.com/en-us/entra/fundamentals/how-to-customize-branding) in a Microsoft Entra ID tenant looks:

[![Screenshot of the Microsoft Entra ID default Microsoft branding.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-customize-branding-customers/microsoft-branding.png)](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-customize-branding-customers/microsoft-branding.png#lightbox)

## Text customization

You might have different requirements for the information you want to collect during sign-up and sign-in. The external tenant comes with a built-in set of information stored in attributes, such as Given Name, Surname, City, and Postal Code. In the external tenant, we have two options to add custom text to the sign-up and sign-in experience. The function is available under each user flow during language customization and also under **Company Branding**. Although we have two ways to customize strings, both ways modify the same JSON file. The most recent change made either via **User flows** or via **Company Branding** will always override the previous one.

## Language customization

You can create a personalized sign-in experience for users who sign in using a specific browser language by customizing the branding elements. If you don't make any changes to the elements, the default elements will be displayed. In the tenant, you can add a custom language to the sign-in experience under **Company Branding** or to a specific user flow under **User flows**. The language customization is available for a list of languages. For more information, see [Customize the language of the authentication experience](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-customize-languages-customers).

## Microsoft Graph APIs

You can also manage company branding and configure all assets programmatically.

- For the default branding, use the [organizationalBranding resource type](https://learn.microsoft.com/en-us/graph/api/resources/organizationalbranding) and its associated methods.
- To customize branding based on locale, using the [organizationalBrandingLocalization resource type](https://learn.microsoft.com/en-us/graph/api/resources/organizationalbrandinglocalization) resource type and its associated methods.

## Next steps

- [Customize the user experience for your customers](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-customize-branding-customers)
- [Customize the language of the authentication experience](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-customize-languages-customers)
