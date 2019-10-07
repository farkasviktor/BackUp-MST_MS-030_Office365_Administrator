

## Module 9: Planning and configuring SharePoint Online

#### Lab: Configuring SharePoint Online

## Exercise 1: Configuring SharePoint Online settings

### Task 1: Configure settings

	1. Ensure you are signed in to the 20347A-LON-CL1 virtual machine as Admin with the password of Pa55w.rd.

	2. In LON-CL1, Select the desktop, on the taskbar, Select Microsoft Edge, and then browse to https://portal.office.com.

	3. Sign in as Admin@M365xyyxxxxx.hostdomain.com (where yyxxxxx is your unique M365x.com number) with the password of Xtr3m3L@bs.

	4. In the Office 365 admin center, Select Admin centers, and then Select SharePoint.

	5. On the leftmost side, Select settings.

	6. Under Site Collection Storage Management, Select Automatic.

	7. Scroll down to Enterprise Social Collaboration.

	8. Select Use Yammer.com service.

	9. Select OK.

	10. On the leftmost side, Select sharing.

	11. Verify that Allow sharing to authenticated external users and using anonymous access links is selected, and then Select OK.

### Task 2: Configure user profiles

	1. On the leftmost side, Select user profiles.

	2. Under people, Select Manage User Profiles. 

	3. In the Find profiles dialog box, type Ada, and then Select Find.

	4. In the result window, in the drop-down list, Select Ada.

	5. Select edit my profile, and in the Manager box, type Admin.

	6. Select the check names field and verify that the field displays MOD Administrator.

	7. In the right corner, Select Save and Close.

	8. On the left side, Select user profiles.

	9. Under My Site settings, Select Setup My Sites.

	10. Scroll down to My Site Cleanup.

	11. In the secondary owner list, type Admin, and then Select the Check names icon.

	12. Scroll down, and then Select OK.

### Task 3: Configure apps

	1. On the leftmost side, Select apps, and then Select Configure Store Settings.

	2. In the Apps for Office from the Store window, Select No to disable apps from starting when documents are opened in the browser.

	3. Select OK, and then close the browser.

 


Results: After completing this exercise, you should have configured SharePoint Online service settings.


  
‎ 

## Exercise 2: Creating and configuring SharePoint Online site collections

### Task 1: Create a site collection using the SharePoint admin center

	1. Open Microsoft Edge and sign in to https://portal.office.com with the user name Admin@M365xyyxxxxx.hostdomain.com, and the password of Xtr3m3L@bs.

	2. In the Office 365 admin center, on the left side menu, Select Admin centers, and then Select SharePoint.

	3. In the leftmost side, Select Site collections.

	4. On the Site Collections ribbon, Select New, and then Select Private Site Collection.

	5. In the new site collection dialog box, in the Title dialog box, type marketing, in the empty text box, type marketing, and then in the administrator list, type Admin and then Select the Check Names icon. Leave the other settings as suggested. To confirm, Select OK.

 Note: SharePoint Online provisions the new marketing site. This process can take a few minutes.

	6. After marketing is created, select the https://M365xyyxxxxx.sharepoint.com/sites/marketing check box. 

 Note: It can take a few minutes until the Sharing menu on the ribbon is active. You can speed this up by refreshing the page by pressing the F5 key.

	7. When the marketing site is selected, on the ribbon, Select Sharing.

	8. In the Sharing dialog box, select Allow sharing with all external users, and by using anonymous access links, and then Select Save.

 Note: The site settings changes to allow external user sharing. This process is usually done within one minute. Now, external user sharing is enabled and you can use it for this marketing site.

### Task 2: Create a site collection using Windows PowerShell

	1. To install the SharePoint Online Management Shell, you must first download it from the Microsoft Download Center. To do so, open a new Microsoft Edge tab and browse to http://aka.ms/f04q5o.

	2. On the SharePoint Online Management Shell download page, in the Select Language drop-down box, select your appropriate language, and then Select Download.

	3. On the Choose the download you want page, select the check box for the 64-bit version and for the most current file. Select Next. 

	4. If a message about pop-ups appears, Select Allow once.

	5. In the Internet Explorer dialog box asking whether you want to run or save the file, Select Save and then Select Run.

	6. On the SharePoint Online Management Shell Setup page, select the I accept the terms in the License Agreement check box, and then Select Install.

	7. If a User Account Control dialog box appears, Select Yes.

	8. When the installation completes, Select Finish.

	9. Select Start, type sharep, and right-Select SharePoint Online Management Shell, and then Select Run as administrator.

	10. In the User Account Control dialog box, Select Yes.

	11. At the command prompt, type the following command, and then press Enter (where yyxxxxx is your unique M365x domain name):


Connect-SPOService –Url https://M365xyyxxxxx-admin.sharepoint.com –credential Admin@M365xyyxxxxx.hostdomain.com


12. In the Enter your credentials dialog box, in the Password box, type Xtr3m3L@bs, and then Select OK.

13. At the command prompt, type the following command, and then press Enter:


New-SPOSite -Url https://M365xyyxxxxx.sharepoint.com/sites/AcctsProj -Owner Admin@M365xyyxxxxx.hostdomain.com -StorageQuota 500 -NoWait -Template PROJECTSITE#0 –Title “Accounts Project”


14. Close the Windows PowerShell window.

### Task 3: Configure permissions on the site collections

	1. In LON-CL1, open Microsoft Edge, in the top-right corner, Select the ellipsis, and then Select New InPrivate Window.

	2. Browse to https://portal.office.com.

	3. Sign in as Admin@M365xyyxxxxx.hostdomain.com, with the password of Xtr3m3L@bs. 

	4. In the Office 365 admin center, Select Admin, and then Select SharePoint.

	5. On the leftmost side, Select Site collections.

	6. Select the https://M365xyyxxxxx.sharepoint.com/sites/marketing check box.

	7. On the ribbon, Select owners, and then Select Manage Administrators.

	8. In the Site Collection Administrators text box, type Ada, Select the Check Names icon, and then Select OK.

	9. Open another InPrivate window, browse to https://M365xyyxxxxx.sharepoint.com/sites/marketing, and sign in as Ada@M365xyyxxxxx.hostdomain.com, with the password of Xtr3m3L@bs.

	10. On the upper-right corner, Select the Settings icon (the wheel icon), and then navigate to site settings.

	11. Under Users and Permissions, Select Site collection administrators to open it.

	12. Verify that Ada Russell appears.

	13. Close the Microsoft Edge window.

### Task 4: Verify access to the site collections

	1. In LON-CL1, open Microsoft Edge.

	2. Browse to https://M365xyyxxxxx.hostdomain.com/sites/marketing.

	3. Sign in as Beth@M365xyyxxxxx.hostdomain.com, with the password of Xtr3m3L@bs. 

 Note: You need permission to access this site, and you need to send an access request for permission to view the site.

	4. In the You need permission to access this site dialog box, type Please enable Beth’s access to this site, and then Select Request Access.

	5. Close Microsoft Edge, and then reopen it.

	6. Browse to https://M365xyyxxxx.sharepoint.com/sites/marketing.

	7. Sign in as Admin@M365xyyxxxxx.hostdomain.com with the password of Xtr3m3L@bs.

	8. In the top-right corner, Select the Settings icon (the wheel icon), and then Select Site settings.

	9. Under User and Permissions, Select Site permissions.

	10. Select Show access requests and invitations.

	11. Verify that Beth’s request is listed, and Select Approve.

	12. Select Site Settings, and then Select Site permissions.

	13. Select marketing Members.

	14. Verify that Beth’s account is listed. 

	15. Select New, and then Select Add Users.

	16. In the text box at the top, type Perry, and then Select Perry Brill.

	17. Select Share.

	18. Close Microsoft Edge.

	19. Open Microsoft Edge and connect to https://M365xyyxxxxx.sharepoint.com/sites/marketing.

	20. Sign in as Beth@M365xyyxxxxx.hostdomain.com, with the password of Xtr3m3L@bs. 

	21. Verify that you can access the site.

	22. Close Microsoft Edge, and then reopen it.

	23. Browse to https://M365xyyxxxxx.sharepoint.com/sites/marketing.

	24. Sign in as Perry@M365xyyxxxxx.hostdomain.com, with the password of Xtr3m3L@bs. 

	25. Verify that you can access the site.

 


Results: After completing this exercise, you should have created and configured SharePoint Online site collections.


  
‎ 

## Exercise 3: Configuring and verifying external user sharing

### Task 1: Configure global settings for external user sharing

	1. In LON-CL1, open Microsoft Edge.

	2. Browse to https://portal.office.com.

	3. Sign in as Admin@M365xyyxxxxx.hostdomain.com, with the password of Xtr3m3L@bs. 

	4. In the Office 365 admin center, Select Admin, and then Select SharePoint.

	5. On the leftmost side, Select sharing.

	6. Select Allow sharing to authenticated users and anonymous access links, and then Select OK.

### Task 2: Configure a site collection for external user sharing

	1. In Microsoft Edge, Select Site Collections.

	2. Select the https://M365xyyxxxxx.sharepoint.com/sites/AcctsProj check box.

	3. On the ribbon, in the Manage section, Select Sharing.

	4. In the Sharing dialog box, Select Allow sharing with all external users, and by using anonymous access links.

	5. Select Save.

	6. Wait for the operation to complete, which might take about 5 minutes.

	7. Close Microsoft Edge.

	8. Open Microsoft Edge and browse to https://M365xyyxxxxx.sharepoint.com/sites/AcctsProj.

	9. Sign in as Admin@M365xyyxxxxx.hostdomain.com with the password of Xtr3m3L@bs.

	10. In the top-right corner, Select SHARE.

	11. In the Share ‘Accounts Project’ dialog box, type in the email address of the Microsoft account you used to set up Office 365.

	12. In the text box, type You can now access this shared site on M365x Publishing.

	13. Select Share.

	14. Browse to https://M365xyyxxxxx.sharepoint.com/sites/marketing

	15. In the left navigation pane, Select Documents.

	16. Select New, and then Select Word document.

	17. In the Word Online window, type some text, and then wait to check if Saved appears in the document title, and then Select the marketing link. 

	18. In the document list, Select the ellipsis button (…) next to the document you created, and then Select Share.

	19. Select Get a link, and then select Edit link – no sign-in required, and Select Create.

	20. Select the link, right-Select it, and then Select Copy and, if prompted Select Allow.

	21. Select Close.

	22. In the SharePoint Online window, Select the apps icon, and then Select Mail.

	23. If prompted, select your language and time zone, and then Select Save.

	24. Select New.

	25. In the To box, type the email address for your Microsoft Live account, and then in the Subject box, type Shared Document.

	26. In the message box, right-Select, and then Select Paste.

	27. Select SEND.

	28. Close Microsoft Edge.

### Task 3: Verify external user sharing

	1. Open Microsoft Edge and browse to https://outlook.com 

	2. Sign in with your Microsoft Live account.

 Note: The Inbox should show two emails from Microsoft Online Services Team. If the messages are not in the Inbox, look in the Junk folder. 

3. Open the message that has the subject: MOD Administrator wants to share Accounts Projects. 

4. Select the Accounts Project link in the email.

5. Select Microsoft Account. Verify that you can access the site. 

6. Close the browser tab. In your inbox, open the second invitation email message with the subject of MOD Administrator wants to share the document.

7. Select the Document link.

 Note: You are redirected directly to the Word Document. Word Online opens and shows the document.

	8. Verify that you can access the Word document and then Select Edit in Browser. 

	9. Add some text in this document. 

	10. Close Microsoft Edge.

	11. Leave the virtual machines running for the next lab.
Results: After completing this exercise, you should have configured a new site collection for external user sharing, and you should have shared a site and a document with external users.


 
