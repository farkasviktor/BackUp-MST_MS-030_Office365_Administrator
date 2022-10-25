## Lab 2A: Managing Office 365 users and groups using the portal

### Exercise 1: Create users

1. Open Edge. Browse to the **Microsoft 365 admin center** and sign in as the tenant owner.

1. In the Navigation menu, select **Users > Active users**.

1. Add a user.

   | Setting | Value |
   | --- | --- |
   | First name | Amy |
   | Last name | Santiago |
   | Display Name | Amy Santiago |
   | Username | amy@XXXXXX.onmicrosoft.com |
   | Password | Pa55w.rd1234 |
   | Require the user to change their password when they first sign in | No |
   | Location | Switzerland |
   | Licenses | Office 365 E5, Enterprise Mobility + Security E5 |
   | Roles | User |
   | Department | (Leave blank) |

1. Add a user.

   | Setting | Value |
   | --- | --- |
   | First name | Christie |
   | Last name | Thomas |
   | Display Name | Christie Thomas |
   | Username | christie@XXXXXX.onmicrosoft.com |
   | Password | Pa55w.rd1234 |
   | Require the user to change their password when they first sign in | No |
   | Location | Switzerland |
   | Licenses | Office 365 E5, Enterprise Mobility + Security E5 |
   | Roles | User |
   | Department | Sales |

1. Add a user.

   | Setting | Value |
   | --- | --- |
   | First name | Francisco |
   | Last name | Chaves |
   | Display Name | Francisco Chaves |
   | Username | francisco@XXXXXX.onmicrosoft.com |
   | Password | Pa55w.rd1234 |
   | Require the user to change their password when they first sign in | No |
   | Location | Switzerland |
   | Licenses | Office 365 E5, Enterprise Mobility + Security E5 |
   | Roles | User |
   | Department | Accounts |

1. Add a user.

   | Setting | Value |
   | --- | --- |
   | First name | Lindsey |
   | Last name | Gates |
   | Display Name | Lindsey Gates |
   | Username | lindsey@XXXXXX.onmicrosoft.com |
   | Password | Pa55w.rd1234 |
   | Require the user to change their password when they first sign in | No |
   | Location | Switzerland |
   | Licenses | Office 365 E5, Enterprise Mobility + Security E5 |
   | Roles | User |
   | Department | Sales |

1. Add a user.

   | Setting | Value |
   | --- | --- |
   | First name | Sallie |
   | Last name | McIntosh |
   | Display Name | Sallie McIntosh |
   | Username | sallie@XXXXXX.onmicrosoft.com |
   | Password | Pa55w.rd1234 |
   | Require the user to change their password when they first sign in | No |
   | Location | Switzerland |
   | Licenses | Office 365 E5, Enterprise Mobility + Security E5 |
   | Roles | User |
   | Department | Accounts |

1. Add a user.

   | Setting | Value |
   | --- | --- |
   | First name | Holly |
   | Last name | Dickson |
   | Display Name | Holly Dickson |
   | Username | holly@XXXXXX.onmicrosoft.com |
   | Password | Pa55w.rd1234 |
   | Require the user to change their password when they first sign in | No |
   | Location | Switzerland |
   | Licenses | Office 365 E5, Enterprise Mobility + Security E5 |
   | Roles | Global admin |
   | Department | IT |

### Exercise 2: Modify users

1. Switch to the **Microsoft 365 admin center** browser.

1. Select **Amy Santiago**.

1. Set Amy’s department to Sales.

### Exercise 3: Block a user

1. Switch to the **Microsoft 365 admin center** browser.

1. Select **Francisco Chaves**.

1. Block Francisco’s sign-in.

1. Open an InPrivate Edge window. Browse to the **Office 365 home page** and sign in as **Francisco**.

1. You will see a “Your account has been locked” message.

1. Close the InPrivate window.

1. Select the **Microsoft 365 admin center** browser window signed in as the tenant owner account.

1. In the **Active Users** list, select **Francisco Chaves**.

1. Unblock Francisco’s sign-in.

   *This may take up to 15 minutes to take effect.*

1. In Edge, open an InPrivate window and sign in to the Office portal again as Francisco.

1. Close the InPrivate window.

### Exercise 4: Delete and undelete a user

1. Switch to the **Microsoft 365 admin center** browser.

1. In the **Active Users** list, select **Lindsey Gates**.

1. Delete Lindsey’s account.

1. Open an InPrivate Edge window. Browse to the **Office 365 home page** and sign in as **Lindsey**.

1. You will see a “This username may be incorrect” message.

1. Close the InPrivate window.

1. Switch to the **Microsoft 365 admin center** browser.

1. In the Navigation menu, select **Users > Deleted users**.

1. In the **Deleted Users** list, select **Lindsey Gates**.

1. Restore the user account. Use an automatically-generated password and note down the temporary password.

1. In Edge, open an InPrivate window and sign in to the Office portal again as Lindsey, using the temporary password. Change the password to **Pa55w.rd1234**.

1. Note that Lindsey has no apps in the list. Deleting the account removed the licence assignment.

1. Close the InPrivate window.

1. Switch to the **Microsoft 365 admin center** browser.

1. In the Navigation menu, select **Users > Active users**.

1. In the **Active Users** list, select **Lindsey Gates**.

1. Assign **Office 365 E5** and **Enterprise Mobility + Security E5** licenses.

### Exercise 5: Manage password policy

1. Switch to the **Microsoft 365 admin center** browser.

1. In the Navigation menu, select **Settings > Org settings**.

1. Select **Security & privacy** then select **Password expiration policy**.

1. Set 14 days before passwords expire, 14 days before a user is notified.

1. Open an InPrivate Edge window. Browse to the **Office 365 home page** and sign in as **Lindsey**.

1. Note that Lindsey now has Outlook, OneDrive, etc in the list.

1. Select the Notification icon in the top right. Note the “Time to change your password” message.

1. Close the InPrivate window.

### Exercise 6: Enable multifactor authentication

TODO: https://docs.microsoft.com/en-us/azure/active-directory/authentication/tutorial-enable-azure-mfa

### Exercise 7: Create groups

1. Open Edge. Browse to the **Microsoft 365 admin center** and sign in as the tenant owner.

1. In the Navigation menu, select **Groups > Active groups**.

1. Add a group.

   | Setting | Value |
   | --- | --- |
   | Type | Security |
   | Name | Sales |
   | Description | Sales department |

1. Add a group.

   | Setting | Value |
   | --- | --- |
   | Type | Security |
   | Name | Accounts |
   | Description | Accounts department |

### Exercise 8: Modify groups

1. In the **Active groups** list, select **Refresh**. Repeat until both Sales and Accounts are in the list.

1. Select **Sales**. Set the members.

   | Setting | Value |
   | --- | --- |
   | Owners | Lindsey Gates |
   | Members | Lindsey Gates, Christie Thomas, Amy Santiago |

1. Select **Accounts**. Set the members.

   | Setting | Value |
   | --- | --- |
   | Owners | Francisco Chaves |
   | Members | Sallie McIntosh, Francisco Chaves |

### Exercise 9: Delete a group

1. Select **Sales**.

1. Delete the group.

1. In the Navigation menu, select **Users > Active users**. Verify that the user accounts for Amy, Christie and Lindsey are still present.

1. In the Navigation menu, select **Groups > Deleted groups**. The Sales group does not appear. Only Microsoft 365 groups can be undeleted.


____________________________________________________________
## Lab 2B: Managing Office 365 users and groups using PowerShell

### Exercise 1: Create users

1. Using **Run as Administrator**, open **Windows PowerShell ISE** or **Windows PowerShell**.

1. Install the latest version of the MSOnline module.

   ```PowerShell
   Install-Module MSOnline -Force
   ```

1. Close **Windows PowerShell ISE** and open it again without using Run as administrator.

1. Create a credential. Sign in as the tenant owner.

   ```PowerShell
   $Credential = Get-Credential
   ```

1. Connect to Office 365.

   ```PowerShell
   Connect-MsolService -Credential $Credential
   ```

1. Enable Directory Synchonisation (in preparation for Lab 4).

   ```PowerShell
   Set-MsolDirSyncEnabled -EnableDirSync $true -Force
   ```

1. Create the users.

   ```PowerShell
   New-MsolUser -UserPrincipalName "catherine@XXXXXX.onmicrosoft.com" -DisplayName "Catherine Richard" -FirstName "Catherine" -LastName "Richard" -Password "Pa55w.rd1234" -ForceChangePassword $false -UsageLocation "CH"
   ```

   ```PowerShell
   New-MsolUser -UserPrincipalName "tameka@XXXXXX.onmicrosoft.com" -DisplayName "Tameka Reed" -FirstName "Tameka" -LastName "Reed" -Password "Pa55w.rd1234" -ForceChangePassword $false -UsageLocation "CH"
   ```

### Exercise 2: Licence users

1. List the unlicensed users.

   ```PowerShell
   Get-MsolUser -UnlicensedUsersOnly
   ```

1. Determine the available licenses.

   ```PowerShell
   Get-MsolAccountSku
   ```

1. Assign licenses. Edit the correct license name (XXXXXXX:ENTERPRISEPREMIUM) before running the script.

   ```PowerShell
   Set-MsolUserLicense -UserPrincipalName "catherine@XXXXXX.onmicrosoft.com" -AddLicenses "XXXXXXX:ENTERPRISEPREMIUM", "XXXXXXX:EMSPREMIUM"
   ```

   ```PowerShell
   Set-MsolUserLicense -UserPrincipalName "tameka@XXXXXX.onmicrosoft.com" -AddLicenses "XXXXXXX:ENTERPRISEPREMIUM", "XXXXXXX:EMSPREMIUM"
   ```

### Exercise 3: Block a user

1. Block Catherine’s sign-in.

   ```PowerShell
   Set-MsolUser -UserPrincipalName "catherine@XXXXXX.onmicrosoft.com" -BlockCredential $true
   ```

### Exercise 4: Delete and undelete a user

1. Delete Catherine’s user account.

   ```PowerShell
   Remove-MsolUser -UserPrincipalName "catherine@XXXXXX.onmicrosoft.com"
   ```

1. List all deleted users. Note that Catherine’s account is still licensed.

   ```PowerShell
   Get-MsolUser -ReturnDeletedUsers
   ```

1. Undelete Catherine’s user account.

   ```PowerShell
   Restore-MsolUser -UserPrincipalName "catherine@XXXXXX.onmicrosoft.com"
   ```

1. List users.

   ```PowerShell
   Get-MsolUser
   Get-MsolUser -UnlicensedUsersOnly
   Get-MsolUser -ReturnDeletedUsers
   ```

### Exercise 5: Bulk create users

1. Run **Explorer** and navigate to **C:\Labfiles**.

1. Right-click **O365users.csv**, choose **Edit**.

1. Replace all yourdomain.hostdomain.com with XXXXXX.onmicrosoft.com.

1. Replace all adatumyyxxxx:ENTERPRISEPACK with XXXXXXX:ENTERPRISEPREMIUM.

1. Save the file and close Notepad.

1. Load the file and use it to create users. Note that you might run out of licenses. If so, make a note of which users were not created.

   ```PowerShell
   Import-Csv -Path "C:\labfiles\O365Users.csv" | ForEach-Object { New-MsolUser -UserPrincipalName $PSItem."UPN" -AlternateEmailAddresses $PSItem."AltEmail" -FirstName $PSItem."FirstName" -LastName $PSItem."LastName" -DisplayName $PSItem."DisplayName" -BlockCredential $False -ForceChangePassword $False -LicenseAssignment $PSItem."LicenseAssignment" -Password $PSItem."Password" -PasswordNeverExpires $True -Title $PSItem."Title" -Department $PSItem."Department" -Office $PSItem."Office" -PhoneNumber $PSItem."PhoneNumber" -MobilePhone $PSItem."MobilePhone" -Fax $PSItem."Fax" -StreetAddress $PSItem."StreetAddress" -City $PSItem."City" -State $PSItem."State" -PostalCode $PSItem."PostalCode" -Country $PSItem."Country" -UsageLocation $PSItem."UsageLocation" }
   ```

1. List users.

   ```PowerShell
   Get-MsolUser
   ```

### Exercise 6: Modify groups

1. Create a group.

   ```PowerShell
   New-MsolGroup -DisplayName "Marketing" -Description "Marketing department"
   ```

1. Add members.

   ```PowerShell
   $MarketingGroup = Get-MsolGroup | Where-Object DisplayName -eq "Marketing"
   $CatherineUser = Get-MsolUser | Where-Object DisplayName -eq "Catherine Richard"
   $TamekaUser = Get-MsolUser | Where-Object DisplayName -eq "Tameka Reed"
   Add-MsolGroupMember -GroupObjectId $MarketingGroup.ObjectId -GroupMemberType "User" -GroupMemberObjectId $CatherineUser.ObjectId
   Add-MsolGroupMember -GroupObjectId $MarketingGroup.ObjectId -GroupMemberType "User" -GroupMemberObjectId $TamekaUser.ObjectId
   ```

1. Verify membership.

   ```PowerShell
   Get-MsolGroupMember -GroupObjectId $MarketingGroup.ObjectId
   ```

### Exercise 7: Manage passwords and password policy

1. Set password expiry.

   ```PowerShell
   Set-MsolPasswordPolicy -DomainName "XXXXXX.onmicrosoft.com" -ValidityPeriod 90 -NotificationDays 14
   ```

   If you wanted to do this for all of your domains, you could use the following.

   ```PowerShell
   Get-MsolDomain | Where-Object IsInitial -eq $false | Select-Object @{ l="DomainName"; e={$PSItem.Name} } | Set-MsolPasswordPolicy -ValidityPeriod 90 -NotificationDays 14
   ```

1. Reset a user’s password.

   ```PowerShell
   Set-MsolUserPassword -UserPrincipalName "tameka@XXXXXX.onmicrosoft.com" -NewPassword "Pa55w.rd9876"
   ```

1. Disable password expiry for all users (for ease of use during the labs).

   ```PowerShell
   Get-MsolUser | Set-MsolUser -PasswordNeverExpires $true
   ```


____________________________________________________________
## Lab 2C: Managing Office 365 service administrators

### Exercise 1: Set service administrators using the portal

1. Open Edge. Browse to the **Microsoft 365 admin center** and sign in as the tenant owner.

1. In the Navigation menu, select **Users > Active users**.

1. Select **Francisco Chaves**.

1. Select **Manage roles**, **Billing admin** (in the **Other** section).

1. Select **Tameka Reed**.

1. Select **Manage roles**, **Password admin** (in the **Identity** section).

1. Select **Christie Thomas**.

1. Select **Manage roles**, **User admin**.

1. Close all Edge windows.


### Exercise 2: Set service administrators using PowerShell

1. Assign roles.

   ```PowerShell
   Add-MsolRoleMember -RoleName "Service Support Administrator" -RoleMemberEmailAddress "sallie@XXXXXX.onmicrosoft.com"
   ```

   ```PowerShell
   Add-MsolRoleMember -RoleName "Company Administrator" -RoleMemberEmailAddress "amy@XXXXXX.onmicrosoft.com"
   ```

1. Verify role membership.

   ```PowerShell
   $role = Get-MsolRole -RoleName "Service Support Administrator"
   Get-MsolRoleMember -RoleObjectId $role.ObjectId
   ```

   ```PowerShell
   $role = Get-MsolRole -RoleName "Billing Administrator"
   Get-MsolRoleMember -RoleObjectId $role.ObjectId
   ```

   ```PowerShell
   $role = Get-MsolRole -RoleName "Company Administrator"
   Get-MsolRoleMember -RoleObjectId $role.ObjectId
   ```

### Exercise 3: Test service administrators

1. Open Edge. Browse to the **Microsoft 365 admin center** and sign in as **Tameka**.

1. In the Navigation menu, select **Users > Active users**.

1. In the **Active Users** list, select **Jessica Jennings**.

1. Note that you cannot change group membership or contact information.

1. Reset Jessica’s password to **Pa55w.rd9876**.

1. Sign out of the admin center and close Edge.

1. Open Edge. Browse to the **Microsoft 365 admin center** and sign in as **Christie**.

1. In the Navigation menu, select **Users > Active users**.

1. In the **Active Users** list, select **Jessica Jennings**.

1. Note that you can change group membership and contact information.

1. Add a user.

   | Setting | Value |
   | --- | --- |
   | First name | Chris |
   | Last name | Breland |
   | Display Name | Chris Breland |
   | Username | chris@XXXXXX.onmicrosoft.com |
   | Password | Pa55w.rd1234 |
   | Require the user to change their password when they first sign in | No |
   | Location | Switzerland |
   | Licenses | Office 365 E5, Enterprise Mobility + Security E5 |
   | Roles | User |
   | Department | (Leave blank) |

1. In the **Active Users** list, select **Chris Breland**.

1. Delete Chris’s account.

1. Sign out of the admin center and close Edge.
