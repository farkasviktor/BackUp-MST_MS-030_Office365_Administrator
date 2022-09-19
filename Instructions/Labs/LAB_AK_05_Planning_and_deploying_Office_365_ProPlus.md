## Lab 5: Planning and deploying Office 365 ProPlus

### Exercise 1: Prepare an Office 365 ProPlus managed installation

#### Task 1: Download the Office 365 deployment tool

1. On **LON-DC1**, signed in as **ADATUM\Administrator**.

1. Open **Server Manager**. Select **File and Storage Services**, **Shares**.

1. Create a share.

   | Setting | Value |
   | --- | --- |
   | File share profile | SMB Share - Quick |
   | Share location | Select by volume C: |
   | Share Name | OfficeProPlus |
   | Enable access-based enumeration | Off |
   | Allow caching of share | Off |
   | Encrypt data access | Off |
   | NTFS Permissions | Disable inheritance, leave entries as default |
   | Share permissions | Authenticated Users: Full Control |

1. Open Internet Explorer. Browse to **https://www.microsoft.com/en-us/download/details.aspx?id=49117** (Office Deployment Tool). Download and run the tool. 

   Store the extracted files in **C:\Shares\OfficeProPlus**.

#### Task 2: Modify an Office 365 ProPlus installation

1. Run File Explorer. Browse to **C:\Shares\OfficeProPlus**.

1. Right-click **configuration-Office365-x64.xml**, choose **Edit**.

1. Edit the XML.

   ```XML
   <Configuration>
     <Add SourcePath="\\LON-DC1\OfficeProPlus" OfficeClientEdition="64" Channel="Monthly" AllowCdnFallback="TRUE">
       <Product ID="O365ProPlusRetail">
         <Language ID="en-us" />
       </Product>
     </Add>
     <Property Name="PinIconsToTaskbar" Value="TRUE" />
     <Updates Enabled="TRUE" Channel="Monthly" />
     <Logging Level="Standard" Path="\\LON-DC1\OfficeProPlus" />
   </Configuration>
   ```

1. Save the file as **"AdatumConfiguration.xml"**. Including the double-quotes in Notepad will stop Notepad from appending.txt to the file name.

1. Open **Windows PowerShell ISE** or **Windows PowerShell**.

1. Download the setup files.

   ```PowerShell
   cd C:\Shares\OfficeProPlus
   .\setup.exe /download \\LON-DC1\OfficeProPlus\AdatumConfiguration.xml
   ```

   This download takes several minutes to complete. Continue with the next task and leave the download in the background.

### Exercise 2: Manage user-driven Office 365 ProPlus installations

#### Task 1: Manage user rights to install Office 365 ProPlus

1. On **LON-CL1**, signed in as **ADATUM\Administrator**.

1. Open Edge. Browse to the **Microsoft 365 admin center** and sign in as the tenant owner.

1. In the Navigation menu, select **Users > Active users**.

1. Select **Lindsey Gates**. On the **Licenses and Apps** section, deselect **Microsoft 365 apps for enterprise**.

#### Task 2: Install Office 365 ProPlus from the Office 365 portal

1. On **LON-CL3**, signed in as **ADATUM\Administrator**.

1. Open Edge. Browse to the **Office 365 home page** and sign in as **Abbi**.

   This is an AD DS account so the password is **Pa55w.rd**.

1. Verify that Abbi has no apps in the list and no option to install Office 365 apps (the orange link at the top right).

1. Sign out from the portal. Close Edge.

1. Open Edge. Browse to the **Office 365 home page** and sign in as **Lindsey**.

1. Verify that Lindsey has Outlook and OneDrive and the other apps but no option to install Office 365 apps.

1. Sign out from the portal. Close Edge.

1. Open Edge. Browse to the **Office 365 home page** and sign in as **Amy**.

   Note that Amy has Outlook and OneDrive and the other apps and has the option to install Office 365 apps.

1. Select **Install Office** then select **Office 365 apps**. Download and run the tool.

   This installation takes several minutes to complete. Continue with the next task and leave the download in the background.

### Exercise 3: Manage centralized Office 365 ProPlus installations

#### Task 1: Verify ODT download

1. On **LON-DC1**, signed in as **ADATUM\Administrator**.

1. Verify that the ODT download has completed without errors.

1. Run File Explorer. Browse to **C:\Shares\OfficeProPlus**.

   Note the Office folder containing the installation source files.

#### Task 2: Install Office 365 ProPlus using the ODT

1. On **LON-CL4**, signed in as **ADATUM\Administrator**.

1. Using **Run as Administrator**, open **Windows PowerShell ISE** or **Windows PowerShell**.

1. Install the app.

   ```PowerShell
   \\LON-DC1\OfficeProPlus\setup.exe /configure \\LON-DC1\OfficeProPlus\AdatumConfiguration.xml
   ```

1. Wait until the installation has finished on both **LON-CL3** and **LON-CL4**.

#### Task 3: Verify installation

1. On **LON-CL3**, signed in as **ADATUM\Administrator**.

1. Open **Word**. Sign in as **Amy**.

1. At the **Stay signed in to all your apps** screen, select **No, sign in to this app only**.

1. Create a document. Save it to **OneDrive - Contoso**.

1. Close Word.

1. Open **Outlook**. Sign in as **Amy**.

1. Send an e-mail to Sallie.

1. Create a meeting and invite Sallie.

1. On **LON-CL4**, signed in as **ADATUM\Administrator**.

1. Open **Word**. Sign in as **Sallie**.

1. At the **Stay signed in to all your apps** screen, select **No, sign in to this app only**.

1. Create a document. Save it to **Documents**.

   Note that OneDrive for Business is not set up for Sallie, because the Office 365 ProPlus installation was done as ADATUM\Administrator.

1. Close Word.

1. Open **Outlook**. Sign in as **Sallie**.

1. Reply to Amy’s e-mail.

1. Accept Amy’s meeting request.
