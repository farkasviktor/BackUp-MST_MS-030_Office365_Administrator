## Lab 4: Planning and configuring directory synchronization (*Optional*) 

### Exercise 1: Resolve issues

1. Open Edge. Browse to **https://github.com/microsoft/idfix**.

1. Scroll down to the **ClickOnce Launch** heading and select the launch link. Install and run the app.

1. In IdFix, select **Query** on the toolbar. 

   Five issues will be shown.

1. Issue: An Dung Dao’s account has spaces in the User Principal Name.

   Resolution: In the Action column, select **EDIT**.

1. Issue: DefaultAccount has a blank Display Name.

   Resolution: In the Action column, select **EDIT**.

1. Issue: Klemen Sic’s account has two @ symbols in the User Principal Name.

   Resolution: In the Action column, select **EDIT**.

1. Issue: Ngoc Bich Tran’s account has spaces in the User Principal Name.

   Resolution: In the Action column, select **EDIT**.

1. Issue: Lara Raisic and Logan Boyle have the same email adrress. IdFix doesn't display Logan’s account (it should - this is a bug in the tool).

   Resolution: In the Update column, enter **larar@adatum.com**. In the Action column, select **EDIT**.

1. In the toolbar, select **Apply**.

1. In the toolbar, select **Query**. Verify that no issues are listed.

1. Close IdFix.

### Exercise 2: Configure the Azure AD tenant

1. Open **Windows PowerShell ISE** or **Windows PowerShell**.

1. Create a credential. Sign in as the tenant owner.

   ```PowerShell
   $Credential = Get-Credential
   ```

1. Connect to Office 365.

   ```PowerShell
   Connect-MsolService -Credential $Credential
   ```

1. Get DirSync information.

   ```PowerShell
   Get-MsolCompanyInformation | fl *sync*
   ```

1. Verify that DirectorySynchronizationEnable is True. If it is not then run the following and check again.

   ```PowerShell
   Set-MsolDirSyncEnabled -EnableDirSync $true -Force
   ```

### Exercise 3: Download and install AD Connect, set up synchronisation

1. Open Internet Explorer. Browse to the **Microsoft 365 admin center** and sign in as the tenant owner.

1. In the Navigation menu, select **Azure Active Directory**.

1. In the navigation menu of the **Azure Active Directory admin center**, select **Azure Active Directory**. In the **XXXXXX | Overview blade**, select **Azure AD Connect** in the **Manage** section.

1. Select **Download Azure AD Connect**. Download and install the tool.

1. When Microsoft Azure Active Directory Connect runs, select **Customize**.

1. At the **Install required components** screen, select **Install**.

1. At the **User-sign-in** screen, select **Password Hash Synchronization** and select **Next**.

1. At the **Connect to Azure AD** screen, sign in using the tenant owner account and select **Next**.

1. At the **Connect your directories** screen, select **Add directory**.

1. At the **Ad forest account** screen, select **Create new AD account**, sign in using **XXXXXX\Administrator** and select **OK**.

1. At the **Connect your directories** screen, verify that Adatum.com has been added, then select **Next**.

1. At the **Azure AD sign-in configuration** screen, select **Continue without matching all UPN suffixes to verified domains** and select **Next**.

1. At the **Domain and OU filtering** screen, select **Sync selected domains and OUs** and select only the **IT** OU, then select **Next**.

1. At the **Uniquely identifying your users** screen, select **Next**.

1. At the **Filter users and devices** screen, select **Next**.

1. At the **Optional features** screen, select **Next**.

1. At the **Ready to configure** screen, select **Install**.

1. At the **Configuration complete** screen, select **Exit**.


### Exercise 4: Verify synchronisation

1. Switch to the PowerShell session where Connect-MsolService was run.

1. Get DirSync information.

   ```PowerShell
   Get-MsolCompanyInformation | fl *sync*
   ```

1. Verify that all the properties have values (in particular that LastDirSyncTime has a date and time).

1. Open Edge. Browse to the **Microsoft 365 admin center** and sign in as the tenant owner.

1. In the Navigation menu, select **Users > Active users**.

1. Verify that there are more users than before.

1. Check that Beth Burke (IT) does have an account.

1. Check that Vera Pace (Research) does not have an account.

1. Check that Ada Russell (Marketing) does not have an account.


### Exercise 5: Modify synchronisation

1. Open **Azure AD Connect**. Select **Configure**.

1. At the **Additional tasks** screen, select **Customize synchronisation options** and select **Next**.

1. At the **Connect to Azure AD** screen, sign in using the tenant owner account and select **Next**.

1. At the **Connect your directories** screen, select **Next**.

1. At the **Domain and OU filtering** screen, select the **Research** OU, then select **Next**.

1. At the **Optional features** screen, verify that **Password hash synchronization** is enabled, enable **Password writeback**, then select **Next**.

1. At the **Ready to configure** screen, select **Configure**.

1. At the **Configuration complete** screen, select **Exit**.

1. Open **Windows PowerShell ISE** or **Windows PowerShell**.

1. Perform a manual sync.

   ```PowerShell
   Start-AdSyncSyncCycle Delta
   ```

### Exercise 6: Verify synchronisation

1. Open Edge. Browse to the **Microsoft 365 admin center** and sign in as the tenant owner.

1. In the Navigation menu, select **Users > Active users**.

1. Check that Vera Pace does have an account.

#### Exercise 7: Assign licenses

1. Open Edge. Browse to the **Microsoft 365 admin center** and sign in as the tenant owner.

1. In the Navigation menu, select **Users > Active users**.

1. Select **Filter**, **Licensed users**.

1. Tick all the users imported earlier using the csv file (some or all of Nona, Jessica, Misty, Elvis, Leila, Sheri, Mickey and Leanna).

1. Remove all product licenses.

1. Select **Filter**, **Unlicensed users**.

1. Tick Ada, Arturs, August and Cai.

1. Add **Enterprise Mobility + Security E5** and **Office 365 E5** licenses, with a **Usage location** of **Switzerland**.
