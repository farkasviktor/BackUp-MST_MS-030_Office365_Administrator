
## Module 13: Planning and configuring identify federation

#### Lab: Planning and configuring identity federation

## Exercise 1: Deploying Active Directory Federation Services (AD FS) and Web Application Proxy

### Task 1: Add DNS records required for AD FS

	1. On LON-DS1, Select Start and then Select Windows PowerShell.

	2. Type IPConfig and press Enter.

	3. Record the IPv4 address assigned to the server. 

	4. On LON-DC1, open Server Manager, Select Tools, and then Select DNS.

	5. Expand LON-DC1, expand Forward Lookup Zones, and then Select M365xyyxxxxx.hostdomain.com.

	6. Right-Select M365xyyxxxxx.hostdomain.com, and then Select New Host (A or AAAA).

	7. In the New Host dialog box, leave the Name box empty, in the IP address box, type the External IP address provided by the hosting partner. 

	8. Select Add Host, and then Select OK. 

	9. In the New Host dialog box, leave the Name box empty, in the IP address box, type the LON-DS1 IP address that you recorded in Step 3.

	10. Select Add Host, Select OK, and then Select Done.

### Task 2: Install and configure the AD FS server role

	1. Sign in to the LON-DS1 virtual machine as ADATUM\Administrator with a password of Pa$$word.

	2. Select Start, right Select Windows PowerShell, and then Select Run as Administrator.

	3. At the command prompt, type the following command and press Enter. This command creates the Key Distribution Services root key to generate group Managed Service Account passwords for the account that will be used later in this lab. You should receive a Guid value as a response to this command.


Add-KdsRootKey –EffectiveTime ((get-date).addhours(-10))


4. Select Start and then Select Server Manager.

5. In Server Manager, Select Manage, and then Select Add Roles and Features. If you get a Server Manger message about collecting inventory data, Select OK. Wait a minute and then try this step again.

6. In the Add Roles and Features Wizard, on the Before you begin page, Select Next.

7. On the Select installation type page, Select Role-based or Feature-based installation, and then Select Next.

8. On the Select destination server page, Select Select a server from the server pool, verify that the target computer is highlighted, and then Select Next.

9. On the Select server roles page, Select Active Directory Federation Services, and then Select Next.

10. On the Select features page, Select Next.

11. On the Active Directory Federation Service (AD FS) page, Select Next.

12. On the Confirm installation selections page, Select Install.

13. When installation completes, on the Installation progress page, Select Close.

14. Select the exclamation mark icon on the toolbar, and then Select Configure the federation service on this server.

15. In the Active Directory Federation Services Configuration Wizard, on the Welcome page, Select Create the first federation server in a federation server farm, and then Select Next.

16. On the Connect to AD DS page, Select Next.

17. On the Specify Service Properties page, use the following settings, and then Select Next:

- For SSL Certificate, Select the wild card certificate provided by the hosting partner.

- For Federation Service Name, type M365xyyxxxxx.hostdomain.com, replacing M365xyyxxxxx with your unique M365x domain name.

- For Federation Service Display Name, type Adatum Corporation.

18. On the Specify Service Account page, select the option Create a Group Managed Service Account, for Account Name type svc-ADFS, and then Select Next.

19. On the Specify Configuration Database, Select Create a database on this server using Windows Internal Database, and then Select Next.

20. On the Review Options page, Select Next.

21. Once the prerequisites check is complete, on the Pre-requisite Checks page, Select Configure. Note : Some warnings are expected to be shown.

22. When the configuration completes, on the Results page, Select Close.

### Task 3: Install the Web Application Proxy server role service

	1. Sign in to the LON-WAP1 virtual machine as Adatum\Administrator with a password of Pa$$word.

	2. Select Start and then Select Server Manager.

	3. In Server Manager, Select Manage, and then Select Add Roles and Features.

	4. In the Add Roles and Features Wizard, on the Before you begin page, Select Next.

	5. On the Select installation type page, Select Role-based or Feature-based installation, and then Select Next.

	6. On the Select destination server page, Select Select a server from the server pool, verify that the target computer is highlighted, and then Select Next.

	7. On the Select server roles page, Select Remote Access, and then Select Next.

	8. On the Select features page, Select Next.

	9. On the Remote Access page, Select Next.

	10. On the Select role services page, Select Web Application Proxy, in the popup window, Select Add Features, and then Select Next.

	11. On the Confirm installation selections page, Select Install.

	12. When the installation is complete, on the Installation progress page, Select Close.

### Task 4: Configure the Web Application Proxy server

	1. On LON-WAP1, in Server Manager, Select Tools, and then Select Remote Access Management.

	2. In the Remote Access Management Console, in the left navigation pane, Select Web Application Proxy. In the middle navigation pane, Select Run the Web Application Proxy Configuration Wizard.

	3. In the Web Application Proxy Configuration Wizard, on the Welcome page, Select Next.

	4. On the Federation Server page, use the following settings, and then Select Next:

	- Federation service name: M365xyyxxxxx.hostdomain.com, replacing M365xyyxxxxx with your unique M365x domain name.

	- User name: Adatum\Administrator

	- Password: Pa55w.rd

	5. On the AD FS Proxy Certificate page, select the .hostdomain.com certificate, and then Select Next.

	6. On the Confirmation page, Select Configure.

	7. When the configuration is complete, on the Results page, Select Close.

### Task 5: Verify that the AD FS server is working

	1. Switch to the LON-DS1 virtual machine.

	2. In Server Manager, Select Tools, and then Select Event Viewer.

	3. In Event Viewer, in the details pane, expand Applications and Services Logs, expand AD FS, and then Select Admin.

	4. In the Event ID column, verify that event ID 100 displays. 

 Note: If the federation server is configured properly, you should see a new event with event ID 100 in the Event Viewer Application log. This event verifies that the federation server was able to communicate successfully with the Federation Service.

	5. On LON-DC1, open Internet Explorer and connect to https://M365xyyxxxxx.hostdomain.com/adfs/fs/federationserverservice.asmx, replacing M365xyyxxxxx with your unique M365x domain name, and then press Enter. 

	6. If you get a message stating There is a problem with this website’s security certificate, Select Continue to this website. 

 Note: The expected output is a display of XML with the service description document. If this page displays, then Microsoft Internet Information Services (IIS) on the federation server is operational and serving pages successfully.

 


Results: After completing this exercise, you should have deployed the AD FS server in a federation server farm, and deployed the Web Application Proxy server to support AD FS.


  
‎ 

## Exercise 2: Configuring federation with Microsoft Office 365

### Task 1: Switch the Office 365 tenant to federated mode

	1. Switch to the LON-DS1 virtual machine.

	2. Open Internet Explorer, and then connect to https://portal.office.com.

	3. Sign in as [Admin@adyyxxxxx.hostdomain.com](mailto:holly@adyyxxxxx.hostdomain.com) with the password Xtr3m3L@bs.

	4. Select Admin.

	5. If you are connected to the previous Office 365 admin center, Select the banner at the top of the page to access the new Office 365 admin center

	6. Select Users and then Select Active Users.

	7. Select MOD Administrator, and then, in the User name/Email Aliases section, Select Edit.

	8. Change the primary email alias to M365xyyxxxxx.onmicrosoft.com. In the Warning window, Select Save, and then Select Sign Out.

	9. Close Internet Explorer. Admin cannot change the M365xyyxxxxx.hostdomain.com to a federated domain if she is logged in using an account from this domain. 

	10. Select Start, and then Select the Windows PowerShell icon.

	11. At the Windows PowerShell prompt, type the following commands, pressing Enter at the end of each line:


Set-ExecutionPolicy 

Unrestricted –force

 

Import-Module MSOnline


	12. At the Windows PowerShell prompt, type the following command, and then press Enter:


$msolcred = Get-Credential


	13. In the Windows PowerShell Credential dialog box, enter the following credentials, and then Select OK:

	- User name: Admin@ M365xyyxxxxx.onmicrosoft.com

	- Password: Xtr3m3L@bs

	14. At the Windows PowerShell prompt, type the following command, and then press Enter:


Connect-MsolService -Credential $msolcred


	15. At the Windows PowerShell prompt, type the following command, and then press Enter:


Get-MsolDomain


	16. Verify that your lab domain, M365xyyxxxxx.hostdomain.com, is listed as Verified and Managed.

 Note: If you were running this from a computer other than the AD FS federation server, you would need to use the Set-MsolAdfsContext to reference the AD FS server.

	17. At the Windows PowerShell prompt, type the following command, and then press Enter:


Convert-MsolDomainToFederated -DomainName M365xyyxxxxx.hostdomain.com


	18. Verify that you get a Successfully updated M365xyyxxxxx.hostdomain.com domain message.

	19. At the Windows PowerShell prompt, type the following command, and then press Enter:


Get-MsolFederationProperty -DomainName M365xyyxxxxx.hostdomain.com


 Note: This command reports the status of the domain federation, and provides details of URLs and certificates.

Results: After completing this exercise, you should have enabled a federation trust between your on-premises Active Directory domain and Office 365 through your AD FS federation server, and you should have converted your domain for federated authentication in Office 365.


 
