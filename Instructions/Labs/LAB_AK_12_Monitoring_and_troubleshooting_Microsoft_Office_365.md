## Lab 12: Monitoring and troubleshooting Microsoft Office 365

### Exercise 1: Monitor Office 365

#### Task 1: Send an email to a non-existent domain

1.Open **Outlook**, signed in as **Amy**.

1. Send an email to **user@alt.none** with a subject of **Test email to non-existent domain**.

1. Open the “Delivery has failed” message.

1. Copy the grey body text (from “Diagnostic information for administrators” to the end) to the clipboard.

1. Open Edge. Browse to **https://testconnectivity.microsoft.com**.

1. Select **Message Analyzer**.

1. Paste the text, select **Analyze headers**.

1. Review the results, in particular the first header, that contains "DNS domain … does not exist."

#### Task 2: Send an email to a non-existent user

1. Send an email to **difflop1248999@outlook.com** with a subject of **Test email to non-existent user**.

1. Open the “Delivery has failed” message.

1. Copy the grey body text (from “Diagnostic information for administrators” to the end) to the clipboard.

1. Open Edge. Browse to **https://testconnectivity.microsoft.com**.

1. Select **Message Analyzer**.

1. Paste the text, select **Analyze headers**.

1. Review the results, in particular the first header, that contains “Mailbox unavailable.”

#### Task 3: Analyse Mail Flow using the portal

1. Open Edge. Browse to the **Office 365 Security & Compliance Center** and sign in as the tenant owner.

   At the time of writing, Message Trace is also available in the Modern Exchange admin center, but not in the Microsoft 365 Compliance center or the Microsoft 365 Security center.

1. In the navigation pane, select **Mail flow > Message trace** then select **Start a trace**.

   | Setting | Value |
   | --- | --- |
   | By these people | Amy |
   | To these people | All recipients |
   | Within this time range | In the last 6 hours |

1. Review the message trace search results. In particular, review the two failed messages from Amy.

   The message detail pane does not allow you to copy the message headers in the same way Outlook does.

1. Select **Export results > Export loaded results**.

1. Open the downloaded csv file. Review the (limited) information.

#### Task 4: Analyse Mail Flow using PowerShell.

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

1. View the message trace.

   ```PowerShell
   Get-MessageTrace -Page 1 -PageSize 10
   ```

1. View message trace details.

   ```PowerShell
   Get-MessageTrace -Page 1 -PageSize 10 | fl *address, *id, subject
   ```

   Copy the MessageTraceId of the “Test email to non-existent user” message.

   ```PowerShell
   Get-MessageTraceDetail -MessageTraceId "<paste>" -RecipientAddress "difflop1248999@outlook.com"
   ```

### Exercise 2: Monitor service health

#### Task 1: View Office 365 service health

1. Open Edge. Browse to the **Microsoft 365 admin center** and sign in as the tenant owner.

1. In the Navigation menu, select **Health > Service health**.

1. Review the content.

1. In the Navigation menu, select **Health > Message center**.

1. Review the content.

1. In the Navigation menu, select **Reports > Usage**.

1. Review the content. Note the “Date as of” - these reports are 48 hours behind the current time.

1. In Edge, open a new tab. Browse to the **Microsoft 365 security center**.

1. In the Navigation menu, select **Reports**.

1. Review the content.

1. In Edge, open a new tab. Browse to the **Microsoft 365 Compliance Center**.

1. In the Navigation menu, select **Reports**.

1. Review the content.
