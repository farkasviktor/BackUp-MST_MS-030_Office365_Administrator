

## Module 7: Planning and configuring Exchange Online services

#### Lab A: Configuring message transport in Exchange Online

## Exercise 1: Configuring message-transport settings

### Task 1: Connect to Exchange Online in Windows PowerShell

	1. On LON-CL1, on the desktop, double-Select Windows Azure Active Directory Module for Windows PowerShell.

 Note: You might have a Windows PowerShell connection to Office 365 open from a previous lab. If so, you can use the existing connection and skip this step.

	2. In Windows PowerShell, type $cred=Get-Credential, and then press Enter.

	3. In the Windows PowerShell credential request window, in the User name box, type Admin@yourdomain.hostdomain.com.

	4. In the Password box, type Pa55w.rd, and then Select OK

	5. In Windows PowerShell, type the following command, and then press Enter:


$Session=New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell-liveid/ -Credential $cred -Authentication Basic –AllowRedirection


6. Type the following command, and then press Enter:


Import-PSSession $Session


### Task 2: Create a custom send and receive connector to enforce TLS

	1. On the taskbar, Select Microsoft Edge.

	2. In Microsoft Edge, in the search box, type https://login.microsoftonline.com, and press Enter.

	3. At the login page, sign in as Admin@yourdomain.hostdomain.com with the password Xtr3m3L@bs.

	4. To open the Office 365 admin center, Select Admin.

	5. In the Office 365 admin center, on menu on the left, in Admin centers, Select Exchange.

	6. In the Exchange admin center, Select mail flow, and then Select connectors.

	7. Select New.

	8. On the Select your mail flow scenario page, in the From box, select Office 365.

	9. In the To box, select Partner organization, and then Select Next.

	10. On the New connector page, in the Name box, type Humongous Insurance Outgoing, and then Select Next.

	11. Select Only when email messages are sent to these domains, and then Select Add.

	12. On the add domain page, type humongousinsurance.com, Select OK, and then Select Next.

	13. Select Use the MX record associated with the partner’s domain, and then Select Next.

	14. Select the Always use Transport Layer Security (TLS) to secure the connection check box, Select Issued by a trusted certificate authority (CA), and then Select Next.

	15. On the Confirm your settings page, Select Next.

	16. On the Validate this connector page, Select Add.

	17. In the Send the test email to the address box, type postmaster@humongousinsurance.com, Select OK, and then Select Validate.

	18. Wait while validation completes, and then Select Close. 

	19. On the Validation Result page, Select Save.

	20. In the Warning window, Select Yes.

 Note: Validation of mail flow will fail because the connector is to a fictitious organization. This is expected behavior for this lab.

	21. In the Exchange admin center, on the connectors tab, Select New.

	22. On the Select your mail flow scenario page, in the From box, select Partner organization.

	23. In the To box, select Office 365, and then Select Next.

	24. On the New connector page, in the Name box, type Humongous Insurance Incoming, and then Select Next.

	25. Select Use the sender’s domain, and then Select Next.

	26. Select Add, type humongousinsurance.com, Select OK, and then Select Next.

	27. Select the Reject email messages if they aren’t sent over TLS check box, and then Select Next.

	28. On the Confirm your settings page, Select Save.

### Task 3: Create transport rules

	1. On LON-CL1, in the Exchange admin center page, Select rules.

	2. Select New, and then Select Apply disclaimers.

	3. In the new rule window, in the Name box, type A. Datum Disclaimer.

	4. In the Apply this rule if box, select The recipient is located, Select Outside the organization, and then Select OK.

	5. Select Enter text.

	6. In the specify disclaimer text window, type &lt;HR&gt; If you are not the intended recipient of this message, you must delete it, and then Select OK.

	7. Select Select one.

	8. In the specify fallback action window, select Wrap, and then Select OK.

	9. In the new rule window, Select Save.

	10. If the Warning window appears, Select Yes.

	11. In Exchange admin center, Select New, and then Select Send messages to a moderator.

	12. In the new rule window, in the Name box, type Moderate Managers.

	13. In the Apply the rule if box, select The recipient is a member of, in the Select Members window, Select Managers, Select add, and then Select OK.

	14. In the Do the following box, select Forward the message for approval to, Select MOD Administrator, Select add, and then Select OK.

	15. In the new rule window, Select Save.

	16. On LON-CL2, on the taskbar, Select Microsoft Edge.

	17. In Microsoft Edge, in the search box, type https://login.microsoftonline.com, and then press Enter.

	18. Sign in as Francisco@yourdomain.hostdomain.com with the password Pa55w.rd.

	19. In Office 365, Select Mail.

	20. In the Mail window, Select New.

	21. In the To field, type [alias@outlook.com](mailto:alias@outlook.com), where [alias@outlook.com](mailto:alias@outlook.com) is the Microsoft account that you configured at the beginning of this course.

	22. In the Subject field, type Disclaimer Test.

	23. In the message body, type This message will have a disclaimer, and then Select Send.

	24. Sign in to Outlook.com, and then verify that the message has the disclaimer If you are not the intended recipient of this message, you must delete it added at the end of the message body. If the message is not in the Inbox, check the Junk folder. 

	25. In the Mail window in which you are signed is as Francisco, Select New.

	26. In the To field, type Martina.

	27. In the Subject field, type Moderation Test.

	28. In the message body, type This message requires approval by Admin, and then Select Send.

	29. On LON-CL1, Select Start, type Outlook, and then Select Outlook 2016. 

	30. Type Admin@yourdomain.hostdomain.com and Pa55w.rd in the Windows Security dialog box. 

	31. In Outlook, read the approval request, and then Select Approve.

	32. Close Outlook 2016.

### Task 4: Create a journal rule for members of the research department

	1. On LON-CL1, in the Exchange admin center, Select compliance management, Select journal rules, and then Select Select address.

	2. In the non-delivery reports window, Select Browse, Select MOD Administrator, Select OK, and then Select Save.

	3. In the Warning window, Select OK.

	4. Select New.

	5. In the new journal rule window, in the Send journal reports to box, type journal@humongousinsurance.com.

	6. In the Name box, type Development Messages.

	7. In the If the message is sent to or received from box, select A specific user or group, Select Development, Select add, and then Select OK.

	8. In the Journal the following messages box, select All messages, and then Select Save.

### Task 5: Track internal and external message delivery

	1. On LON-CL1, in the Exchange admin center, Select mail flow, and then Select message trace.

	2. Review the available search options, and then Select search.

	3. In the Message Trace results window, double-Select the message sent to alias@outlook.com.

	4. Review the information in the message, including the message events that show that the disclaimer was applied.

	5. Select Close.

	6. Double-Select the message sent from Francisco to Martina.

	7. Review the information in the message, including that the message was sent for moderation.

	8. Select Close.

	9. In the Message Trace Results window, Select Close.

 


Results: After completing the exercise, you will have configured message-transport settings.


#### Lab B: Configuring email protection and client policies

## Exercise 1: Configuring email protection

### Task 1: Configure the malware filter

	1. On LON-CL1, in the Exchange admin center, Select protection, and then Select malware filter.

	2. Select Default, and then Select Edit.

	3. In the Default window, Select settings.

	4. Under Notifications, select the Notify internal senders check box.

	5. Select the Notify administrator about undelivered messages from internal senders check box.

	6. In the Administrator email address box, type Admin@yourdomain.hostdomain.com.

	7. Select the Notify administrator about undelivered messages from external senders check box.

	8. In the Administrator email address box, type Admin@yourdomain.hostdomain.com, and then Select Save.

### Task 2: Configure the connection filter

	1. On LON-CL1, in the Exchange admin center, Select connection filter.

	2. Select Default, and then Select Edit.

	3. In the Default window, Select connection filtering.

	4. Under IP Block list, Select Add.

	5. In the add blocked IP address window, type 192.168.0.0/24, and then Select OK.

	6. Select the Enable safe list check box, and then Select Save.

### Task 3: Configure the spam filter

	1. On LON-CL1, in the Exchange admin center, Select spam filter.

	2. Select Default, and then Select Edit.

	3. In the Default window, Select spam and bulk actions.

	4. In the High confidence spam box, select Quarantine message, and then Select Save.

	5. Select Add.

	6. In the new spam filter policy window, in the Name box, type Sales spam policy.

	7. In the Spam box, select Prepend subject line with text.

	8. In the High confidence spam box, select Move message to Junk Email folder.

	9. In the Prepend subject line with this text box, type Junk:.

	10. Scroll to the bottom of the window, and under Applied To, in the If box, select The recipient is a member of, Select Sales, Select add, and then Select OK.

	11. Select Save.

### Task 4: Test the spam-filter settings (optional)

	1. Sign in to your alias@outlook.com account.

	2. Create a new message to send to kendra@Yourdomain.hostdomain.com.

	3. In the body of the message, include the text XJSC4JDBQADN1.NSBN32IDNENGTUBE-STANDARD-ANTI-UBE-TEST-EMAILC.34X, and then send the message.

	4. Create a new message to send to francisco@Yourdomain.hostdomain.com.

	5. In the body of the message, include the text XJSC4JDBQADN1.NSBN32IDNENGTUBE-STANDARD-ANTI-UBE-TEST-EMAILC.34X, and then send the message.

	6. On LON-CL1, in the Exchange admin center, Select protection, and then Select quarantine.

	7. Verify that the message sent to Francisco is in quarantine, but the message sent to Kendra is not.

	8. Select the message sent to Francisco, Select Release Message, and then Select Release selected message(s) to ALL recipients.

	9. In the Warning window, Select Yes.

	10. When processing is complete, Select Close.

	11. On LON-CL2, in Outlook on the web, verify that the message was delivered.

### Task 5: Enable Advanced Threat Protection

	1. Switch to LON-CL1 computer.

	2. In Exchange admin center, Select advanced threats, and then Select safe attachments.

	3. Select New.

	4. In the new safe attachments window, in the Name box, type Sales policy.

	5. Under Safe attachments unknown malware response, Select Replace - Block the attachments with detected malware, continue to deliver the message.

	6. Below Applied To in the If box, select The recipient is a member of.

	7. In the Select Members window, Select Sales, Select add, and then Select OK.

	8. In the new safe attachments policy window, Select Save.

	9. In the Warning window, Select OK.

 


Results: After completing this exercise, you should have configured anti-spam and antivirus settings.


  
‎ 

## Exercise 2: Configuring client access policies

### Task 1: Configure an Outlook Web App policy

	1. On LON-CL1, in the Exchange admin center, Select permissions, and then Select Outlook Web App policies.

	2. Select New.

	3. In the new Outlook Web App mailbox policy window, in the Policy name box, type Limited features.

	4. Clear the following check boxes:

		- Instant messaging

		- Text messaging

		- Unified messaging

		- LinkedIn contact sync

		- Journaling

5. Under Private computer or OWA for devices, clear the Direct file access check box, and then Select Save.

6. Select recipients, Select mailboxes, Select Kendra Sexton, and then Select Edit.

7. In the Kendra Sexton window, Select mailbox features.

8. Under Email Connectivity, Select View details.

9. In the Outlook Web App mailbox policy window, Select Browse, Select Limited features, Select OK, and then Select Save.

10. In the Kendra Sexton window, Select Save.

11. On LON-CL1, Select Start, type Outlook and then Select Outlook 2016. If prompted, type Admin@yourdomain.hostdomain.com and Pa55w.rd in the Windows Security dialog box.

12. Select New Email.

13. In the new email window, in the To box, type Kendra@yourdomain.hostdomain.com and then Select Check Names.

14. In the Subject box, type Attachment Test.

15. In the ribbon, Select Attach File, and then Select Browse This PC.

16. In the Insert File window, browse to C:\Windows\Logs\DISM, Select dism, and then Select Insert.

17. Select Send.

18. On LON-CL2, in Outlook on the web, sign out, and then sign in again as Kendra@yourdomain.hostdomain.com with the password Pa55w.rd.

19. On the Outlook page, select your time zone and Select Save.

20. Read the new Attachment Test message.

21. Select the message attachment.

22. Select OK to close the message, indicating that you do not have permission to download files.

 Note: In some cases, it may take a few minutes for the new Outlook Web App mailbox policy to take effect.

### Task 2: Configure mobile-device access

	1. On LON-CL1, in the Exchange admin center, Select mobile, and then Select mobile device access.

	2. Select edit.

	3. In the Exchange ActiveSync access settings window, Select Quarantine – Let me decide to block or allow later.

	4. Under Quarantine Notification Email Messages, Select Add, Select MOD Administrator, Select add, and then Select OK.

	5. In the Exchange ActiveSync access settings window, Select Save.

### Task 3: Configure a mailbox policy for mobile devices

	1. On LON-CL1, in the Exchange admin center, on the mobile menu, Select mobile device mailbox policies.

	2. Select Default (default), and then Select Edit.

	3. In the Default window, Select security, and then select the Require a password check box.

	4. Select the Allow simple passwords check box.

	5. Select the Minimum password length check box, enter a value of 4, and then Select Save.

### Task 4: Validate mobile-device management policies (optional)

	1. On your mobile device, add a new ActiveSync account for Francisco Chaves.

	2. If Autodiscover does not detect the server name, enter outlook.office365.com.

	3. Your device will be placed into quarantine, and you must approve the device before you can send and receive messages.

	4. After you configure the Exchange ActiveSync account, the security settings from the mobile-device mailbox policy will apply, and you may be prompted to create a password on your device.

	5. When you finish your testing, you can delete the account from your mobile device.

	6. Leave the virtual machines running for the next lab.

 


Results: After completing this exercise, you should have configured client access policies.


 
