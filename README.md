# 🎣 Phishing Email Analysis: PayPal Spoofing Case Study

This repository contains a detailed analysis of a sample phishing email designed to impersonate **PayPal**. The analysis systematically identifies and breaks down the various indicators of compromise (IoCs) and social engineering tactics used in the attempt.

## 🎯 Goal of the Analysis

To document the process of identifying a fraudulent email, providing clear evidence for the "phishing" conclusion, and educating on common tactics used by cybercriminals.

## 📧 Sample Phishing Email Details

### 1. Subject and Sender
| Element | Details | Note |
| :--- | :--- | :--- |
| **Subject** | `Your Account Will Be Suspended – Immediate Verification Required!` | High urgency and threat. |
| **From** | `PayPal Support security@paypal.com` | Appears legitimate but is spoofed. |

### 2. Email Body (Key Content)
> Dear Customer,
> Your PayPal account has been flagged for unusual activity.
> To avoid permanent suspension, you must verify your information immediately.
> Click the link below to confirm your account: `https://paypal.com.verify-user-security-check.com/login`
> Failure to complete this step within **24 hours** may result in account termination.
> Thank you,
> PayPal Security Team

### 3. Attachment
* **Name:** `Account_Verification_Form.pdf.exe`

---

## 🔬 Detailed Analysis of Phishing Indicators

The email was analyzed across seven key areas to determine its fraudulent nature.

### 1. Sender Address Verification
* **Evidence:** The displayed domain, `paypal.com`, is actually altered. The letter "l" is replaced with a capital "I" (`paýpaI.com`).
* **Conclusion:** **Sender address is fake**—a common technique to visually deceive users.

### 2. Email Header Review (Authentication Failure)
Header analysis (via tools like MXToolbox) revealed crucial authentication failures:
* **SPF:** **Failed** $\rightarrow$ Server not authorised to send this email.
* **DKIM:** **Failed** $\rightarrow$ Signature does not match the real domain.
* **DMARC:** **Failed** $\rightarrow$ The domain denies this email.
* **Conclusion:** These failures clearly show the email is **not coming from the legitimate PayPal servers**.

### 3. URL Inspection (Domain Spoofing)
* **Displayed Link:** `https://paypal.com.verify-user-security-check.com/login`
* **Evidence:** While it *appears* to contain "PayPal", the actual main domain is **`secure-login-info-check.com`**. Everything before this (`paypal.com.`) is merely a subdomain used to mislead the recipient.
* **Conclusion:** The link leads to a **fake login page** designed to steal credentials.

### 4. Emotional Manipulation (Urgency)
* **Evidence:** The claim that the account will be restricted/terminated **within 24 hours**.
* **Conclusion:** This tactic uses **urgency** to create fear and pressure, forcing the user to act quickly without thinking critically about the email's legitimacy.

### 5. Suspicious Attachment
* **Attachment Name:** `Account_Update_Form.pdf.exe`
* **Evidence:** The file pretends to be a PDF (`.pdf`) but is actually an **executable file (`.exe`)**.
* **Conclusion:** The attachment is dangerous and **likely malicious**, designed to install malware.

### 6. Language and Formatting Issues
* **Generic Greeting:** Uses "Dear Customer" instead of a personalized name.
* **Wording:** Slightly unnatural sentence flow and not the usual, professional style of official communications.
* **Conclusion:** The unprofessional presentation further suggests the email is fraudulent.

---

## 💡 Overall Phishing Indicators Summary

| Indicator | Evidence |
| :--- | :--- |
| **Fake sender address** | Slight spelling change in the PayPal domain (I/l swap). |
| **Failing authentication** | SPF/DKIM/DMARC all fail. |
| **Fake URL** | Real domain is different from what is shown (`secure-login-info-check.com`). |
| **Urgency** | Threat of account lockout/termination within 24 hours. |
| **Dangerous attachment** | `.exe` file hidden behind a fake `.pdf` extension. |
| **Generic greeting** | Not personalized ("Dear Customer"). |
| **Formatting Issues** | Unprofessional writing and structure. |

## 🛡️ Final Conclusion

The email is clearly a **phishing attempt** designed to steal PayPal login details and possibly install malware on the victim's device.

---

## 📚 Resources and Tools Used
* **Email Header Analysis:** MXToolbox or Google Admin Toolbox
* **Domain Inspection:** Manual inspection of the URL structure
* **File Analysis:** Identification of the double extension (`.pdf.exe`)
*
