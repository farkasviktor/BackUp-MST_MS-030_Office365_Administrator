## Lab 7A: Configuring message transport in Exchange Online

### Exercise 1: Configure message-transport settings

#### Task 1: Create a custom send and receive connector to enforce TLS

1. Open Edge. Browse to the **Exchange admin center** and sign in as the tenant owner.

1. In the navigation menu, select **mail flow** then select **connectors**.

1. Select **New** (the plus icon).

   | Setting | Value |
   | --- | --- |
   | From | Office 365 |
   | To | Partner organization |
   | Name | Humongous Insurance Outgoing |
   | When do you want to use this connector? | Only when email messages are sent to these domains: humongousinsurance.com |
   | How do you want to route email messages? | Use the MX record |
   | How should Office 365 connect? | Always use Transport Layer Security, Issued by a trusted CA |
   | Validate this connector | Yes, to postmaster@humongousinsurance.com, but note that this will fail |

1. Select **New** (the plus icon).

   | Setting | Value |
   | --- | --- |
   | From | Partner organization |
   | To | Office 365 |
   | Name | Humongous Insurance Incoming |
   | How do you want to identify the partner organization? | Use the sender’s domain |
   | What sender domain? | humongousinsurance.com |
   | What security restrictions do you want to apply? | Reject email messages if they aren’t sent over TLS |

#### Task 2: Create transport rules

1. In the Navigation menu, select **mail flow** then select **rules**.

1. Select the **down arrow** button next to the plus icon then select **Apply disclaimers…**

   | Setting | Value |
   | --- | --- |
   | Name | A. Datum disclaimer |
   | Apply this rule if… | The recipient is located… Outside the organization |
   | Do the following… | Append the disclaimer… |
   | Edit text | \<hr /\>Disclaimer goes here. |
   | Fall back to action | Wrap |
   | Audit this rule with severity level | Low |
   | Choose a mode for this rule | Enforce |

1. Select the **down arrow** button next to the plus icon then select **Send messages to a moderator…**

   | Setting | Value |
   | --- | --- |
   | Name | IT2 Moderation |
   | Apply this rule if… | The recipient is a member of… IT 2 |
   | Do the following… | Forward the message for approval to… MOD Administrator |
   | Audit this rule with severity level | Medium |
   | Choose a mode for this rule | Enforce |

#### Task 3: Verify transport rules

1. Open **Outlook**, signed in as **Amy**.

1. Send an e-mail to **alias@outlook.com** with a subject of “External recipient”.

1. Send an email to Holly.

1. Open a web browser and sign in to **alias@outlook.com**.

1. Read the email from Amy and verify the disclaimer has been added.

1. 1. Open **Outlook 2016**, signed in as **MOD Administrator**.

1. Approve Amy’s e-mail message to Holly.

#### Task 4: Create a journal rule

1. Switch to Edge running the Exchange admin center.

1. In the navigation menu, select **compliance management** then select **journal rules**.

1. Next to **Send undeliverable journal reports to**, select **Select address**. Select **MOD Administrator**

1. Select **New** (the plus icon).

   | Setting | Value |
   | --- | --- |
   | Send journal reports to | journal@humongousinsurance.com |
   | Name | Development journaling |
   | If the message is sent to or received from… | A specific user or group… Development |
   | Journal the following messages… | All messages |


____________________________________________________________
## Lab 7B: Configuring email protection and client policies

### Exercise 1: Configure email protection

#### Task 1: Configure the malware filter

1. Open Edge. Browse to the **Exchange admin center** and sign in as the tenant owner.

1. In the navigation menu, select **protection** then select **malware filter**.

1. Select **Default**, and then select **Edit** (the pencil icon).

   | Setting | Value |
   | --- | --- |
   | Do you want to notify recipients if their messages are quarantined? | Yes and use custom notification text |
   | Custom notification text | Malware has been detected. Please wait to be contacted by the IT team. |
   | Sender notifications | Both internal senders and external senders |
   | Notify administrator about undelivered messages from internal senders | Admin@XXXXXX.onmicrosoft.com |
   | Notify administrator about undelivered messages from external senders | Admin@XXXXXX.onmicrosoft.com |

#### Task 2: Configure the connection filter

1. In the navigation menu, select **protection** then select **connection filter**.

1. Select **Default**, and then select **Edit** (the pencil icon).

   | Setting | Value |
   | --- | --- |
   | IP Block list | Add 191.161.0.0/24 |
   | Enable safe list | Selected |

#### Task 3: Configure the spam filter

1. In the navigation menu, select **protection** then select **spam filter**.

1. Select **Default**, and then select **Edit** (the pencil icon).

   | Setting | Value |
   | --- | --- |
   | Spam | Move message to Junk Email folder |
   | High confidence spam | Quarantine message |

1. Select **New** (the plus icon).

   | Setting | Value |
   | --- | --- |
   | Name | Sales spam policy |
   | Spam | Prepend subject line with text. |
   | High confidence spam | Move message to Junk Email folder |
   | Prepend subject line with this text | Junk: |
   | Applied to *(scroll to bottom)* | If the recipient is a member of… Sales |

#### Task 4: Test the spam-filter *(optional)*

1. Open a web browser and sign in to **alias@outlook.com**.

1. Create a new message to **lindsey@XXXXXX.onmicrosoft.com**.

1. Copy and paste the following into the body of the message and then send.

   ```
   XJS*C4JDBQADN1.NSBN3*2IDNEN*GTUBE-STANDARD-ANTI-UBE-TEST-EMAIL*C.34X
   ```

   *Link*:  https://spamassassin.apache.org/gtube/

1. Repeat the above, to **francisco@XXXXXX.onmicrosoft.com**.

1. Switch to the Edge tab running **Office 365 Security & Compliance**.

1. In the navigation menu, select **Threat management > Review** then select **Quarantine**.

1. Review the quarantined messages.

*The GTUBE test email should trigger the anti-spam features of an email system. Often, however, Exchange Online rejects it before the message even reaches a tenant. Check the inbox of alias@outlook.com for any NDRs.*

### Exercise 2: Configure client access policies

#### Task 1: Configure an Outlook Web App policy

1. Switch to the Edge tab running **Exchange admin center**.

1. In the navigation menu, select **permissions** then select **Outlook Web App policies**.

1. Select **New** (the plus icon).

   | Setting | Value |
   | --- | --- |
   | Name | Limited features |
   | Instant messaging | Not selected |
   | Text messaging | Not selected |
   | Unified messaging | Not selected |
   | LinkedIn contact sync | Not selected |
   | Journaling | Not selected |
   | Direct File Access | Not selected |

1. In the navigation menu, select **recipients** then select **mailboxes**.

1. Select **Sallie McIntosh**, then select **Edit** (the pencil icon).

1. On the **mailbox features** tab, next to Email Connectivity, Outlook on the web: Enabled, select **View details**. Assign the **Limited features** policy.

1. Open **Outlook 2016**, signed in as MOD Administrator.

1. Send a message to Sallie, attaching the csv files in C:\Labfiles.

1. Open an InPrivate Edge window. Browse to the **Office 365 home page** and sign in as **Sallie**.

1. Open the e-mail from MOD Administrator. 

*This feature take time to be applied to a mailbox. If necessary, come back to this task later.*

#### Task 2: Configure mobile-device access

1. Switch to the Edge tab running **Exchange admin center**.

1. In the navigation menu, select **mobile** then select **mobile device access**.

1. Select **edit** (right-hand side).

   | Setting | Value |
   | --- | --- |
   | When a mobile device that isn't managed by a rule or personal exemption connects to Exchange | Quarantine |
   | Select administrators to receive email messages when a mobile device is quarantined | MOD Administrator |

#### Task 3: Configure a mailbox policy for mobile devices

1. In the navigation menu, select **mobile** then select **mobile device mailbox policies**.

1. Select **Default (default)**, and then select **Edit** (the pencil icon).

   | Setting | Value |
   | --- | --- |
   | Require a password | Selected |
   | Allow simple passwords | Selected |
   | Minimum password length | 6 |
