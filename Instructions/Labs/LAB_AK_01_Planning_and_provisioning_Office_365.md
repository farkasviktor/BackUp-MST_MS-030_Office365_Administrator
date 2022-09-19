## Lab 1: Planning and Provisioning Office 365

### Exercise 1: Explore the various administrative portals.

During this lab, if asked to save the password or to stay signed in, select **Yes**.

1. On **LON-CL1**, signed in as **ADATUM\Administrator**.

1. Open Edge. Browse to the **Office 365 home page** (**https://portal.office.com**). Sign in using the tenant owner (**admin@LODSXXXXXXX.onmicrosoft.com**).

1. Select the Admin link. This opens the **Microsoft 365 admin center**.

1. Close Edge.

1. Open Edge. Browse to the **Microsoft 365 admin center** directly (**https://admin.microsoft.com**). Sign in using the tenant owner.

1. In the Navigation menu (the left-hand pane), select **…Show all**.

1. In the Navigation menu, select **Users > Active users**.

1. How many users are listed? What licences are assigned to them?

1. In the Navigation menu, select **Exchange**. This opens the **Exchange admin center**.

   You can open this site directly by browsing to **https://outlook.office365.com/ecp**.

1. In the Navigation menu, select **recipients** then select **mailboxes**.

1. How many mailboxes are listed? The number should match the number of active users licensed with Office 365.

1. Select the **Microsoft 365 admin center** browser tab.

1. In the Navigation menu, select **Azure Active Directory**. This opens the **Azure Active Directory admin center**.

   You can open this site directly by browsing to **https://aad.portal.azure.com**.

1. In the navigation menu, select **Azure Active Directory**. In the **Contoso | Overview blade** scroll to the the **Manage** section and select **Users**.

1. How many accounts are listed? The number should match the number of active users.

1. Select the **Microsoft 365 admin center** browser tab.

1. In the Navigation menu, select **Security**. This opens the **Office 365 Security & Compliance** center.

   You can open this site directly by browsing to **https://protection.office.com**.

1. Select the **Microsoft 365 admin center** browser tab.

1. In the Navigation menu, select **Compliance**. This opens the new **Microsoft 365 Compliance** portal.

   You can open this site directly by browsing to **https://compliance.microsoft.com**.

1. Open a new tab and browse to **https://compliance.microsoft.com**. This opens the new **Microsoft 365 Security** portal.

1. Select the **Microsoft 365 admin center** browser tab.

### Exercise 2: Add a DNS domain

1. On **LON-DC1**, signed in as **ADATUM\Administrator**.

1. Open Internet Explorer. Browse to the **Microsoft 365 admin center** and sign in as the tenant owner.

1. In the Navigation menu, select **Settings > Domains**.

1. Select **Add domain**.

1. Type **adatumXXXXXX.onelearndns.com** then select **Use this domain**.

1. Select **Add a TXT record** then **Continue**.

1. Record the **TXT value**.

1. Open **DNS Manager**.

1. Create a new **Forward Lookup Zone**.

   | Setting | Value |
   | --- | --- |
   | Zone type | Primary |
   | Store in Active Directory | Selected |
   | Replicated | To all DNS servers running on domain controllers in this forest |
   | Zone name | adatumXXXXXX.onelearndns.com |
   | Dynamic update | Allow only secure dynamic updates |

1. Right-click **adatumXXXXXX.onelearndns.com**, choose **New host (A or AAAA)…**.

   | Setting | Value |
   | --- | --- |
   | Name | NSadatumXXXXXX | 
   | IP Address | (Your public IP address) |

   *Hint*: Before clicking **Add Host**, copy the fully qualified domain name to the clipboard.
   
1. Right-click the **Start of Authority (SOA)** record, choose **Properties**.

1. Select the **Start of Authority (SOA)** tab. 

1. Type (or paste) **NSadatumXXXXXX.adatumXXXXXX.onelearndns.com** in the Primary Server textbox.

1. Select the **Name Servers** tab then select **Edit**.

1. Type (or paste) **NSadatumXXXXXX.adatumXXXXXX.onelearndns.com** in the server fully qualified domain name textbox and select **Resolve**. Verify that the IP address is correct (your public IP address) and select **OK** twice.

1. Right-click **adatumXXXXXX.onelearndns.com**, choose **Other new records…**, **Text (TXT)**.

   | Setting | Value |
   | --- | --- |
   | Record name | (Leave blank) |
   | Text | (The TXT value from above) |

1. Switch to the **Microsoft 365 admin center** browser.

1. On the **Verify you own this domain** page, select **Verify**.

1. On the **How do you want to connect your domain?** page, select **Close**. *We will add the DNS records later*.

### Admin Center Reference

Add these to the favourites list in Edge on LON-CL1.

- Microsoft 365 admin center - [https://admin.microsoft.com](https://admin.microsoft.com) or [https://portal.office.com/adminportal/home](https://portal.office.com/adminportal/home)

- Microsoft 365 compliance center - [https://compliance.microsoft.com](https://compliance.microsoft.com)

- Microsoft 365 security center - [https://security.microsoft.com](https://security.microsoft.com)

- Office 365 Security & Compliance center - [https://protection.office.com](https://protection.office.com)\
(mostly superseded by the above two)

- Microsoft Endpoint Manager admin center - [https://endpoint.microsoft.com](https://endpoint.microsoft.com)

- Azure Active Directory admin center - [https://aad.portal.azure.com](https://aad.portal.azure.com)

- Exchange admin center - [https://outlook.office365.com/ecp](https://outlook.office365.com/ecp)

- (Preview) Modern Exchange admin center - [https://admin.exchange.microsoft.com](https://admin.exchange.microsoft.com)

- SharePoint admin center - https://\<TenantName\>-admin.sharepoint.com

- Teams admin center - [https://admin.teams.microsoft.com](https://admin.teams.microsoft.com)


See also https://docs.microsoft.com/en-us/microsoft-365/security/mtp/portals?view=o365-worldwide
