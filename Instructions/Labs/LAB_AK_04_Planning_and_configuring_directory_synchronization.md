## Lab 4: Planning and configuring directory synchronization

### Exercise 1: Prepare for directory synchonisation

1. On **LON-DC1**, signed in as **ADATUM\Administrator**.

1. Open **Active Directory Domains and Trusts**.

1. In the console tree, right-click **Active Directory Domains and Trusts [LON-DC1.Adatum.com]**, choose **Properties**.

1. Add a UPN suffix of **adatumXXXXXX.onelearndns.com**.

1. Open **Windows PowerShell ISE** or **Windows PowerShell**.

1. Set the UPN suffixes for all users.

   ```PowerShell
   Get-ADUser -Filter * -Properties SamAccountName | ForEach-Object { Set-ADUser $PSItem -UserPrincipalName ($PSItem.SamAccountName + "@adatumXXXXXX.onelearndns.com" ) }
   ```

### Exercise 2: Create issues

1. Run the break script.

   ```PowerShell
   cd C:\Labfiles
   .\CreateProblemUsers.ps1
   ```

1. Verify that five accounts were updated - Klemen, Lara, Logan, Holly and Maj. Note that IdFix will not detect the issues with Holly and Maj.

### Exercise 3: Resolve issues

1. On **LON-CL1**, signed in as **ADATUM\Administrator**.

   Not LON-DC1 - it does not have the .NET Framework required.

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

### Exercise 4: Configure the Azure AD tenant

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

### Exercise 5: Download and install AD Connect, set up synchronisation

1. On **LON-DS1**, signed in as **ADATUM\Administrator**.

1. Open Internet Explorer. Browse to the **Microsoft 365 admin center** and sign in as the tenant owner.

1. In the Navigation menu, select **Azure Active Directory**.

1. In the navigation menu of the **Azure Active Directory admin center**, select **Azure Active Directory**. In the **Contoso | Overview blade**, select **Azure AD Connect** in the **Manage** section.

1. Select **Download Azure AD Connect**. Download and install the tool.

1. When Microsoft Azure Active Directory Connect runs, select **Customize**.

1. At the **Install required components** screen, select **Install**.

1. At the **User-sign-in** screen, select **Password Hash Synchronization** and select **Next**.

1. At the **Connect to Azure AD** screen, sign in using the tenant owner account and select **Next**.

1. At the **Connect your directories** screen, select **Add directory**.

1. At the **Ad forest account** screen, select **Create new AD account**, sign in using **ADATUM\Administrator** and select **OK**.

1. At the **Connect your directories** screen, verify that Adatum.com has been added, then select **Next**.

1. At the **Azure AD sign-in configuration** screen, select **Continue without matching all UPN suffixes to verified domains** and select **Next**.

1. At the **Domain and OU filtering** screen, select **Sync selected domains and OUs** and select only the **IT** OU, then select **Next**.

1. At the **Uniquely identifying your users** screen, select **Next**.

1. At the **Filter users and devices** screen, select **Next**.

1. At the **Optional features** screen, select **Next**.

1. At the **Ready to configure** screen, select **Install**.

1. At the **Configuration complete** screen, select **Exit**.


### Exercise 6: Verify synchronisation

1. On **LON-CL1**, signed in as **ADATUM\Administrator**.

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


### Exercise 7: Modify synchronisation

1. On **LON-DS1**, signed in as **ADATUM\Administrator**.

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

### Exercise 8: Verify synchronisation

1. On **LON-CL1**, signed in as **ADATUM\Administrator**.

1. Open Edge. Browse to the **Microsoft 365 admin center** and sign in as the tenant owner.

1. In the Navigation menu, select **Users > Active users**.

1. Check that Vera Pace does have an account.

### Exercise 9: Manage AD DS users and groups

1. On **LON-DC1**, signed in as **ADATUM\Administrator**.

1. Open **Active Directory Users and Computers**.

1. Select the **Research** OU.

1. Create a user.

   | Setting | Value |
   | --- | --- |
   | First name | Perry |
   | Last name | Brill |
   | Full name | Perry Brill |
   | User logon name | perry@adatumXXXXXX.onelearndns.com |
   | User logon name (pre-Windows 2000) | ADATUM\perry |
   | Password | Pa55w.rd |
   | Password options | Unselected |

1. Create a group.

   | Setting | Value |
   | --- | --- |
   | Group name | Project Team |
   | Group name (pre-Windows 2000) | Project Team |
   | Scope | Universal |
   | Type | Security |

1. Move **Vera Pace** to the **Marketing** OU.

1. Edit the **Research** security group.

   Remove **Vera Pace** and **Tia Zecirevic**. Add **Ada Russell**.

1. Select the **Marketing** OU.

1. Move **Ada Russell** to the **Research** OU.


### Exercise 10: Synchronise

1. On **LON-DS1**, signed in as **ADATUM\Administrator**.

1. Open **Windows PowerShell ISE** or **Windows PowerShell**.

1. Perform a manual sync.

   ```PowerShell
   Start-AdSyncSyncCycle Delta
   ```

### Exercise 11: Verify synchronisation

1. On **LON-CL1**, signed in as **ADATUM\Administrator**.

1. Open Edge. Browse to the **Microsoft 365 admin center** and sign in as the tenant owner.

1. In the Navigation menu, select **Users > Active users**.

1. Check that Vera Pace does not have an account any more.

1. Check that Ada Russell does have an account.

1. Check that Perry Brill does have an account.

1. In the Navigation menu, select **Groups > Active groups**.

1. Check that Project Team is present.

1. Check that Ada is a member of the Research group and that Vera Pace and Tia Zecirevic are not.


#### Exercise 12: Assign licenses

1. On **LON-CL1**, signed in as **ADATUM\Administrator**.

1. Open Edge. Browse to the **Microsoft 365 admin center** and sign in as the tenant owner.

1. In the Navigation menu, select **Users > Active users**.

1. Select **Filter**, **Licensed users**.

1. Tick all the users imported earlier using the csv file (some or all of Nona, Jessica, Misty, Elvis, Leila, Sheri, Mickey and Leanna).

1. Remove all product licenses.

1. Select **Filter**, **Unlicensed users**.

1. Tick Ada, Arturs, August and Cai.

1. Add **Enterprise Mobility + Security E5** and **Office 365 E5** licenses, with a **Usage location** of **Switzerland**.


#### Exercise 13: Enable Seamless SSO (*Optional*)

#### Task 1: Azure AD Connect

1. On **LON-DS1**, signed in as **ADATUM\Administrator**.

1. Open **Azure AD Connect**. Select **Configure**.

1. At the **Additional tasks** screen, select **Change user sign-in** and select **Next**.

1. At the **Connect to Azure AD** screen, sign in using the tenant owner account and select **Next**.

1. At the **User sign-in** screen, select the **Enable single sign-on**, then select **Next**.

1. At the **Enable single-sign-on** screen, select **Enter credentials**. Sign in as **ADATUM\Administrator**. Select **Next**.

1. At the **Ready to congure** screen, select **Configure**.

1. At the **Configuration complete** screen, select **Exit**.

1. Open **Windows PowerShell ISE** or **Windows PowerShell**.

1. Perform a manual sync.

   ```PowerShell
   Start-AdSyncSyncCycle Delta
   ```

#### Task 2: Group Policy

1. On **LON-DC1**, signed in as **ADATUM\Administrator**.

1. Open **Group Policy Management**.

1. Edit **Default Domain Policy**. Navigate to **User Configuration** > **Preferences** > **Window Settings** > **Registry**.

1. Create a new **Registry item**.

   | Setting | Value |
   | --- | --- |
   | Action | Update |
   | Hive | HKEY_CURRENT_USER |
   | Key Path | software\Microsoft\Windows\CurrentVersion\Internet Settings\ZoneMap\Domains\microsoftazuread-sso.com\autologon |
   | Value name | https |
   | Value type | REG_DWORD |
   | Value data | 1 |

1. Close **Group Policy Management Editor**.
