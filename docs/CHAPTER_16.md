# CHAPTER 16: Non-Human Identities (Service Principals & Managed Identities)

Automations and applications require identities that can operate without a human present.

---

## 1. Service Principals (App Registrations)

<img width="1887" height="789" alt="image" src="https://github.com/user-attachments/assets/9706372a-02f2-4f1f-8f9b-df75a99f5e89" />

When an app or automation needs to create resources, it uses a **Service Principal**. 
* **Authentication:** Uses **Secrets**, **Certificates** (preferred), or **Federated Credentials**.
* **OIDC Federation (GitHub Example):**
    * A **GitHub Actions** workflow needs to create an Azure resource.
    * Instead of storing a secret in GitHub, the workflow gets a token from GitHub's IdP.
    * It presents this to Entra ID, which "swaps" it for an Entra token.
    * This allows the GitHub identity to act as a **DevOps Automation** identity in your tenant without any long-lived secrets.


<img width="679" height="248" alt="image" src="https://github.com/user-attachments/assets/2c6e84d7-f6d7-420e-bfa0-8e0431628f3a" />


## 2. Managed Identities
The "Golden Standard" for Azure resources. It removes the need for human secret management.
* **The Secret-less Flow:** An identity is tied to an Azure resource (e.g., an Azure Function). 
* **The Trust:** Because the **Azure Control Plane** knows the code is running on that specific resource, the resource can simply request a token, and Azure will provide it automatically.
* **Usage:** Use this so your function can talk to a Storage Account or SQL Database without storing any certificates or passwords in the code.

<img width="975" height="632" alt="image" src="https://github.com/user-attachments/assets/d2ea684f-e307-4d75-8bc9-5c94948bfcfd" />


---
