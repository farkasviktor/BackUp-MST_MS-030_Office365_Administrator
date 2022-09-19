

## Module 12: Monitoring and troubleshooting Microsoft Office 365

#### Lab: Monitoring and troubleshooting Office 365

## Exercise 1: Monitoring Office 365

### Task 1: Send an email to a nonexistent domain

	1. On LON-CL1, on the taskbar, Select Microsoft Edge.

	2. Browse to https://portal.office.com/, and then sign in as Admin@M365xyyxxxxxx.hostdomain.com by using the password Xtr3m3L@bs.

	3. Select Mail, and then Select New.

	4. In the To text box, type user@alt.none.

	5. Enter a subject and some body text, and then Select Send.

### Task 2: Track mail delivery

	1. Wait for the delivery failure message to appear.

	2. Note the reason for the failure (“The domain name in the email address is incorrect.”).

	3. Select the body text of the message, including the phrase “Generating server” down to “X-OriginatorOrg: M365xyyxxxxx.hostdomain.com” and then press Ctrl+C to copy it to the Clipboard.

	4. In Microsoft Edge, press Ctrl+T to create a new tab.

	5. In the new tab, browse to testconnectivity.microsoft.com.

	6. On the Microsoft Remote Connectivity Analyzer page, Select the Message Analyzer tab.

	7. Under Message Header Analyzer, paste the message, and then Select Analyze headers.

	8. Note the diagnostic information and the time taken for the message to be rejected.

	9. Select Clear to reset the Message Header Analyzer.

### Task 3: Send an email to a nonexistent user

	1. In Microsoft Edge, Select Admin’s Mail tab.

	2. Select New, and then in the To text box, type difflop48999@outlook.com.

	3. Enter a subject and some body text, and then Select Send.

### Task 4: Track mail delivery

	1. Wait for the delivery failure message to appear. 

	2. Note the reason for the “550 Requested action not taken: mailbox unavailable” failure.

	3. Select the body text of the message including the phrase “Generating server” down to “X-OriginatorOrg: M365xyyxxxxx.hostdomain.com” and then press Ctrl+C to copy it to the Clipboard.

	4. In Microsoft Edge, switch to the Microsoft Remote Connectivity Analyzer tab.

	5. On the Microsoft Remote Connectivity Analyzer page, ensure that you are on the Message Analyzer tab.

	6. Under Message Header Analyzer, paste the message, and then Select Analyze headers.

	7. Note the diagnostic information and the time taken for the message to be rejected.

	8. Close the Microsoft Remote Connectivity Analyzer page.

### Task 5: Analyze mail flow

	1. On Admin’s Mail tab in the Microsoft Office 365 portal, Select the Apps launcher in the top task bar, and Select Admin.

	2. Access the new Office 365 admin center, Select Admin centers, Select Exchange, and then Select mail flow.

	3. In mail flow, Select message trace.

	4. In message trace, next to Sender, Select add sender.

	5. In the Select Members dialog box, Select Admin, Select add, and then Select OK.

	6. Under Date range, select Past 24 hours.

	7. Under Delivery status, select Failed, and then Select search. Note the two messages.

	8. Double-Select each message to view the sender, recipient, message size, ID, and IP address information.

	9. Note the differences between the message processing events: Receive, Submit, Spam Diagnostics, and Fail for the nonexistent domain, and Submit, Receive, Spam Diagnostics, and Fail for the nonexistent user.

	10. Close the Message Trace window.

 


Results: After completing this exercise, you should have used the Message Header Analyzer to identify why email failed to deliver.


  
‎ 

## Exercise 2: Monitoring service health and analyzing reports

### Task 1: View Office 365 service health

	1. In the new Office 365 admin center, Select Home.

	2. On the Home page, in the left menu, select Health, and then Select Service health. 

	3. Select Go to the v2 Service Health page link.

	4. Select Exchange Online in the left column.

	5. On the right side of the page, Select View history.

	6. Select any entry in the calendar that is colored yellow to see further details about incident. Details appear below the calendar.

	7. Select the Home icon on the menu to the left.

### Task 2: View reports in the Office 365 admin center

	1. In the Office 365 admin center, on the Home page, Select Go to the old admin center to go to the previous Office 365 admin center. 

	2. In the Office 365 admin center, Select REPORTS.

 Note: At the time of writing this course, reports were not available in the new Office 365 admin center.

	3. On the Reports page, in the Mail section, Select Mailbox usage.

 Note: There might be little or no data shown because there is not much mailbox usage in the lab environment.

	4. Select the back arrow.

	5. On the Reports page, in the Protection section, Select Sent and received mail, and then Select View table.

	6. Close the table view.

 Note: There might be little or no data shown because there is not much mailbox usage in the lab environment.

	7. Close the open window.

	8. On the Reports page, in the Protection section, Select Malware detections.

	9. Close the open window.

	10. On the Reports page, in the Protection section, Select Spam detections.

	11. Close the open window.

	12. Keep the virtual machines running for the next lab.

 


Results: After completing this exercise, you should have monitored the health of Office 365 services and viewed reports in the Office 365 admin center.
