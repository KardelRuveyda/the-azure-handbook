# CHAPTER 07: Getting Started with Azure and Subscription Models

To truly master Azure, watching videos or reading documentation is not enough. You must gain **hands-on experience**. This chapter explains how to access Azure, the different account types available, and how organizations manage their subscriptions and costs.

---

## 1. The Core Principle: "Pay-As-You-Go"
Azure operates on a **consumption-based model**, meaning you pay only for the resources you use. To manage your budget effectively, remember these rules:
* **Shut down resources:** Turn off virtual machines or services when they are not in use.
* **Scale down:** Reduce the capacity of your services during low-traffic periods.
* **Use Tags:** Label resources to see which department or project is spending the budget.

---

## 2. Options for Beginners and Individuals
Microsoft provides several ways to start learning without a large initial investment.

### A. The Azure Free Account
This is the most popular starting point for students and new learners. It includes:
1.  **$200 Credit:** For the first 30 days, you can explore almost any service.
2.  **12 Months of Free Services:** Access to popular services (like SQL databases or AI tools) for a full year within specific limits.
3.  **Always Free Services:** Over 55 services (like Azure Functions or Cosmos DB) stay free forever as long as you stay within the usage limits.

### B. Visual Studio Subscriptions
If you have a Visual Studio license through your work or school, you receive monthly credits automatically:
* **Enterprise License:** $150 per month.
* **Professional License:** $50 per month.
> **Note:** These credits are intended for testing and development, not for running production business workflows.

---

## 3. Business Subscription Models
As companies grow, they need professional ways to manage billing and security. Here are the primary methods:

| Model | Best For | Description |
| :--- | :--- | :--- |
| **Pay-As-You-Go** | Small Teams | A simple model where you link a credit card and pay the monthly bill based on usage. |
| **Enterprise Agreement (EA)** | Large Companies | A formal contract for large-scale use. It allows for advanced management, departments, and potential discounts. |
| **Cloud Service Provider (CSP)** | Outsourced IT | You purchase Azure through a partner (reseller) who provides extra support and value-added services. |

---

## 4. Organizing the Cloud Environment
Large organizations use a hierarchy to stay organized and secure. 

* **Microsoft Entra ID (formerly Azure AD):** This is the identity provider where all your user accounts, devices, and permissions live.
* **Management Groups:** These are containers that allow you to apply policies and security rules to multiple subscriptions at once.
* **Subscription Organization:** You can group your work based on:
    * **Functional Teams:** (e.g., Sales, Legal, Marketing)
    * **Business Divisions:** (e.g., Windows, Bing, Xbox)
    * **Geographic Regions:** (e.g., North America, Europe, Asia)

---

### Key Takeaway
Whether you are using a free trial or an Enterprise Agreement, the goal is the same: **Efficiency**. Use the free tiers to experiment, but always monitor your consumption to avoid unnecessary costs.

---