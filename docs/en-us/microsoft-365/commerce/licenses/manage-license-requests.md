<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/commerce/licenses/manage-license-requests?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-06-17 -->

# Manage self-service license requests in the Microsoft 365 admin center

Note

The information in this article only applies to self-service purchased products and services. To learn more, see [Self-service purchase FAQ](https://learn.microsoft.com/en-us/microsoft-365/commerce/subscriptions/self-service-purchase-faq?view=o365-worldwide).

If you turn off self-service purchases in your organization, you can set up a self-service license request process to control how users request licenses for blocked products. This article explains how to:

- Approve or deny license requests
- Use your own request process
- Share a license request with someone else in your organization

When a user tries to make a self-service purchase for a product that you blocked, they can submit a request for a license to you, the admin. When they make a request, they can add the names of other users who also need licenses for the product.

Note

If you block users from making self-service purchases, Microsoft doesn't send them marketing emails. Also, if they're using a trial version of a product, they don't see recommendations to buy it. To learn more, see [Manage self-service purchases \(Admin\)](https://learn.microsoft.com/en-us/microsoft-365/commerce/subscriptions/manage-self-service-purchases-admins?view=o365-worldwide).

To see and manage license requests, use the **Requests** tab on the **Licensing** page in the admin center. The list shows the name of the product requested, name of the person requesting a license, date requested, and status of the request. You can filter the list to show requests that are pending or completed. Requests are held for 12 months.

## Before you begin

- You must be at least a User Administrator or a License Administrator to complete the tasks in this article. For more information, see [About admin roles](https://learn.microsoft.com/en-us/microsoft-365/admin/add-users/about-admin-roles?view=o365-worldwide).
- If you're a partner who's an Admin On Behalf Of \(AOBO\) a customer, you must have a role that's set to Global Administrator to complete the tasks in this article.

Caution

Global Administrators have almost unlimited access to your organization's settings and most of its data. To help keep your organization secure, we recommend that you limit the number of Global Administrators as much as possible.

## Use your own license request process

If your organization has its own request process, you can use it instead. Create a policy with instructions to display to users when they request a license.

Important

If you use your own request process, the **Requests** tab doesn't display any requests. Existing requests from before you added your message continue to appear until you approve or decline them.

1. In the Microsoft 365 admin center, select the **Navigation menu**, and then select **Billing** > [Licenses](https://go.microsoft.com/fwlink/p/?linkid=842264).
2. On the **Licenses** page, select the **Requests** tab.
3. Select **Connect your request process**.
4. In the **Use your request process** pane, select the **Use my organization's request process** check box.
5. In the **Message** box, type the message you want users to see when they request a license. If you want to also include a link to your organization's policy or other documentation, enter the URL in the **Link to documentation \(optional\)** text box.
6. Select **Save**.

When you return to the **Requests** list, you see the message **You're using your own license request process**. To make changes to the message that is displayed to users, select **Use your existing request process instead**.

## Stop using your own license request process

1. In the admin center, select the **Navigation menu**, and then select **Billing** > [Licenses](https://go.microsoft.com/fwlink/p/?linkid=842264).
2. On the **Licenses** page, select the **Requests** tab.
3. Select **Connect your request process**.
4. In the **Use your request process** pane, clear the **Use my organization's request process** check box.
5. Select **Save**.

## Approve or deny a self-service license request

1. In the admin center, select the **Navigation menu**, and then select **Billing** > [Licenses](https://go.microsoft.com/fwlink/p/?linkid=842264).
2. On the **Licenses** page, select the **Requests** tab.
3. Select the row that contains the request you want to review. The details pane shows details about which users want licenses for the product.
4. Assign licenses to each user through the default **Approve the selected license requests** option. Choose one of the following actions:
   | What you want to do | Steps |
   | --- | --- |
   | Approve all users | Select all checkboxes, then select **Approve**. |
   | Approve some users, deny others | Select only the checkboxes for users to approve, then select **Approve x - Reject y**. Unselected users are automatically rejected. |
   | Deny all users | Clear all checkboxes, then select **Reject**. |
5. If you have more than one product, under **Select a product**, select the one that you want to use to assign licenses for.

   - To deny users access to certain apps and services, expand **Turn apps and services on or off**, and then clear the check boxes for the ones that you want to exclude.

6. To assign licenses based on group membership, select **Assign license by adding people to the following security group**.

   - A grayed-out option typically signifies that the security groups are either unlicensed or not yet configured.
   - For more information about how to assign licenses to a security group, see [Assign or unassign licenses to a group using the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/manage-group-licenses?view=o365-worldwide).
   - When multiple security groups are available, select the one to which you want to assign licenses.

7. When you're finished, select **Submit**. The details pane shows the details of the request.
8. Close the details pane. Users receive an email that says their request was approved or denied.

## Share a self-service license request by email

If you don't have the authority within your organization to make decisions about who can receive a license for a particular product or service, you can share a license request via email with someone in your organization who does. You can only share one request at a time. The person who receives the license request email doesn't need access to the Microsoft 365 admin center to review the request. They just respond to the email and indicate whether the person should be given the license they requested, and then you [Approve or deny a self-service license request](#approve-or-deny-a-self-service-license-request).

1. In the admin center, select the **Navigation menu**, and then select **Billing** > **Licenses**.
2. On the **Licenses** page, select the **Requests** tab.
3. Select the **Share request** tab, and then select a request to share.
4. In the request pane, select **Share request**.
5. In the **Share license request details** pane, type an email address, and then select the recipient name.

   Note

   You can select more than one recipient, but if the email that you entered doesn't resolve into a user name, you can't share the request.
6. To personalize the email, select the **Include a personalized message** check box, and then type a **Message**.
7. When you're finished, select **Share request**.

## Related content

[Assign licenses to users](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/assign-licenses-to-users?view=o365-worldwide) \(article\)  
[Move users to a different subscription](https://learn.microsoft.com/en-us/microsoft-365/commerce/subscriptions/move-users-different-subscription?view=o365-worldwide) \(article\)  
[Buy or remove subscription licenses](https://learn.microsoft.com/en-us/microsoft-365/commerce/licenses/buy-licenses?view=o365-worldwide) \(article\)  
[Self-service purchase FAQ](https://learn.microsoft.com/en-us/microsoft-365/commerce/subscriptions/self-service-purchase-faq?view=o365-worldwide) \(article\)
