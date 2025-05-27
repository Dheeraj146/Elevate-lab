## 1. Sample Phishing Email
A phishing email was obtained for educational purposes. The message claimed to be from Netflix and warned the recipient of suspicious activity that had resulted in a suspended account.
The email prompted the recipient to click a link to "verify billing information."

<pre>Subject: Action Required: Your Netflix Account Has Been Suspended

From: Netflix Support support@netflix-billing.com
To: john.doe@gmail.com

Dear Customer,

We noticed suspicious activity on your Netflix account and have temporarily suspended your membership for your security.

To restore full access, please verify your billing information:

👉 Click here to verify your account

If you do not complete the verification within 24 hours, your account will be permanently locked.

Thank you for being a valued member of Netflix.

Sincerely,
Netflix Billing Department
Netflix Inc.</pre>

2. Examination of Sender's Email Address
   
Claimed Sender: Netflix Support support@netflix-billing.com

The domain netflix-billing.com is not an official Netflix domain.

This is a spoofed address meant to mimic legitimate communication.

🔍 Red Flag: Domain looks official but is not registered to Netflix.


3. Email Header Analysis
Using an online email header analyzer:

Return-Path and Received From domains did not match the claimed sender.

IP address traced back to a non-Netflix server.

SPF/DKIM authentication failed or was absent.

🔍 Red Flag: Inconsistencies between sender and return-path; authentication missing.

<pre>Return-Path: <support@netflix-billing.com>
Received: from mail.netflix-billing.com (192.0.2.12)
  by smtp.example.com with ESMTP id ZKXH8M1G7;
  Mon, 3 Mar 2025 08:42:13 -0500 (EST)
From: Netflix Support <support@netflix-billing.com>
Reply-To: billing@netflix-support.com
To: user@example.com
Subject: Action Required: Update Your Netflix Payment Information
Date: Mon, 3 Mar 2025 08:42:13 -0500
Message-ID: <E8A9F7A2D9B@netflix-billing.com>
MIME-Version: 1.0
Content-Type: multipart/alternative;
 boundary="----=_Part_192_3048238927.1709466132904"</pre>

4. Suspicious Links or Attachments
Link in the email: http://netflix-security-check.com/verify

Hovering revealed a mismatched and unofficial domain.

No attachments were present, but the link directed to a fake login page.

🔍 Red Flag: Deceptive link leading to a phishing site.

5. Urgent or Threatening Language
Example language used:

“If you do not complete the verification within 24 hours, your account will be permanently locked.”

🔍 Red Flag: Creates a false sense of urgency to provoke immediate action.

6. Mismatched URLs
The anchor text in the email said “Click here to verify your account.”

Hovering over it revealed the URL: http://netflix-security-check.com/verify

Not consistent with Netflix’s official domain: netflix.com

🔍 Red Flag: Mismatch between displayed and actual URL.



7. Spelling and Grammar Errors
Minor grammar issues were noted, such as:

“Thank you for being a valued member of Netflix.” (Awkward phrasing)

“Sincerely, Netflix Billing Department” (Netflix does not typically use this closing.)

🔍 Red Flag: Subtle errors indicating unprofessional crafting.



8. Summary of Phishing Traits Identified
<pre>
| Trait                   | Detected  | Notes                                 |
| ----------------------- | --------  | ------------------------------------- |
| Spoofed Sender          | ✅        | Unofficial domain used                |
| Header Discrepancies    | ✅        | IP and domain mismatch                |
| Suspicious Links        | ✅        | Leads to non-Netflix domain           |
| Urgency/Threats         | ✅        | Pressure to act fast                  |
| Mismatched URLs         | ✅        | Display text differs from actual link |
| Grammar/Spelling Issues | ✅        | Minor errors detected                 |</pre>
