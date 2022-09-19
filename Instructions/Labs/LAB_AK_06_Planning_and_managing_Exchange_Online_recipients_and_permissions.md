## Lab 6: Managing Exchange Online recipients and permissions

### Exercise 1: Configure Exchange Online recipients

#### Task 1: Use the Exchange admin center

1. On **LON-CL1**, signed in as **ADATUM\Administrator**.

1. Open Edge. Browse to the **Exchange admin center** and sign in as the tenant owner.

1. In the Navigation menu, select **recipients** then select **mailboxes**.

   Note the mailboxes for the licensed users.

1. Select **groups**.

   Note the default groups.

1. Select the **down arrow** button next to **New Microsoft 365 group**.

   Note that the Exchange admin center allows you to create four types of group: Microsoft 365, distribution, Mail-enabled security, and dynamic distribution.

#### Task 2: Connect to Exchange Online with Windows PowerShell

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

1. Verify connectivity.

   ```PowerShell
   Get-AcceptedDomain
   Get-Mailbox
   ```

#### Task 3: Create groups and assign members

1. Create distribution groups.

   ```PowerShell
   New-DistributionGroup -Name "IT2" -Members holly -DisplayName "IT 2"
   New-DistributionGroup -Name "Development" -Members catherine, tameka -DisplayName "Development"
   New-DistributionGroup -Name "Sales" -Members lindsey, christie -DisplayName "Sales"   
   Get-DistributionGroup
   ```

#### Task 4: Create resource mailboxes

1. Create resource mailboxes.

   ```PowerShell
   New-Mailbox -Name "Conference Room" -DisplayName "Conference Room" -Room -Alias "conferenceroom"
   Set-Mailbox -Identity "Conference Room" -ResourceCapacity 25
   ```

   ```PowerShell
   New-Mailbox -Name "Demonstration Laptop" -DisplayName "Demonstration Laptop" -Equipment -Alias "demonstrationlaptop"
   ```

1. Set auto-accept.

   ```PowerShell
   Get-Mailbox | ft name, recipienttype*
   ```

   ```PowerShell
   Get-Mailbox -RecipientTypeDetails RoomMailbox | Set-CalendarProcessing -AutomateProcessing AutoAccept
   ```

   ```PowerShell
   Get-Mailbox -RecipientTypeDetails EquipmentMailbox | Set-CalendarProcessing -AutomateProcessing AutoAccept
   ```

#### Task 5: Test resource mailboxes

1. On **LON-CL3**, signed in as **ADATUM\Administrator**.

1. Open **Outlook**, signed in as **Amy**.

1. Create a meeting. Invite Francisco, Demonstration Laptop and Conference Room.

1. Wait for the “accepted” messages from Demonstration Laptop and Conference Room.

1. On **LON-CL4**, signed in as **ADATUM\Administrator**.

1. Open **Outlook**, signed in as **Sallie**.

1. Create a meeting at the same time as Amy’s meeting. Select the Scheduling Assistant tab.

   Invite Francisco, Demonstration Laptop and Conference Room. Note that Francisco’s time shows as Tentative and Demonstration Laptop and Conference Room show as Busy.

   Send the meeting request.

1. Wait for the “declined” messages from Demonstration Laptop and Conference Room.

### Exercise 2: Configure role-based access control

#### Task 1: Assign users to built-in role groups

1. On **LON-CL1**, signed in as **ADATUM\Administrator**.

1. Switch to Edge connected to the **Exchange admin center**.

1. In the Navigation menu, select **permissions** then select **admin roles**.

1. Select **Organization Management**, then select **Edit** (the pencil icon).

1. Under **Members**, Select **Add** (the plus icon).

1. Add **Holly**.

#### Task 2: Create a new admin role and assign a user to it

1. Switch to PowerShell ISE or PowerShell connected to Exchange Online.

1. Enable customization of the Exchange Online tenant.

   ```PowerShell
   Enable-OrganizationCustomization
   ```

1. Create a new role group and add a member.

   ```PowerShell
   New-RoleGroup -Name "Branch Office Admins" -Roles "Mail Recipients", "Distribution Groups", "Move Mailboxes", "Mail Recipient Creation"
   Add-RoleGroupMember "Branch Office Admins" -Member Christie
   ```

1. Switch to Edge connected to the Exchange admin center.

1. In the Navigation menu, select **permissions** then select **admin roles**. 

1. Select **Refresh** (the circled arrows icon).

1. Verify that Branch Office Admins is present.
