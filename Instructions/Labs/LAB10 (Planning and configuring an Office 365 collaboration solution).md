## Lab 10: Planning and configuring an Office 365 collaboration solution 

### Exercise 1: Configure Yammer

1. Open Microsoft Edge from the taskbar, and then browse to https://portal.office.com.

2. Sign in as **Admin@XXXXXX.onmicrosoft.com**.

3. Select the **Office 365 app** launcher icon, and then Select **Yammer**.

4. On the **WHO DO YOU WORK WITH?** page, Select the **X** at the top-right corner to close the page.

5. In Yammer, in the left pane beside MOD Administrator, Select the **Settings** icon.

6. Select **NETWORK ADMIN**.

7. In Yammer admin center, in the left navigation pane, Select **Usage Policy**.

8. In the **Usage Policy** window, select the **Require users to accept policy** during sign up and after any changes are made to the policy check box.

9. In the **Usage Policy** window, select the **Display policy reminder** in sidebar check box.

10. In the **Custom Policy Title** text box, type **M365x Acceptable Use Policy**.

11. In the **Enter your policy in the textbox** below text box, copy and paste the following text:

Welcome to Yammer! Our goal is to provide a collaborative environment to connect with colleagues and bridge various departments and geographic locations to share meaningful information.

12. Select **Save**.

13. In the **M365x Acceptable Use Policy** window, Select **I Accept**. 

14. If needed, in Yammer, in the left pane beside MOD Administrator, Select the **Settings** icon, and then Select **NETWORK ADMIN**.

15. In the left menu of the Yammer console, Select **Configuration**.

16. In the **Email Settings section**, Select **A weekly digest of your group messages**.

17. In the **Enabled Features** page, remove the check mark from **3rd Party Applications**.

18. Select **Save**.

19. In the left-side menu of the Yammer console, Select **Data Retention**.

20. In the **Data Retention Policy** page, read the description of available options and Select **Soft Delete** and then Select **Save**.

21. In the left menu of the Yammer console, Select **Monitor Keywords**.

22. In the **Monitor Keywords** page, type **Admin@XXXXXX.onmicrosoft.com** in the **Email Address** field.

23. In the text box below, type the following words, one in each line:gambling,erotic,warez.

24. Select **Save**.

25. In the left menu of the Yammer console, Select **Success**.

26. Selec **Write a welcome** message in the middle pane.

27. Select **All Company**, and in the middle pane, in the **What are you working on?** text box, type: Welcome to all Adatum users!, and then Select **Post**.

### Task 2: Configure Yammer service settings, and enforce Office 365 identity

1. In Yammer, in the left pane, Select the **Settings** icon.

2. Select **NETWORK ADMIN**.

3. In Yammer admin center, in the left navigation pane in the **Content and Security** section, Select **Security Settings**.

4. Scroll down to **Office365 Identity Enforcement**. 

5. Select the **Enforce Office 365 identity** check box.

6. In the pop-up window, Select **Okay**.

7. Select **Save**.


### Task 3: Configure the Yammer user experience

1. In Yammer, in the left pane, Select the **Setting**s icon, and then Select **EDITSETTINGS**.

2. In the toolbar, Select **Notifications**.

3. In the **Send me a digest of message activity** drop-down list, Select **weekly**.

4. Select only the following options in the **Email me when...** section:

		-I receive a message in my inbox

		-I log in from somewhere new

		-I post a message via email (This will send a confirmation email)

5. Select **Save**.

6. Close Microsoft Edge.


### Task 4: Using Yammer

1. Open Microsoft Edge, and then connect to **https://portal.office.com**.

2. Sign in as **Beth@XXXXXX.onmicrosoft.com**.

3. On the Office 365 portal, Select **Yammer**.

4. At the **WHO DO YOU WORK WITH** prompt, type **Christie in the first** text box, and then Select **DONE** and close the window.

5. Select **I Accept** at the **M365x Acceptable Use Policy prompt**.

6. Find the post from MOD Administrator in the post list.

7. Select **Like**, and then Select **SHARE**.

8. In the **Share This Conversation** dialog box, select **Post** in a Group, type **All Company** in the drop-down box, and then in the text box, type **Welcome from me too**.

9. Select **Share**.

10. Select **All Company** and in the **What are you working** on text box, type “free gambling here”, and then Select **Post**.

11. Close Microsoft Edge.

12. Open Microsoft Edge and browse to **https://portal.office.com**.

13. Sign in as **Admin@XXXXXX.onmicrosoft.com**.

14. On the Office 365 portal, Select **Mail**.

15. Verify that you received a message from Yammer with a report about a monitored keyword appearance in Beth’s post.

16. Close Microsoft Edge.

Results: After completing this exercise, you should have enabled Yammer Enterprise for A. Datum Corporation.



### Exercise 2: Configure OneDrive for Business

#### Task 1: Enable OneDrive for Business synchronization (cloud-only users)

1. Open **Word**. Sign in as **Amy**.

1. Create a document and save it to **OneDrive - XXXXXX**.

1. Open Edge. Browse to the **Office 365 home page** and sign in as **Amy**.

1. Select **OneDrive**. Verify that the new document is listed.

1. Open **File Explorer**.

1. Select **OneDrive**. Sign in as **Amy**.

1. Once OneDrive synchronisation is complete, select **OneDrive - XXXXXX**. Verify that the new document is listed.

1. Other client open **Word**.

1. Select **Account**. Sign out administrator@XXXXXX.onmicrosoft.com and sign in as **Sallie**.

1. Under **Connected Services**, add **Storage > OneDrive for Business**. Sign in as **Sallie**.

1. Create a document and save it to **OneDrive - XXXXXX**.

1. Open Edge. Browse to the **Office 365 home page** and sign in as **Sallie**.

1. Select **OneDrive**. Verify that the new document is listed.

1. Open **File Explorer**.

1. Select **OneDrive**. Sign in as **Sallie**.

1. Once OneDrive synchronisation is complete, select **OneDrive - XXXXXX**. Verify that the new document is listed.


#### Task 2: Share files with other users

1. Open **File Explorer**.

1. Select **OneDrive - XXXXXX**.

1. Create a folder called **Tailspin Project**. Right-click **Tailspin Project**, choose **Share**. Select **Anyone with the link can edit**. Send the link to **Amy Santiago**.

1. Run **Outlook**. Sign in as **Amy**.

1. Open the “Sallie McIntosh shared the folder” e-mail and select **Tailspin Project**.

1. Verify that the folder loads (in Edge).

#### Task 3: Enable OneDrive for Business synchronization (synced users) (*Optional*)

If Seamless SSO has been set up then the AD DS users will not need to provide passwords to sign in to Office 365 resources.

1. Signed in as **XXXXXX\Ada**.

1. Open **Word**.

1. Select **Account**. If required, sign in as **Ada**.

1. Create a document and save it to **OneDrive - XXXXXX**.

1. Open Edge. Browse to the **Office 365 home page** and sign in as **Ada**.

1. Select **OneDrive**. Verify that the new document is listed.

1. Open **File Explorer**.

1. Select **OneDrive**. Sign in as **Ada**.

1. Once OneDrive synchronisation is complete, select **OneDrive - XXXXXX**. Verify that the new document is listed.

1. Signed in as **XXXXXX\Cai**.

1. *Repeat the above steps.*

*Note*: Why is the OneDrive for Business folder called “OneDrive - XXXXXX”? Because the tenant name is “XXXXXX”.

Microsoft 365 admin center, Settings | Org settings, Organization profile, Organization information.


### Exercise 3: Configuring Microsoft 365 groups

#### Task 1: Configure a private Microsoft 365 group using the portal

1. Open Edge. Browse to the **Microsoft 365 admin center** and sign in as the tenant owner.

1. In the Navigation menu, select **Groups > Active groups**.

1. Add a group.

   | Setting | Value |
   | --- | --- |
   | Type | Microsoft 365 |
   | Name | XXXXXX Marketing |
   | Description | XXXXXX Corporation Marketing team |
   | Owners | MOD Administrator, Holly Dickson |
   | Group email address | adatummarketing@XXXXXX.onmicrosoft.com |
   | Privacy | Private |
   | Create a team for this group | Selected |

1. **Refresh** the list until ADatum Marketing appears.

1. Select **ADatum Marketing**. Add a member, select **Amy** and **Cai**.

#### Task 2: Configure a public Office 365 group using PowerShell

1. Open **Windows PowerShell ISE** or **Windows PowerShell**.

1. Create a credential. Sign in as the tenant owner.

   ```PowerShell
   $Credential = Get-Credential
   ```

1. Connect to Exchange Online.

   ```PowerShell
   $PSSession = New-PSSession -ConfigurationName "Microsoft.Exchange" -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $Credential -Authentication "Basic" -AllowRedirection
   Import-PSSession $PSSession -DisableNameChecking
   ```

1. Create a Microsoft 365 group.

   ```PowerShell
   New-UnifiedGroup -DisplayName "Planning Group" -Alias "PlanningGroup" -EmailAddresses "planninggroup@XXXXXX.onmicrosoft.com" -Owner "MOD Administrator" -Members "Francisco" -AccessType Public
   ```

1. Add additional owners.

   ```PowerShell
   Add-UnifiedGroupLinks "Planning Group" -Links "Holly Dickson" -LinkType Owner
   ```

   Note the “Only Members can be Owners of a group. Please add 'holly' first as members before adding them as owners.” error message.

1. Add additional members.

   ```PowerShell
   Add-UnifiedGroupLinks "Planning Group" -Links "Sallie McIntosh", "Holly Dickson" -LinkType Member
   ```

1. Add additional owners.

   ```PowerShell
   Add-UnifiedGroupLinks "Planning Group" -Links "Holly Dickson" -LinkType Owner
   ```

1. List groups and members.

   ```PowerShell
   Get-UnifiedGroup
   Get-UnifiedGroup | fl *name
   Get-UnifiedGroup "Planning Group" | Get-UnifiedGroupLinks -LinkType Member
   Get-UnifiedGroup "Planning Group" | Get-UnifiedGroupLinks -LinkType Owner
   ```

#### Task 3: Explore the Office 365 group components

1. Open Edge. Browse to the **Office 365 home page** and sign in as **Amy**.

1. From the home page, select **Outlook**.

1. Note the “You've joined the XXXXXX Marketing group” e-mail.

1. In the left pane, select **XXXXXX Marketing** (scroll down).

1. Send an e-mail to the group.

1. In the left pane, select **Discover groups** (scroll down).

1. Search for **Planning Group** and join it.

   The group is public, so Amy does not need permission or approval to join the group.

1. In the left pane, select **Planning Group** (scroll down).

1. Send an e-mail to the group.

1. Open **Outlook**. Sign in as **Amy**, select **No, sign in to this app only**.

1. In the left pane, select **Planning Group**.

1. Verify that the message from Amy is present.

1. Open **Teams**. Sign in as **Amy**, select **No, sign in to this app only**.

1. In the **Teams** list, select **XXXXXX Marketing**.

1. Verify that there are no posts. Email messages to a group do not appear in the Teams app.

1. In the **Activity feed**, note the “MOD added you to XXXXXX Marketing” message.

1. Open Edge. Browse to the **Office 365 home page** and sign in as **Sallie**.

1. From the home page, select **Outlook**.

1. Note that there is no “You've joined the Planning Group group” e-mail (because Sallie was added using PowerShell).

1. In the left pane, select **Planning Group** (scroll down).

1. Send an e-mail to the group.

1. Open **Outlook**. Sign in as **Sallie**, select **No, sign in to this app only**.

1. In the left pane, select **Planning Group**.

1. Verify that the message from Amy and the mesage from Sallie are present.

1. Open **Teams**. Sign in as **Sallie**, select **No, sign in to this app only**.

1. Verify that there is no Planning Group team.

1. Select **Join or create a team**, then **Create team**, then **Create from… An existing Microsoft 365 group or team**.

1. No groups are listed, because Sallie is not an owner of any groups.

1. Sign out of Teams.

1. Open **Teams**. Sign in as **Holly**, select **No, sign in to this app only**.

1. Select **Join or create a team**, then **Create team**, then **Create from… An existing Microsoft 365 group or team**, then **Microsoft 365 group**.

1. Select **Planning Group** and select **Create**.

1. Verify that the Planning Group team is present.

1. Sign out of Teams.
