# CHAPTER 20: Conditional Access and Zero Trust Implementation

Microsoft Entra ID provides authentication and authorization, but Conditional Access adds the critical "under what circumstances" layer. This chapter examines how organizations implement adaptive, policy-based access control.

---

## 1. Conditional Access: The Policy Engine

Conditional Access is the Zero Trust policy engine in Microsoft Entra ID. It evaluates signals from multiple sources to make real-time access decisions.

### **Core Concept: If-Then Logic**
At its foundation, Conditional Access is an if-then statement:
* **If** a user wants to access a resource,
* **Then** they must satisfy specific requirements.

### **Why Organizations Need This**
Traditional perimeter security assumed that anything inside the corporate network was trustworthy. Conditional Access rejects this assumption. Every access request is evaluated based on current context, not just a successful login.

---

## 2. The Three Components: Signals, Decisions, Controls

Every Conditional Access policy is built from three parts.

### **A. Signals (The "If" Conditions)**
These are the data points evaluated when a user attempts access:

* **User and Group Identity:** Specific users, groups, directory roles, or guest users.
* **Location:** IP address ranges or geographic locations. Organizations can designate trusted locations (e.g., office headquarters).
* **Device Platform:** Windows, macOS, iOS, Android, or Linux.
* **Device State:** Is the device registered in Entra ID? Is it compliant with Intune policies?
* **Application:** Which cloud app or service is being accessed?
* **Risk Level:** Integration with Entra ID Protection. Is the sign-in flagged as risky? Is the user flagged as compromised?
* **Client Application Type:** Browser, mobile app, legacy authentication protocols.

### **B. Decisions**
After evaluating signals, the policy makes one of three decisions:
* **Grant Access:** Allow the user to proceed.
* **Grant Access with Requirements:** Allow access, but require additional actions (covered in Controls).
* **Block Access:** Deny access entirely.

### **C. Controls (The "Then" Actions)**
If access is granted conditionally, these are the requirements a user must satisfy:

**Grant Controls:**
* **Require Multifactor Authentication (MFA):** User must complete a second verification step.
* **Require Device Compliance:** Device must meet organizational security policies (managed by Intune).
* **Require Hybrid Azure AD Joined Device:** Device must be joined to both on-premises AD and Entra ID.
* **Require Approved Client App:** Only specific apps (e.g., Outlook Mobile) are allowed.
* **Require App Protection Policy:** App must have Intune policies applied.

**Session Controls:**
* **Sign-in Frequency:** Force re-authentication after a specific time period.
* **Persistent Browser Session:** Control whether users stay signed in after closing the browser.
* **App Enforced Restrictions:** Limit functionality (e.g., block downloads in SharePoint Online).
* **Defender for Cloud Apps:** Monitor sessions and block risky actions in real time.

---

## 3. Common Policy Scenarios

### **Scenario 1: Block Legacy Authentication**
Legacy protocols (POP, IMAP, SMTP) cannot perform MFA. Attackers exploit this.
* **Signal:** Client application type = Legacy authentication.
* **Decision:** Block access.

### **Scenario 2: Require MFA for Administrators**
Administrative accounts are high-value targets.
* **Signal:** User has a directory role (e.g., Global Administrator).
* **Decision:** Grant access.
* **Control:** Require multifactor authentication.

### **Scenario 3: Require Compliant Device for Sensitive Apps**
Financial or HR applications require secure devices.
* **Signal:** User accessing app "Payroll System."
* **Decision:** Grant access.
* **Control:** Require device to be compliant with Intune policies.

### **Scenario 4: Block Access from Untrusted Locations**
Prevent access from high-risk countries.
* **Signal:** User location = Geographic region "High Risk Countries."
* **Decision:** Block access.

---

## 4. Report-Only Mode and Policy Testing

Conditional Access policies can have significant impacts. Microsoft provides tools to test safely.

### **Report-Only Mode**
Policies in this state are evaluated but not enforced.
* **How it works:** The policy logs what *would* have happened if it were enabled.
* **Use case:** Deploy a new policy in report-only mode. Review sign-in logs for 7-14 days to identify unintended impacts (e.g., blocking critical users or apps).
* **Where to check:** Entra ID > Sign-in logs > Select an event > "Report-only" tab.

### **What-If Tool**
This tool simulates policy application.
* **Input:** Specify a user, application, device platform, and location.
* **Output:** The tool shows which policies would apply and what actions would be required.
* **Benefit:** Test "what would happen if Sarah tries to access SharePoint from her personal iPad in Paris?"

### **Insights and Reporting Workbook**
This Azure Monitor workbook provides visualizations:
* Which policies are affecting the most users?
* Are there apps being blocked unintentionally?
* How many MFA challenges were triggered in the past 30 days?

---

## 5. Zero Trust Principles

Conditional Access is the enforcement mechanism for Zero Trust in Azure.

### **The Three Pillars**
**1. Verify Explicitly**
Always authenticate and authorize using all available data: user identity, device health, location, real-time risk detection, and data sensitivity.

**2. Use Least Privilege Access**
Grant the minimum permissions necessary. Combine with Privileged Identity Management (PIM) for just-in-time admin access.

**3. Assume Breach**
Do not trust anything inside or outside the network perimeter. Every access request is untrusted until verified.

### **How Conditional Access Implements Zero Trust**
* **Verify Explicitly:** Policies evaluate multiple signals per request.
* **Least Privilege:** Grant controls enforce "prove you are secure" requirements before access.
* **Assume Breach:** Even authenticated users face continuous evaluation. If a user's risk level changes mid-session, access can be revoked or re-challenged.

---

## 6. Licensing Requirements

Conditional Access is not available in the free tier of Entra ID.

| Feature | Free Tier | Premium P1 | Premium P2 |
| :--- | :--- | :--- | :--- |
| **Conditional Access Policies** | No | Yes | Yes |
| **Risk-Based Policies** | No | No | Yes (requires ID Protection) |
| **Report-Only Mode** | No | Yes | Yes |
| **PIM Integration** | No | No | Yes |

**Note:** Microsoft 365 E3 includes Entra ID P1. Microsoft 365 E5 includes Entra ID P2.

---

## 7. Policy Evaluation and Multiple Controls

### **Evaluation Order**
Policies are not evaluated in the order they appear in the portal. All enabled policies are evaluated simultaneously.

### **Multiple Grant Controls**
If a policy requires multiple controls, administrators choose the logic:
* **Require ALL selected controls:** User must satisfy MFA *and* have a compliant device.
* **Require ONE of the selected controls:** User must satisfy MFA *or* have a compliant device.

### **Conflicting Policies**
If one policy grants access and another blocks access, **block always wins**. This is a security safeguard.

---

## 8. Real-World Example: "SecureBank Inc."

**SecureBank Inc.** has 2,000 employees and operates in 15 countries. They implement Conditional Access to meet regulatory requirements.

### **Phase 1: Block Legacy Authentication**
SecureBank creates a policy:
* **Signal:** Client application = Exchange ActiveSync, IMAP, POP3.
* **Decision:** Block access.
* **Result:** Attackers using password spray attacks against legacy protocols are completely blocked. All users are forced to modern authentication clients (Outlook app, web browser).

### **Phase 2: Protect Administrators**
SecureBank has 25 Global Administrators. A second policy:
* **Signal:** Directory role = Global Administrator, Security Administrator, or Privileged Role Administrator.
* **Decision:** Grant access.
* **Control:** Require MFA (using hardware security keys for phishing resistance).
* **Result:** Even if an attacker steals an admin password, they cannot sign in without the physical security key.

### **Phase 3: Enforce Device Compliance for Finance App**
The "Finance Portal" app contains sensitive payroll and investor data. A third policy:
* **Signal:** Cloud app = Finance Portal.
* **Decision:** Grant access.
* **Controls:** Require MFA *and* require device compliance.
* **Result:** A finance analyst named Carlos tries to access the app from his personal, unmanaged laptop. The policy blocks him and displays: "This device does not meet security requirements. Contact IT." Carlos switches to his corporate laptop (managed by Intune, encrypted, patched) and gains access.

### **Phase 4: Geographic Restrictions**
SecureBank has no operations in certain high-risk countries. A fourth policy:
* **Signal:** Location = Named location "Restricted Countries."
* **Decision:** Block access.
* **Result:** An attacker in a blocked country compromises an employee's password. The attacker attempts to sign in but is immediately blocked due to location. The legitimate employee (working from an office in New York) continues to work without disruption.

---

## 9. Integration with Other Services

Conditional Access policies integrate across the Microsoft ecosystem:

* **Entra ID Protection:** Policies can require password change if user risk is "High."
* **Microsoft Intune:** Device compliance is verified through Intune's reporting.
* **Microsoft Defender for Cloud Apps:** Session policies monitor user behavior within apps and block suspicious file downloads.
* **Azure AD PIM:** Require administrators to activate roles only from compliant devices or trusted locations.

---

**Summary:**
Conditional Access transforms identity from a simple "yes or no" decision into a dynamic, context-aware security control. By evaluating signals, enforcing controls, and integrating with Zero Trust principles, organizations build adaptive defenses that respond to modern threats in real time.
