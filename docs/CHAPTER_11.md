# CHAPTER 11: Mechanics of Microsoft Entra ID

**Microsoft Entra ID** (formerly Azure AD) is the Enterprise Identity Provider (IdP) for all Microsoft clouds. It is fundamentally different from traditional Active Directory.

---

## 1. Entra ID vs. Traditional Active Directory (ADDS)
As a professional, you must understand these technical differences:

| Feature | Active Directory (Traditional) | Microsoft Entra ID |
| :--- | :--- | :--- |
| **Connectivity** | Internal Corporate Network. | Open Internet / Cloud. |
| **Protocols** | Kerberos, NTLM, LDAP. | HTTPS, OIDC, OAuth 2.0, SAML. |
| **Structure** | Hierarchical (OUs). | Flat structure (Tenants and Groups). |
| **Connectivity** | Complex ports (RPC, DNS, etc.). | Encrypted Web Port (443). |
| **API** | LDAP. | Microsoft Graph (Restful API). |

---

## 2. Authentication (AuthN) vs. Authorization (AuthZ)
The **Identity Provider (IdP)** acts as the central hub:
1.  **Authentication (AuthN):** Proving who you are (Password, Passkey, Certificate, or MFA).
2.  **The Token:** The IdP issues a digital **Token** (like a passport).
3.  **Authorization (AuthZ):** The user presents the token to an application. The app trusts the IdP, reads the "claims" (Roles) in the token, and grants access.

---

## 3. Microsoft Graph: The API of the Cloud
To manage Entra ID today, we use the **Microsoft Graph**. 
* It is a single, restful API for all Microsoft cloud data (Entra, M365, Dynamics).
* We use the **Microsoft Graph PowerShell SDK** for automation.
* There are no "Organizational Units" (OUs) in Entra; it is a flat directory. For delegation, we use **Administrative Units**.