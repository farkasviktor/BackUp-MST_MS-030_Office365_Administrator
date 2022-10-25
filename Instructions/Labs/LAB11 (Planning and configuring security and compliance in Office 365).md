## Lab 11: Planning and configuring security and compliance in ‎Office 365 

### Exercise 1: Manage Azure Information Protection (optional)

#### Task 1: Install the Azure Information Protection client

1. Run Internet Explorer. Browse to **https://www.microsoft.com/en-us/download/details.aspx?id=53018** (Azure Information Protection unified labelling client).

1. Download **AzInfoProtection_UL.exe** and save it to **C:\<ShareName>\OfficeProPlus**.

   Note that there is a msi download available for centralised software deployment.

1. Run\
**\\<ShareName>\OfficeProPlus\AzInfoProtection_UL.exe**

#### Task 2: Configure Azure Information Protection

1. Open Edge. Browse to the **Microsoft 365 Compliance** admin center and sign in as the tenant owner.

1. In the Navigation menu, select **Solutions > Information protection**.

  Note that sensitivity labels can also be modified in the Office 365 Security & Compliance admin center (Classification > Sensitivity labels) and the Microsoft 365 security admin center (Classification > Sensitivity labels).

1. If you see a message to turn on the ability to process content in Office online files, then select **Turn on now**.

1. Select **Create a label**.

   | Setting | Value |
   | --- | --- |
   | Name | PII |
   | Description for users | Personal Identifiable Information |
   | Description for admins | Personal Identifiable Information |
   | Encryption | None |
   | Content Marking | On |
   | Add a watermark | On |
   | Watermark text | Personal Identifiable Information (PII) |
   | Font size | 24 |
   | Font color | Red |
   | Text layout | Diagonal |
   | Add a header | Off |
   | Add a footer | Not Off |
   | Auto-labelling for Office apps | On |
   | Detect content that matches these conditions | Document contains New Zealand Inland Revenue number |
   | When content matches these conditions | Automatically apply the label |
   | Display this message to users when the label is applied | Personal Identifiable Information (PII) was detected |

1. Select **Publish labels**. This creates a policy.

   | Setting | Value |
   | --- | --- |
   | Sensitivity labels to publish | All |
   | Publish to users and groups | All |
   | Apply this label by default | None |
   | Users must provide justification to set a lower classification label | Selected |
   | Require users to apply a label to their email or documents | Not selected |
   | Provide users with a link to a custom help page | Selected |
   | Custom help page | https://docs.microsoft.com/en-us/azure/information-protection/faqs |
   | Policy name | ADatum PII |
   | Policy description | A. Datum Corporation Personal Identifiable Information (PII) policy |

#### Task 3: Create protected content (cloud-only user)

1. Open Edge. Browse to **https://XXXXXXX.sharepoint.com/sites/adatummarketing**. Sign in as **Amy**.

1. Follow the site.

1.. Select the Documents library. Note the files and folders present.

1. Open **Word**.

1. Open **Accounts** and verify that Office ProPlus is signed in as Amy and that OneDrive - Contoso and Sites - Contoso are both under Connected Services.

1. If prompted to sign in to Microsoft Azure Information Protection then sign in as **Amy**.

1. Create a new document. Enter the following text into the document.\
Memo to HR.\
Alex Wilbur’s IRD number is 21-234-567.

   *Note: This number was generated (2 then 123456 then the correct checksum digit). Any resemblance to an actual entity is accidental.*

1. Save the document to the **Documents** library of the **ADatum Marketing** SharePoint site.

   Note: If the Sites location in the Save As dialog shows “There are no sites to show right now” then Office has not yet cached the SharePoint Sites. In this case, select Browse and enter https://XXXXXXX.sharepoint.com/sites/adatummarketing in the address bar.

1. Word should automatically apply the PII policy.

  *It should, but often doesn't. I can't find anything on the web for why it might not work.* **TODO**
