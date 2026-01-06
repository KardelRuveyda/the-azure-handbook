# CHAPTER 16: Non-Human Identities (Service Principals & Managed Identities)

Automations and applications require identities that can operate without a human present.

---

## 1. Service Principals (App Registrations)
When an app or automation needs to create resources, it uses a **Service Principal**. 
* **Authentication:** Uses **Secrets**, **Certificates** (preferred), or **Federated Credentials**.
* **OIDC Federation (GitHub Example):**
    * A **GitHub Actions** workflow needs to create an Azure resource.
    * Instead of storing a secret in GitHub, the workflow gets a token from GitHub's IdP.
    * It presents this to Entra ID, which "swaps" it for an Entra token.
    * This allows the GitHub identity to act as a **DevOps Automation** identity in your tenant without any long-lived secrets.

## 2. Managed Identities
The "Golden Standard" for Azure resources. It removes the need for human secret management.
* **The Secret-less Flow:** An identity is tied to an Azure resource (e.g., an Azure Function). 
* **The Trust:** Because the **Azure Control Plane** knows the code is running on that specific resource, the resource can simply request a token, and Azure will provide it automatically.
* **Usage:** Use this so your function can talk to a Storage Account or SQL Database without storing any certificates or passwords in the code.



---