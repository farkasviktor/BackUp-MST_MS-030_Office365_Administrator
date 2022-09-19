## Lab 3: Configuring client connectivity to Microsoft Office 365

### Exercise 1: Create DNS records

1. On **LON-DC1**, signed in as **ADATUM\Administrator**.

1. Open Internet Explorer. Browse to the **Microsoft 365 admin center** and sign in as the tenant owner.

1. In the Navigation menu, select **Settings > Domains**.

1. Select **adatumXXXXXX.onelearndns.com** then select **Continue setup**.

1. On the Add DNS Records screen, select **Exchange and Exchange Online Protection**, **Skype for Business**, and **Intune and Mobile Device Management for Microsoft 365**.

1. Open **DNS Manager**.

1. Add the following records, copying and pasting the values from admin center.

   1. Mail Exchanger (MX).
      | Setting | Value |
      | --- | --- |
      | Host or child domain | (Leave blank) |
      | Fully qualified domain name (FQDN) of mail server | AdatumXXXXXX-onelearndns-com.mail.protection.outlook.com |
      | Mail server priority | 0 |

   1. CNAME.
      | Setting | Value |
      | --- | --- |
      | Alias name | autodiscover |
      | Fully qualified domain name (FQDN) for target host | autodiscover.outlook.com |

   1. Text (TXT).
      | Setting | Value |
      | --- | --- |
      | Record name | (Leave blank) |
      | Text | v=spf1 include:spf.protection.outlook.com -all

   1. CNAME.
      | Setting | Value |
      | --- | --- |
      | Alias name | sip |
      | Fully qualified domain name (FQDN) for target host | sipdir.online.lync.com |

   1. CNAME.
      | Setting | Value |
      | --- | --- |
      | Alias name | lyncdiscover |
      | Fully qualified domain name (FQDN) for target host | webdir.online.lync.com |

   1. Service Location (SRV).
      | Setting | Value |
      | --- | --- |
      | Service | _sip |
      | Protocol | _tls |
      | Priority | 100 |
      | Weight | 1 |
      | Port number | 443 |
      | Host offering this service | sipdir.online.lync.com |

   1. Service Location (SRV).
      | Setting | Value |
      | --- | --- |
      | Service | _sipfederationtls |
      | Protocol | _tcp |
      | Priority | 100 |
      | Weight | 1 |
      | Port number | 5061 |
      | Host offering this service | sipfed.online.lync.com |

   1. CNAME.
      | Setting | Value |
      | --- | --- |
      | Alias name | enterpriseregistration |
      | Fully qualified domain name (FQDN) for target host | enterpriseregistration.windows.net |

   1. CNAME.
      | Setting | Value |
      | --- | --- |
      | Alias name | enterpriseenrollment |
      | Fully qualified domain name (FQDN) for target host | enterpriseenrollment.manage.microsoft.com |

1. Switch to the **Microsoft 365 admin center** browser.

1. Select **Continue** then **Done**. Correct any mismatches reported.

### Exercise 2: Use the Microsoft Remote Connectivity Analyzer

1. On **LON-CL1**, signed in as **ADATUM\Administrator**.

1. Open Edge. Browse to the **Microsoft Remote Connectivity Analyzer** (**https://testconnectivity.microsoft.com**).

1. In the navigation menu, select **Office 365**. In the centre pane, select **Help Identify My Issue with Exchange DNS**.

1. Enter **adatumXXXXXX.onelearndns.com**, select **Office 365 (Default)**, then select **Perform Test**.

1. Verify that there are no errors.

1. In the navigation menu, select **Office 365**. In the centre pane, select **Help Identify My Issue with Lync DNS**.

1. Enter **francisco@adatumXXXXXX.onelearndns.com**, select **Office 365 (Default)**, then select **Perform Test**.

1. Verify that there are no errors.

1. In the navigation menu, select **Office 365**. In the centre pane, select **Outlook Connectivity**.

1. Enter Francisco’s sign-in address and password, select **Use Autodiscover to detect server settings**, select the **I understand** box, then select **Perform Test**.

1. Verify that there are no errors.

1. In the navigation menu, select **SARA Client**. Download and install the tool.

### Exercise 3: Use the Microsoft Support and Recovery Assistant

1. In the **Microsoft Support and Recovery Assistant**, select **Outlook** then select **Next**.

1. Select **I need help setting up my Office 365 email in Outlook** then select **Next**.

1. Select **Yes** to **Is this the affected machine?** then select **Next**.

1. Enter the tenant owner email address and password, then select **Next**.

1. Note any recommendations then close the tool.

### Exercise 4: Connect Office 2016 clients

1. On **LON-CL1**, signed in as **ADATUM\Administrator**.

1. Run **Outlook 2016**.
   | Setting | Value |
   | --- | --- |
   | Your name | MOD Administrator |
   | E-mail address | admin@LODSXXXXXX.onmicrosoft.com |

1. Send an e-mail to Francisco.

1. Create a meeting and invite Francisco.

1. On **LON-CL2**, signed in as **.\Student**.

1. Run **Outlook 2016**.
   | Setting | Value |
   | --- | --- |
   | Your name | Francisco Chaves |
   | E-mail address | francisco@adatumXXXXXX.onelearndns.com |

1. Reply to MOD Administrator’s email.

1. Accept MOD Administrator’s meeting request.
