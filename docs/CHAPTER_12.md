# CHAPTER 12: Implementation — Tenants, Domains, and Licensing

This chapter covers how to get started with Entra ID and how to manage your organization's digital identity environment.

---

## 1. Getting Your Entra Tenant
**You probably already have it.** If your organization uses Microsoft 365, Dynamics 365, or an Azure Subscription, an Entra Tenant was created automatically.
* **The Tenant:** This is your dedicated directory instance containing your users, groups, and policies.
* **Changing Directories:** While you can change which directory an Azure subscription trusts, **it is extremely dangerous.** It will break all existing RBAC assignments and managed identities.

---

## 2. Managing Domains
* **The Default Name:** Every tenant starts with a name like `company.onmicrosoft.com`.
* **Custom Domains:** You should add custom DNS names (e.g., `company.net`). You prove ownership by adding a TXT record to your DNS zone.
* **Primary Domain:** Once verified, you set the custom domain as the **Primary**, so users can log in with a professional email address.

---

## 3. Licensing Skus (Per-User, Per-Month)
Entra ID uses a per-user licensing model. You can mix and match licenses based on user needs:
* **Free:** Basic identity features included with Azure/M365.
* **P1:** Adds **Conditional Access**, advanced reporting, and self-service password reset.
* **P2:** Adds **Identity Protection** (AI-based risk detection) and **Privileged Identity Management (PIM)**.
* **Entra Suite:** The highest tier, adding Private Access and Verified ID features.