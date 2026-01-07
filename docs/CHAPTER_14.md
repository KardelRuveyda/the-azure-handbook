# CHAPTER 14: User Objects and the "Carbon-Based" Requirement

This chapter defines the most fundamental identity object: the User. In modern cloud security, we must distinguish between human actors and automated processes to maintain a secure environment.

---

## 1. The Definition of a "User"
In Microsoft Entra ID, a **User Account** must strictly represent a **carbon-based life form**. 
* **Individual Accountability:** Every account should be tied to a specific person. Sharing accounts between multiple people is a critical error that leads to:
    * **Audit Failure:** You lose the ability to see who actually performed a specific action.
    * **Permission Inflation:** Shared accounts end up with "creeping permissions" (inflated POS) to satisfy the varied needs of multiple users.
* **The "Mouse and Keyboard" Rule:** Human users sit at a keyboard, use a mouse, and possess the ability to interact with secondary devices like phones for MFA (Multiactor Authentication).

<img width="1309" height="609" alt="image" src="https://github.com/user-attachments/assets/07f2176c-72fa-4487-a726-0e5a12745a53" />


## 2. The MFA Crisis for Automations
Historically, many organizations used "User Accounts" for scripts and automations. This is now causing major issues:
* **Human-Based Requirements:** Humans can comply with mandatory MFA requests. Automations/Applications cannot operate a phone or use a token.
* **The Panic:** As Microsoft rolls out mandatory MFA, organizations that used user accounts for scripts are "panicking" because they cannot perform the authentication. 
* **The Move:** These organizations must now move to the "correct thing all along": Service Principals and Managed Identities.

<img width="875" height="353" alt="image" src="https://github.com/user-attachments/assets/685eb489-9f1f-475d-a874-4862186343d6" />


## 3. Managing Users in the Portals
While user information appears in multiple places, the functionality differs:
* **Entra Portal (Primary):** This is the primary place to manage Entra ID. 
* **Azure & Office Portals:** These offer only a **subset** of the full identity functionality.
* **Microsoft Graph & PowerShell:** The modern standard for management is the **Microsoft Graph PowerShell module**, used for automation and scaling.

<img width="1230" height="610" alt="image" src="https://github.com/user-attachments/assets/c36e6755-56f2-4046-b987-4bd5768d162f" />



## 4. Attributes, Types, and Origins
* **UPN (User Principal Name):** The unique login ID (e.g., `commander@tech.net`) containing the primary custom DNS.
* **User Type:**
    * **Member:** Internal identities within the organization.
    * **Guest:** External identities (e.g., from Facebook, Google, or other Azure ADs).
    * *Note:* You can make an external identity a Member if needed; there isn't a 1:1 correlation between external and guest.
* **Identities/Origins:** The identities column shows where the account originates (the local tenant, Facebook, Google, Microsoft Account, etc.).
* **On-Premise Sync:** A property showing "Yes" or "No" to indicate if the object was replicated from a local Active Directory (ADDS).

<img width="701" height="469" alt="image" src="https://github.com/user-attachments/assets/4fd1ddb1-d800-40e7-acbc-8d73df04de8a" />



## 5. Provisioning and Bulk Operations
* **Bulk Operations:** Creating users via **CSV file** for large-scale imports.
* **HR-Driven Provisioning:** You can hook into HR systems (like Workday).
    * The HR system calls the **Entra Provisioning Agent**.
    * This agent creates the user in the **on-premises Active Directory** (if applicable) or directly in **Entra ID**.
* **Detailed Metadata:** Profiles contain job titles, office locations, and replicated on-prem details (e.g., seeing which **Organizational Unit (OU)** a user belongs to in the local domain).

<img width="1398" height="777" alt="image" src="https://github.com/user-attachments/assets/419fd1ec-a1a7-4011-bc65-00163cd44686" />


---
