# CHAPTER 12: Implementation — Tenants, Domains, and Licensing

This chapter covers how to get started with Entra ID and how to manage your organization's digital identity environment.

---

## 1. Getting Your Entra Tenant
**You probably already have it.** If your organization uses Microsoft 365, Dynamics 365, or an Azure Subscription, an Entra Tenant was created automatically.
* **The Tenant:** This is your dedicated directory instance containing your users, groups, and policies.
* **Changing Directories:** While you can change which directory an Azure subscription trusts, **it is extremely dangerous.** It will break all existing RBAC assignments and managed identities.

<img width="803" height="620" alt="image" src="https://github.com/user-attachments/assets/3672c84b-2313-4d75-940a-8d95a3082f8f" />


---

## 2. Managing Domains
* **The Default Name:** Every tenant starts with a name like `company.onmicrosoft.com`.
* **Custom Domains:** You should add custom DNS names (e.g., `company.net`). You prove ownership by adding a TXT record to your DNS zone.
* **Primary Domain:** Once verified, you set the custom domain as the **Primary**, so users can log in with a professional email address.

<img width="1200" height="707" alt="image" src="https://github.com/user-attachments/assets/0ff17c93-8510-46f1-8c6d-81802cce8839" />
<img width="413" height="265" alt="image" src="https://github.com/user-attachments/assets/76b30110-992c-449f-8897-cb3967d974ac" />
<img width="1200" height="707" alt="image" src="https://github.com/user-attachments/assets/1bf235bd-4108-4dc4-883f-cd363ae2ab19" />
<img width="609" height="472" alt="image" src="https://github.com/user-attachments/assets/2ac74fb9-7d2a-466a-a4f2-3d3036bc9f24" />

---

## 3. Licensing Skus (Per-User, Per-Month)
Entra ID uses a per-user licensing model. You can mix and match licenses based on user needs:
* **Free:** Basic identity features included with Azure/M365.
* **P1:** Adds **Conditional Access**, advanced reporting, and self-service password reset.
* **P2:** Adds **Identity Protection** (AI-based risk detection) and **Privileged Identity Management (PIM)**.
* **Entra Suite:** The highest tier, adding Private Access and Verified ID features.

https://learn.microsoft.com/en-us/entra/fundamentals/licensing
