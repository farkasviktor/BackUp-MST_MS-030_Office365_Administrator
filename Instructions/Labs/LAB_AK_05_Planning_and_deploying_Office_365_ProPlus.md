

## Module 5: Planning and deploying Office 365 ProPlus

#### Lab: Managing Office 365 ProPlus installations

## Exercise 1: Preparing an Office 365 ProPlus managed installation

### Task 1: Download the Office 365 deployment tool

	1. On LON-CL1, on the taskbar, Select File Explorer.

	2. In File Explorer, Select Local Disk (C:) in the left navigation pane

	3. In File Explorer, Select the Home tab, and then Select New Folder.

	4. Type Office16, and then press Enter.

	5. In File Explorer, right-Select Office16, Select Share with, and then Select Specific people.

	6. In the File Sharing dialog box, Select the drop-down list box, select Everyone from the list, Select Add, and then Select Share.

	7. In the File Sharing dialog box, Select Done. 

	8. From the taskbar, open the Microsoft Edge browser.

	9. In the address bar, type https://portal.office.com, and then press Enter.

	10. Sign in as Admin@M365xYYXXXXX.hostdomain.com, with the password Xtr3m3L@bs.

	11. On the Office 365 home page, Select Admin. Select Go to the old admin center to switch to previous Office365 admin center.

	12. In the Office 365 admin center, in the left panel, Select SERVICE SETTINGS, and then Select User software.

	13. Under the Manually deploy user software area, Select Learn how to download and deploy software.

	14. In the Manually download and install the Office apps by using the Office Deployment Tool section, Select the Office Deployment Tool (Office 2016 version) link to open the Office Deployment Tool download page.

	15. On the download page, expand Details, System Requirements, and Install Instructions.

	16. Read and familiarize yourself with each section. You can mark this page as a favorite to refer to later.

	17. Select Download and notice the information bar at the bottom of the browser.

	18. Once the download is completed, Select Run.

	19. In the User Account Control dialog box, Select Yes.

	20. Accept the license agreement and Select Continue. 

	21. Browse to the Office16 folder on This PC’s C: drive.

	22. Select OK. You should see that the files were extracted successfully. Select OK.

	23. Navigate to the Office16 folder with File Explorer. You should see two files in the newly created Office Deployment Tool folder named configuration and setup.

### Task 2: Modify an Office 365 ProPlus installation

	1. In this step, you will back up the Office 16 configuration.xml file and then open it so that you can edit it in the next step. To do this, perform the following steps:

		- In File Explorer, double-Select C:\Office16. 

		-  Right-Select configuration.xml, and Select Copy. Right Select again and Select Paste. 

		- Right-Select the configuration.xml file, Select Open with, and then Select Notepad. 

2. In Notepad, edit the first Add line after <Configuration> to read <Add SourcePath=”\\LON-CL1\Office16\” OfficeClientEdition=”32” Branch=”Current”>.

3. In Notepad, remove all the remaining comment codes (lines that start with &lt;!-- and end with --&gt;).

4. Comment out Microsoft Visio with the &lt;!-- --&gt; code to make the download quicker, by replacing this code:


</Product>

<Product ID="VisioProRetail">

<Language ID="en-us" />

</Product>


with this code:


</Product>


&lt;!--


<Product ID="VisioProRetail">

<Language ID="en-us" />

</Product>


--&gt;


5. Save the file as AdatumConfiguration.xml.

6. Switch to File Explorer (you should still be in the Office16 folder), press Shift, right-Select any white space below the file list, and then Select Open command window here. 

7. At the command prompt, type the following command, and then press Enter:


Setup /?


8. Note the Office Deployment Tool command-line options. 

9. At the command prompt, type the following command, and then press Enter:


setup.exe /download \\LON-CL1\Office16\AdatumConfiguration.xml


10. In the User Account Control window, Select Yes.

11. The download will take several minutes to complete.

12. Switch to File Explorer, and verify that the download has started in the Office16 folder. You can continue with the next task and leave the download in the background.

 


Results: You will have downloaded a copy of the Microsoft Office 365 ProPlus install for managed deployment to a shared folder. You will also download and install the Office Deployment Tool on the same machine.


  
‎ 

## Exercise 2: Managing user-driven Office 365 ProPlus installations

### Task 1: Managing user rights to install Office 365 ProPlus

	1. On LON-CL1, if required, sign in to Office365 admin center as Admin@M365xyyxxxxx.hostdomain.com with the password of Xtr3m3L@bs.

	2. Connect to the new Office 365 admin center. 

	3. On the Office 365 home page, Select Admin.

	4. In the Office 365 admin center, Select Users.

	5. Select Abbi Skinner, and then next to Product licenses, Select Edit.

	6. Under Set user location, select United Kingdom, and then enable Office 365 Enterprise E5.

	7. Set the Office 365 ProPlus option to Off, Select Save, and then Select Close twice.

	8. In the Office 365 admin center, under Active users, Select Beth Burke.

	9. Beside Product licenses, Select Edit.

	10. Under Location, select United Kingdom, and then enable Office 365 Enterprise E5.

	11. Verify that Beth has permission to use all features.

	12. Select Save, and then Select Close twice.

	13. Repeat steps 8 through 12 for Cai Chu. 

	14. In the Office 365 admin center, Select Home icon.

	15. Select Software download settings.

	16. In the Software for PC section, under 2016 version, turn off all options. 

	17. Select Save, and then Close.

	18. On the Admin page, Select MOD Adminsitrator’s profile photo icon in the top right of the screen, and then Select Sign Out.

	19. On the Sign in page, at https://portal.office.com, sign in as abbi@M365xyyxxxxx.hostdomain.com, using the password Xtr3m3L@bs.

	20. On the Default Landing page, Select the small Gear icon in the top- right corner, and then Select the Office 365 option.

	21. On the Office 365 settings page, Select Software.

 Note: Because this user is not licensed for Office 365 ProPlus, Office 2016 is not available for download.

	22. Close and reopen Microsoft Edge and connect to https://portal.office.com.

	23. On the Sign in page, in the Name box, type beth@M365xyyxxxxx.hostdomain.com.

	24. In the Password box, type Xtr3m3L@bs, and then Select Sign in.

	25. On the default landing page, Select the small Gear icon in the top-right corner, and then Select Office 365.

	26. On the Settings page, Select Software.

 Note: This user has a license, but Teams and Office 2016 are not available for download because Admin disabled Office download. Select Phone &amp; tablet. Verify that Phone and tablet apps are available.

	27. Close Microsoft Edge.

	28. Open Microsoft Edge.

	29. In the address bar, type https://portal.office.com, and then press Enter.

	30. Sign in as Admin@M365xyyxxxxx.hostdomain.com.

	31. Select Admin on the Office 365 home page.

	32. In the Office 365 admin center, Select Home.

	33. Select Software download settings.

	34. Next to the 2016 version, set the value to On. Verify that Office and Teams are both set to on, and Select Save. 

	35. Select Close. 

	36. In Microsoft Edge, on the User Software page, Select MOD Administrator profile photo icon, and then Select Sign out.

 Note: Instead of signing out your admin user every time, you can Select the Microsoft Edge browser ellipse menu (…) at the top right of the browser and open a New InPrivate window. This will allow you to have two sessions at a time open

	37. Switch to LON-CL3. Verify that you are signed in as Beth.

	38. Open Microsoft Edge.

	39. In the address bar, type https://portal.office.com, and then press Enter.

	40. On the Sign in page, in the Name box, type beth@M365xYYXXXXX.hostdomain.com.

	41. In the Password box, type Xtr3m3L@bs, and then Select Sign in. 

	42. On the Office 365 home page page, Select the small Gear icon in the top-right corner, and then Select Office 365.

	43. On the Settings page, Select Software.

 Note: This user has a license, and Office 2016 is now available for download.

	44. Verify that Office and Teams desktop software are available to install.

	45. Do not install, but notice that this user can now install the 32-bit version of Office 365 ProPlus and select which language they want to install. They must Select Advanced to turn on the 64-bit version option.

	46. Note also that Phone and tablet apps are available from the left menu. 

	47. Leave this page open and continue to the next lab to perform the user-driven installation.

### Task 2: Installing Office 365 ProPlus from the Office 365 portal

	1. On LON-CL3, if needed, open Microsoft Edge and sign into Office 365 portal at portal.office.com, with the username beth@M365xyyyxxxxx.hostdomain.com, Select Office365 Settings in upper right corner and then Select Software.

	2. In the Language section, select the language to install from the drop-down menu.

	3. Leave 32-bit (recommended) selected.

	4. Select Install.

	5. In the Microsoft Edge notification bar, Select Save, and then Select Run.

	6. If the User Account Control dialog box appears, type Adatum\Admin in the user name box, in the Password box, type Xtr3m3L@bs, and then Select Yes.

	7. On the taskbar, Select the Office icon, and note the status of the download.

 Note: It will take several minutes to complete, but applications are now available.

	8. Select Close when the wizard finishes.

	9. Go to the Start screen.

	10. On the Start screen, Select Word 2016. On the first things first window Select Accept.

	11. In the top-right corner, if no one is signed in, sign in as Beth@M365xYYXXXXX.hostdomain.com, with the password Xtr3m3L@bs, by Selecting the link Sign in to get most out of office.

	12. Once signed in, your subscription license is activated. At the top right, under Beth Burke, Select Switch account.

	13. Select SIGN OUT, and then Select Sign out next to Beth’s name.

	14. Select Yes in the Remove Account dialog box.

	15. At the top right, Select Sign in to get the most out of Office.

	16. On the Sign in page, in the E-mail address box, type Admin@M365xYYXXXXX.hostdomain.com, and then Select Next.

	17. On the Sign in page, in the Password box, type Xtr3m3L@bs, and then Select Sign in.

	18. Select Blank document.

	19. Type some text.

	20. Select File, then Select Save.

	21. Select Sites – A. Datum and Select A. Datum in the right pane.

	22. Double-Select the Documents folder and then save the file with the name Meeting Agenda. 

	23. Select Save. You might see a streaming features message.

	24. Close Word. 

	25. Switch back to Beth Burke’s Office 365 session in Microsoft Edge.

	26. In the top-right corner, Select the Settings icon, and then Select Office 365 settings.

	27. On the Office 365 settings page, Select Software.

	28. Note that you now have a new section at the top of the page where you can manage Office 365 installs.

	29. Select Tools & Add-ins.

### Task 3: Managing office licenses

	1. On LON-CL3, sign out of Beth’s account on the Office 365 page. 

	2. Sign back in as MOD Administrator with the username Admin@M365xYYXXXXX.hostdomain.com. 

	3. In the Password box, type Xtr3m3L@bs, and then Select Sign in.

	4. On the Office 365 home page, Select Admin. 

	5. In the Office 365 admin center, Select Users, and then Select Beth Burke.

	6. In the right pane, under Product licenses, Select Edit. 

	7. Under Office 365 Enterprise E5, set the Office 365 ProPlus option to Off to remove the license from Beth’s account, Select Save, and then Select Close twice.

	8. In Microsoft Edge, at the top right, Select the Profile photo icon for MOD Administrator and then Select Sign out.

	9. On the Sign in page, type Beth@M365xYYXXXXX.hostdomain.com.

	10. In the Password box, type Xtr3m3L@bs, and then Select Sign in.

	11. In the top-right corner, Select the Settings icon, and then Select Office 365.

	12. On the Settings page, Select Software.

	13. Note that the Office installation is no longer listed, as this user no longer has an active license (although software is available).

 Note: The Office 365 ProPlus applications will still be available to Beth on any machine on which she already installed them, but within 30 days, they will drop into low-functionality mode. This means she will only be able to read and print documents.

### Task 4: Reactivating Office 365 ProPlus

	1. Sign out of the Office 365 page, and sign back in as Admin@M365xYYXXXXX.hostdomain.com. 

	2. In the Password box, type Xtr3m3L@bs, and then Select Sign in.

	3. On the Office 365 home page, Select the Admin tile. 

	4. In the Office 365 admin center, Select Users, and then Select Beth Burke.

	5. In the right pane, under Product licenses, Select Edit. 

	6. Under Office 365 Enterprise E5, set the Office 365 ProPlus option to On, Select Save, and then Select Close twice.

	7. Close Microsoft Edge.

 


Results: When completed, you should be able to activate Office 365 ProPlus for self-service installations. You should also be able to set licensing options correctly for end users so that deployment and installation is possible.


## Exercise 3: Managing centralized Office 365 ProPlus installations

### Task 1: Configure a Group Policy Object (GPO) to distribute the custom installation

	1. Switch to LON-DC1 and connect as Adatum\administrator, with the password Pa55w.rd.

	2. On LON-DC1, in Server Manager, Select Tools, and then Select Active Directory Users and Computers.

	3. In the console tree, right-Select Adatum.com, point to New, and then Select Organizational Unit.

	4. Type Adatum_Computers, and then Select OK. 

	5. In the console tree, under Adatum.com, Select Computers.

	6. Right-Select LON-CL4, Select Move, Select Adatum_Computers, and then Select OK. 

	7. In Server Manager, Select Tools, and then Select Group Policy Management.

	8. In the Group Policy Management window, expand Forest: Adatum.com, expand Domains, expand Adatum.com, and then Select Adatum_Computers.

	9. Right-Select Adatum_Computers, and then Select Create a GPO in this domain, and Link it here.

	10. In the New GPO dialog box, in the Name box, type DeployO365, and then Select OK. 

	11. In Group Policy Management, Select Adatum_Computers, and in the right pane, right-Select DeployO365, and then Select Edit. If you see a Group Policy Management Console window, Select OK.

	12. In Group Policy Management Editor, expand Computer Configuration, Policies, Windows Settings, and then double-Select Scripts (Startup/Shutdown).

	13. Double-Select Startup, and then Select Show Files.

	14. In File Explorer, Select Home, Select New item, Select Text Document, and then press Enter to accept the default name.

	15. Double-Select New Text Document.txt.

	16. In Notepad, add the following line:


\\LON-CL1\Office16\setup.exe /configure \\LON-CL1\Office16\AdatumConfiguration.xml


17. Save the file as DeployO365.cmd. Ensure that in Save as type, you select All Files and that the file extension is .CMD.

18. Select Save.

19. Close Notepad.

20. Delete New Text Document.

21. Switch back to the Group Policy Management Editor, Startup Properties dialog box.

22. Select Add.

23. In the Add a Script dialog box, Select Browse.

24. In the Browse dialog box, select DeployO365.cmd, and then Select Open.

25. In the Add a Script dialog box, Select OK.

26. In the Startup Properties dialog box, Select OK.

27. Close Group Policy Management Editor.

28. Note that you could also deploy this script by using Microsoft Intune, Microsoft System Center Configuration Manager, or other electronic software distribution.

### Task 2: Verifying the installation

	1. Switch to LON-CL4, and if necessary, and sign in as Adatum\Beth, with the password, Xtr3m3L@bs. 

	2. Right-Select the Start button, and Select Command Prompt (Admin).

	3. In the User Account Control dialog box, type Adatum\Admin as the user name and Pa55w.rd as the password, and Select Yes.

	4. Type gpupdate /force and press Enter.

	5. Wait for the Group Policy to update for both the computer and user and then close the command prompt.

	6. Restart the computer.

 Note: If any updates have downloaded, Select Update, and then restart.

	7. Wait five minutes after LON-CL4 has restarted before continuing. This is to allow the Group Policy settings to take effect on LON-CL4.

	8. Sign in as ADATUM\Beth with the password Pa55w.rd. You may have to wait for Office to finish installing.

	9. Navigate to the Start screen, and note that Office 2016 is installed. You might have to wait up to 15 minutes before you see any available Office applications. 

	10. Select Word 2016. If you do not see it on the Start screen, type Word to bring up the icon.

	11. On the Activate Office page, in the E-mail address box, type Beth@M365xYYXXXXX.hostdomain.com, and then Select Next.

	12. On the Sign in page, in the Password box, type Xtr3m3L@bs, and then Select Sign in. Select OK on the notification window.

	13. In the First things first dialog box, Select Accept.

	14. Close the Welcome to your new Office dialog box. 

	15. In the templates list, Select Blank document.

	16. Type some text.

	17. Select File, and then Select Save.

	18. Select Browse in This PC – Documents.

	19. In File name, enter Meeting Report, and then Select Save. 

	20. Right-Select the taskbar and then Select Task Manager.

	21. In Task Manager, Select More details.

	22. On the Processes tab, under Background processes, notice that Microsoft Office Select-to-Run appears. 

	23. Select the Details tab, and notice officeSelecttorun.exe in the task list.

	24. Select the Services tab, and notice that the SelectToRunSvc service is running.

 Note: Check Task Manager for your deployment. These items will all be present in a successful install.

	25. Close Task Manager.

	26. Close Word 2016.
Results: You will have enabled centralized managed deployment of Office 365 ProPlus and implemented a standardized Microsoft Office configuration by using one version of Office.
