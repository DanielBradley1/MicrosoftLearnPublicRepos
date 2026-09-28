<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/commerce/subscriptions/self-service-purchase-faq?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-08-24 -->

# Self-service purchase FAQ

Self-service purchase gives users a chance to try out new technologies and develop solutions that ultimately benefit their larger organizations. Central procurement and IT teams have visibility to all users who buy and deploy self-service purchase solutions through the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339). Admins can turn off self-service purchasing on a per product basis via PowerShell. To learn more, see [Use AllowSelfServicePurchase for the MSCommerce PowerShell module](https://learn.microsoft.com/en-us/microsoft-365/commerce/subscriptions/allowselfservicepurchase-powershell?view=o365-worldwide).

Self-service purchase is available for Power Platform \(Power BI, Power Apps, and Power Automate\), Project, and Visio.

Note

Self-service purchase isn't available in India or for government or education customers. Project and Visio aren't available for self-service purchase in Brazil and the Democratic Republic of Congo.

Important

Self-service purchases and trials can't be completely turned off at the tenant level with a single command. The [AllowSelfServicePurchase](https://learn.microsoft.com/en-us/microsoft-365/commerce/subscriptions/allowselfservicepurchase-powershell?view=o365-worldwide) policy is managed on a per-product basis. You can only turn off self-services purchases and trials for the entire tenant by turning off each product individually. By default, all new products are set to allow users to make a self-service purchase.

## Making a self-service purchase

### How does a customer make a self-service purchase?

Customers can make a self-service purchase online from the product websites or from in-app purchase prompts. Customers are first asked to enter an email address to ensure that they're a user in an existing Microsoft Entra tenant. Next, they're directed to sign in by using their Microsoft Entra credentials. After the customer signs in, they're asked to select how many subscriptions they want to buy, and to provide credit card payment. After the purchase is complete, they can start using their subscription. The purchaser has access to a limited view of the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339) where they can assign licenses to the product to other people in their organization.

### What are the payment options for self-service purchases?

Currently, credit card is the only available payment method. Payment through invoicing isn't supported.

### Who can buy through self-service purchase?

Any user with a nonguest user account in a managed Microsoft Entra tenant can make a self-service purchase. Self-service purchasing isn't available to tenants that are government or education organizations. If this applies to your organization, then no other action is required to control self-service purchase.

Users in organizations or markets who aren't eligible for self-service purchase see a message asking them to contact their IT admin.

### Can guest users buy through self-service purchase?

No, guest users can't complete a self-service purchase in a tenant in which they're a guest.

### Can users synced from an on-premises Active Directory buy through self-service purchase?

If a user has an active user account in an eligible Microsoft Entra tenant, they can complete a self-service purchase.

### Who can self-service purchasers assign licenses to?

Self-service purchasers can only assign licenses to users in the same Microsoft Entra tenant. The purchaser has access to a limited view of the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339) to assign licenses. Purchasers can assign licenses to those products that they bought through self-service purchase, and can only assign those licenses to users in the same Microsoft Entra tenant.

### Where does the self-service purchaser see and manage their purchases?

Self-service purchasers can manage their purchases in the limited view of the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339). Purchasers can always get to the admin center from the **Admin** tile in the app launcher built into all Microsoft 365 and Dynamics online apps. Purchasers can view the purchases they made, buy more subscriptions to the same service, and assign licenses for those subscriptions to other users in their organization. Additionally, purchasers can view and pay their bill, update their payment method, and cancel their subscription.

### Can users start a self-service trial, such as a Microsoft Teams Premium trial?

Yes. Eligible users can start a self-service trial, including a Microsoft Teams Premium trial, from in-app prompts. Self-service trials are enabled by default. To prevent users from starting trials for a product, a Global Administrator can set that product to **Do not allow** under **Settings** > **Org settings** > **Services** > **Self-service trials and purchases** in the Microsoft 365 admin center, or with the MSCommerce PowerShell module. It can take up to 72 hours for the change to take effect. For more information, see [Manage self-service purchases and trials \(for admins\)](https://learn.microsoft.com/en-us/microsoft-365/commerce/subscriptions/manage-self-service-purchases-admins?view=o365-worldwide).

## Pricing

### What is the pricing for self-service purchases?

Pricing for each of the products for self-service purchase is available on the Microsoft website. Prices are also displayed as part of the checkout experience when users make a self-service purchase. These prices might differ from the prices an organization pays when making central purchases or prices offered through a partner.

### Who is responsible for payment?

The person who buys the subscription through self-service purchase is the person who is billed and who is responsible for payment based on the terms and pricing of the purchase.

## Admin capabilities

### What capabilities does an admin have for self-service purchases?

Admins can view all self-service purchases made in their organization in the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339). They can see the product, purchaser name, subscriptions purchased, expiry date, order history, purchase price, and assigned users for each self-service purchase. In the Power Platform Admin Center, admins can also view self-service purchases capacity. If required by their organization, admins can turn off self-service purchasing on a per product basis via PowerShell. Admins have the same data management and access policies over products bought through self-service purchase or centrally.

Admins can also control whether users in their organization can make self-service purchases. For more information, see [Use AllowSelfServicePurchase for the MSCommerce PowerShell module](https://learn.microsoft.com/en-us/microsoft-365/commerce/subscriptions/allowselfservicepurchase-powershell?view=o365-worldwide).

### How is Microsoft respecting data governance and compliance by enabling self-service purchase?

Admins maintain control over what services and products are available within their tenant based on their data governance and compliance requirements. All data management and access policies that your organization turned on apply to available self-service purchased services.

### Who owns the product data created from self-service purchases?

Data created from products bought through self-service purchase is owned and controlled by the organization.

### How do I centralize the purchases made through self-service purchase?

Admins can assign existing licenses or buy more subscriptions of self-service purchase products through existing agreements and pricing for users assigned to self-service purchases. After an admin assigns these centrally purchased licenses, they can request that the purchasers cancel their existing subscriptions.

### Where does the admin see self-service purchases?

Global and billing admins can see subscriptions bought through self-service purchase in **Billing** > **Your products** in the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339). They can filter the products list to only show the subscriptions purchased through central procurement, or to include subscriptions bought through self-service purchase. Admins can see the product, purchaser name, subscription purchased, expiry date, order history, the purchase price, and assigned users. Self-service trials appear under **Billing** > **Your products** on the **Self-service trials** tab. If an expected trial doesn't appear, confirm the tenant is eligible \(trials aren't available to government or education tenants, or in some regions\) and that the product's self-service setting allows trials.

Important

Microsoft recommends that you use roles with the fewest permissions. Using lower permissioned accounts helps improve security for your organization. Global Administrator is a highly privileged role that should be limited to emergency scenarios when you can't use an existing role. To learn more, see [About administrator roles in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/add-users/about-admin-roles?view=o365-worldwide).

### Why do users still see a "Get Premium" prompt after I disable self-service trials?

Disabling self-service for a product blocks trial and purchase activation, but it doesn't necessarily remove in-product upgrade prompts. These prompts surface user interest to admins; they don't start a trial when self-service is turned off. To set what users can do, a Global Administrator goes to **Settings** > **Org settings** > **Services** > **Self-service trials and purchases** in the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339) and selects **Allow**, **Allow for trials only**, or **Do not allow** for the product. For more information, see [Manage self-service purchases and trials \(for admins\)](https://learn.microsoft.com/en-us/microsoft-365/commerce/subscriptions/manage-self-service-purchases-admins?view=o365-worldwide).

## Support and training

### Are customers' IT departments or partners expected to support products bought through self-service purchase?

IT departments and partners aren't expected to provide support for products bought through self-service purchase. Microsoft provides standard support for self-service purchasers.

### If a self-service purchaser calls support, does that use the customer's Premier Support incidents?

Self-service purchasers don't use a customer's Premier Support incidents for receiving support for their self-service purchases.

### How are users expected to receive training on the products they buy through self-service purchase?

Extensive training for users is provided on the product websites. The products have guided learning, documentation, samples, and strong communities to get answers and tips directly from other users.

### What happens to a self-service purchase if a user leaves the organization?

If the person who originally bought the self-service purchase product leaves the organization, valid users continue to have full use of the product during the subscription term. The subscription remains active until the purchaser directly cancels it or an admin requests cancellation of the subscription through customer support. Admins can also choose to assign a centrally purchased license to users of the canceled subscription.

## Partners

### Can I disable self-service purchase for all my customers?

Yes. However, there's no single command to turn off all self-service purchases at the tenant level. Self-service purchases and trials can only be disabled on a per-product basis on one customer tenant at a time. For more information, see [Allow or block self-service purchases and trials](https://learn.microsoft.com/en-us/microsoft-365/commerce/subscriptions/manage-self-service-purchases-admins?view=o365-worldwide#allow-or-block-self-service-purchases-and-trials).

### What's the role of Microsoft's partners in self-service purchases?

Partners who have delegated administration privileges can see self-service purchases in the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339), just like an admin. Partners can help support an organization that wants to centralize products bought through self-service purchases. Additionally, partners can offer solutions to extend the capabilities of a self-service purchase.

### What role does a partner need to manage self-service purchases?

Partners who are Admins On Behalf Of \(AOBO\) a customer must have a role that's set to Global Administrator to manage and disable self-service purchases in the Microsoft 365 admin center and via PowerShell. Other roles are restricted from managing and disabling self-service purchases.

### What obligations does a partner have around self-service purchases, billing, and support?

None. Customers are responsible for all payments and billing for any self-service purchases that they make.
