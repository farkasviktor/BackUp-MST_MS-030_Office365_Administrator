## Lab 9: Configuring SharePoint Online

### Exercise 1: Configure SharePoint Online settings

#### Task 1: Configure settings

1. Open Edge. Browse to the **SharePoint admin center** and sign in as the tenant owner.

1. Select **Settings** then **Site storage limits**

1. Verify that Site storage limits is set to **Automatic**.

1. In the **SharePoint admin center**, select **Policies > Sharing**. 

   Verify that both SharePoint and OneDrive are set to **Most permissive**.

#### Task 2: Configure user profiles

1. In the **SharePoint admin center**, select **More features**. In the centre pane, under **User profiles** select **Open**.

1. Select **Manage user profiles**.

1. Enter **Ada**, select **Find**. 

1. Edit Ada’s profile. Set the **Manager** to **MOD Administrator**.

1. Close the browser tab and select **Open** again. *This is because many SharePoint admin pages have no breadcrumb trail.*

1. Select **Setup My Sites**.

1. Under **My Site Cleanup**, set the **Secondary owner** to **MOD Administrator**. Select **OK** (bottom-right).

1. Close the browser tab. 

#### Task 3: Configure apps

1. In the **SharePoint admin center**, select **More features**. In the centre pane, under **Apps** select **Open**.

1. Select **Configure Store settings**. Set **Should Apps for Office from the store be able to start when documents are opened in the browser?** to **No**.

### Exercise 2: Create and configure SharePoint Online site collections

#### Task 1: Create a site collection using the portal

1. In the **SharePoint admin center**, select **Sites > Active Sites**, then select **+ Create**.

1. Create a new **Team site**.

   | Setting | Value |
   | --- | --- |
   | Site name, email address, address | Marketing |
   | Group owner | MOD Administrator |
   | Language | English |
   | Privacy settings | Private |
   | Time zone | Pacific Time (US and Canada) |
   | Site description | Marketing department |
   | Addition owners | (None) |
   | Members | (None) |

1. In the Active sites list, select the new site’s name. In the right-hand panel select **Policies** then under External sharing, select **Edit**.

1. Set **Site content can be shared with** to **Anyone**.

#### Task 2: Create a site collection using Windows PowerShell

   In the script below, replace *XXXXXX* with your tenant details.

1. Open Edge. Browse to **https://www.microsoft.com/en-us/download/details.aspx?id=35588** (SharePoint Online Management Shell). Download and install the x64 version of the tool.

1. Run **Windows PowerShell ISE** or **Windows PowerShell**.

1. Create a credential. Sign in as the tenant owner.

   ```PowerShell
   $Credential = Get-Credential
   ```

1. Connect to SharePoint Online.

   ```PowerShell
   Connect-SPOService -Url https://XXXXXX-admin.sharepoint.com -Credential $Credential
   ```

1. Verify connectivity.

   ```PowerShell
   Get-SpoSite
   Get-SpoWebTemplate
   ```

1. Create a new site.

   ```PowerShell
   New-SPOSite -Url https://XXXXXX.sharepoint.com/sites/AcctsProj -Owner admin@XXXXXX.onmicrosoft.com -StorageQuota 500 -NoWait -Template PROJECTSITE#0 -Title "Accounts Project"
   ```

#### Task 3: Configure permissions on the site collections

1. In the **SharePoint admin center**, select **Sites > Active Sites**, then select the **Site name** column of **Marketing**.

1. Under **Permissions**, **Additional Admins**, select **Manage**. Add **Tameka**.

1. Open Edge. Browse to the **Office 365 home page** and sign in as **Tameka**.

1. Select SharePoint. Note that Tameka has no sites listed.

1. Open a new browser tab. Browse to **https://XXXXXX.sharepoint.com/sites/marketing**.

1. Select **Not following** and wait for the link to change to “Following”.

1. Open a new browser tab. Browse to **https://XXXXXX.sharepoint.com/sites/marketing**. Sign in as **Catherine**.

   This will fail. Catherine’s account is blocked (from a previous lab).

1. Close Edge.

1. Open Edge. Browse to the **Microsoft 365 admin center** and sign in as the tenant owner.

1. Unblock Catherine’s account.

1. Open a new browser tab. Browse to **https://XXXXXX.sharepoint.com/sites/marketing**. Sign in as **Catherine**.

1. In the **You need permission to access this site** box, enter some text and request access.

1. Close Edge.

1. Switch to the **SharePoint** browser tab and refresh the page. Marketing will appear in the **Following* list.

1. Switch to the **Marketing - Home** browser tab.

1. Select **Settings** (the cog icon), **Site permissions**, **Advanced permissions settings**.

1. Select **Show access requests and invitations**. **Approve** Catherine’s request.

1. Select **Home**.

1. Select **Settings** (the cog icon), **Site permissions**, **Advanced permissions settings**.

1. Select **Marketing Members** then **New**.

1. Invite Francisco.

1. Open Edge. Browse to **https://XXXXXX.sharepoint.com/sites/marketing**. Sign in as **Catherine**.

   Catherine has access to the site.

1. Sign out Catherine and close Edge.

1. Open Edge. Browse to **https://XXXXXX.sharepoint.com/sites/marketing**. Sign in as **Francisco**.

   Francisco has access to the site.

1. Sign out Francisco and close Edge.

### Exercise 3: Configure and verify external user sharing

#### Task 1: Configure a site collection for external user sharing

1. Open Edge. Browse to the **SharePoint admin center** and sign in as the tenant owner.

1. In the Navigation menu, select **Sites > Active sites**.

1. Select **Policies**, **External Sharing**. Set **Site content can be shared with:** **Anyone**.

1. Open a new browser tab. Browse to **https://XXXXXX.sharepoint.com/sites/AcctsProj**.

1. Select **Share** (top-right).

1. Invite **alias@outlook.com**.

1. Select the **Documents** collection. Create a **Word document** called **Budgets**.

1. Select **Share** (top-right). Select **Anyone with the link can view**. Copy the link.

1. Open Outlook on the Web in a new browser tab.

1. Send an e-mail to **alias@outlook.com** with a subject of “Document link” and the link pasted into the message body.

#### Task 2: Verify external user sharing

1. Close all Edge windows.

1. Open Edge. Open the e-mail client for **alias@outlook.com**.

1. Open the “MOD Administrator wants to share Accounts project” e-mail and select **Go To Accounts Project**.

1. Verify that the site loads.

1. Open the “Document link” e-mail and select **Budgets.docx**.

1. Verify that the document loads.

1. Close all Edge windows.
