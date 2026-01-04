# CHAPTER 07: Getting Started with Azure and Subscription Models

To truly master Azure, watching videos or reading documentation is not enough. You must gain **hands-on experience**. This chapter explains the practical steps to access Azure, the various account types available, and how to manage costs and technical limits.

---

## 1. The Importance of Hands-On Learning
Learning Azure requires interaction with the platform. However, because Azure uses a **consumption-based model** (you pay for what you use), you must be disciplined:

* **Shut down resources:** Always turn off Virtual Machines (VMs) when they are not in use.
* **Scale down:** Reduce the capacity of services during testing.
* **Tagging:** Use **Tags** to organize resources. This helps you identify which person or department is consuming specific services.

---

## 2. Personal Account Options

### A. The Azure Free Account
This is the standard entry point for individuals. It consists of three tiers:
1.  **$200 Credit:** Available for the first 30 days to explore almost any service.
2.  **12 Months of Free Services:** Certain popular services remain free for a year within specific limits. Examples include:
    * **AI Document Intelligence:** 500 pages per month.
    * **Cosmos DB:** 400 request units per second with 25 GB of storage.
3.  **Always Free Services:** Some services (like certain AI Vision tools or Azure Functions) have a permanent free tier.

> **Note on Spending Limits:** Free accounts have a built-in spending limit to prevent accidental charges. If you want to continue testing after your $200 credit is finished, you can manually remove this limit, but your credit card will be billed for further usage.

### B. Visual Studio & MSDN Credits
If you have a professional subscription, you receive monthly credits that reset every month:
* **Visual Studio Enterprise:** $150/month.
* **MSDN Subscription:** $100/month.
* **Visual Studio Professional/Test:** $50/month.

---

## 3. Business Subscription Models

Organizations choose different paths depending on their size and needs:

| Model | Target Audience | Key Features |
| :--- | :--- | :--- |
| **Pay-As-You-Go** | Small Organizations | No long-term commitment; pay monthly via credit card as you consume resources. |
| **Enterprise Agreement (EA)** | Large Companies | Includes specific roles like **Enterprise Administrators** (who manage the overall enrollment) and **Account Owners** (who create and manage individual subscriptions). |
| **Cloud Service Provider (CSP)** | Outsourced Management | You work with a partner (reseller) who provides the services and often adds "value-add" management on top. |

---

## 4. Organizing Your Environment
Azure uses a hierarchy to manage identities and billing:
* **Microsoft Entra ID Tenant:** Formerly known as Azure AD, this is where all your accounts, identities, and devices are managed. It is similar to an old Active Directory domain but built for the cloud.
* **Management Groups:** These allow you to group multiple subscriptions together to apply governance and policies at a high level.
* **Subscription Grouping:** Large companies often organize subscriptions based on:
    * **Functional Teams:** (e.g., Sales, Legal, Marketing)
    * **Business Divisions:** (e.g., Windows, Bing)
    * **Geographic Regions:** (e.g., North America, Europe)

---

## 5. Understanding Limits and Quotas
Azure sets limits to **protect you from yourself**. These prevent a single user from accidentally creating a massive cloud bill or consuming all available resources in a region.

### Soft Limits vs. Hard Limits
* **Soft Limits (Quotas):** These are default caps (e.g., the number of CPU cores in a subscription). You can request an increase by going to the **"Usage + Quotas"** page in the portal and opening a service ticket.
* **Hard Limits:** These are absolute maximums (e.g., how many resource groups you can have per subscription) and generally cannot be changed.

### The Role of SKUs (Stock Keeping Units)
A **SKU** is essentially a "pricing tier" or "version" of a service (e.g., Basic, Standard, Premium). 
* Limits are often tied to the SKU; as you move to a higher SKU, the limits increase (e.g., more database instances or more compute power).
* Higher SKUs also unlock additional professional capabilities that are not found in the free or basic tiers.
