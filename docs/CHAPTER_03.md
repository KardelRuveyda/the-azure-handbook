# CHAPTER 03: Types of Service & The Shared Responsibility Model

When we talk about cloud services, the core concept is not just technology—it is about **shifting responsibility**.

As we move from traditional on-premises environments to the cloud, we shift the burden of managing infrastructure to the provider. While costs may appear to rise as you move up the service levels, this is offset by the fact that you only pay for what you use and you are freed from managing "undifferentiated heavy lifting" (tasks that don't add direct business value).

To understand this, we use the classic **Pizza Analogy**.

---

## 1. The Pizza Analogy: A Model of Responsibility

Imagine you want a pizza. How you get that pizza determines what you are responsible for versus what someone else provides.

### On-Premises (Home Cooking)
* **Concept:** You make the pizza from scratch at home.
* **Your Responsibility:** You provide the dough, sauce, cheese, toppings. You own the oven, the gas/electricity to run the fire, the dining table, and the drinks. You cook it and clean up.
* **Summary:** You manage **everything**.

### Infrastructure as a Service (Take and Bake)
* **Concept:** You go to a shop that prepares the raw pizza, but you cook it at home.
* **The Provider:** Gives you the dough, sauce, toppings, and cheese (the underlying infrastructure).
* **Your Responsibility:** You provide the oven (fire/heat), the table, and the drinks. You are responsible for the actual cooking process.
* **Summary:** You manage the **cooking environment** and the **dining experience**.

### Platform as a Service (Pizza Delivery)
* **Concept:** You order a pizza to your door.
* **The Provider:** Makes the pizza and cooks it. They handle the infrastructure and the "fire."
* **Your Responsibility:** You provide the dining table and the drinks. You just need a place to eat it.
* **Summary:** You focus only on **consumption environment** (application/data).

### Software as a Service (Dining Out)
* **Concept:** You go to a restaurant.
* **The Provider:** Provides the ingredients, cooks the pizza, serves the drinks, provides the table, and cleans the dishes.
* **Your Responsibility:** You just eat.
* **Summary:** You manage **almost nothing** except the consumption.

---

## 2. The Technical Stack: Mapping Pizza to Cloud

In the technical world, we replace cheese and ovens with the compute stack. As we move up the layers, the cloud provider takes over more of the stack below:

1.  **Physical Infrastructure:** Networking, Storage, Servers.
2.  **Virtualization:** The Hypervisor.
3.  **Operating System (OS):** Windows, Linux.
4.  **Middleware & Runtime:** .NET, Java, Messaging.
5.  **Application:** The code providing business function.
6.  **Data:** The information being processed.

---

## 3. The Three Main Service Models

### IaaS: Infrastructure as a Service
This is the closest to the "Take and Bake" pizza.
* **What the Provider manages:** Physical network, storage, servers, and the **Hypervisor** (e.g., Hyper-V in Azure).
* **What YOU manage:** You are handed a Virtual Machine (VM). You are responsible for the **Operating System** inside that VM.
    * Patching, backups, antivirus, and configuration.
    * Middleware, runtimes, application code, and data.
* **Use Case:**
    * **Lift and Shift:** Migrating on-prem servers to the cloud without changing them.
    * **OS Control:** When you need to install specific third-party software that requires direct OS interaction.
    * *Note:* In the cloud, you never get access to the physical server or hypervisor; your control starts at the OS level.

### PaaS: Platform as a Service
This is the "Pizza Delivery." The provider gives you a place to run your code, but hides the underlying complexity.
* **What the Provider manages:** Hardware, Hypervisor, **Operating System**, Middleware, and Runtimes.
    * They handle OS patching, antivirus, and version updates for you.
* **What YOU manage:** You focus strictly on your **Application** and your **Data**.
* **Nuance (Databases):** Managed databases (like Azure SQL Database) are considered PaaS. Even though it is a database, you must still provide the "business function" (the schema, the queries, the data) on top of it.
* **Use Case:** Developers who want to deploy code (Web Apps, Logic Apps, Functions) without worrying about maintaining Windows/Linux servers.

### SaaS: Software as a Service
This is "Dining Out." The software provides the direct business function.
* **What the Provider manages:** Everything from the hardware up to the Application itself.
* **What YOU manage:** Configuration of the software and your **Data**.
* **Examples:** Microsoft 365, Dynamics 365, Minecraft Realms (where they provide the world for you).
* **Use Case:** Common business requirements (Email, Collaboration, CRM) where you don't need to build a custom solution.

---

## 4. Critical Concepts

### The "Cloud Cadence"
One of the biggest advantages of moving up the stack (PaaS/SaaS) is the Cloud Cadence.
* **Old Way:** Every 3 years, you get a massive new version of Windows Server.
* **Cloud Way:** Constant, incremental new capabilities are introduced.
* By using SaaS/PaaS, you automatically get these new features, resilience improvements, and value-adds without having to perform manual upgrades.

### Shared Responsibility (The "Undrawn Lines")
Even in SaaS (Restaurant), you are never *completely* free of responsibility. There are three things the customer always owns, regardless of the service type:
1.  **Data:** You are responsible for data classification, retention, rights management, and deletion.
2.  **Identity:** You manage your accounts (e.g., Entra ID/Active Directory), MFA, and access policies.
3.  **Devices:** You manage the security of the endpoints (phones, laptops) accessing the service (e.g., using Microsoft Intune).

---

## 5. Summary: How to Choose?


1.  **SaaS First:** If a software exists that meets your business need (e.g., Microsoft 365 for email), use it. Why build and patch an Exchange server if you don't have to?
2.  **PaaS Second:** If you must build a custom app, try PaaS (App Service, Functions). Focus on your code, not the OS.
3.  **IaaS Last:** Use IaaS only if you need specific control over the Operating System or are doing a quick migration where you can't refactor the application yet.

> **Key Takeaway:** The general rule in life (and cloud) is: **The less we are responsible for that isn't key to our core purpose, the better.**

## 6. A Developer's Perspective: Real-World Scenarios

As a developer, your primary goal is to deploy code, not manage cables or update Windows. Here is how you map your coding needs to Azure services:

### PaaS: The Developer's Gold Standard
This is where modern development happens. You want to push your code and have it run.
* **Scenario:** You have a Node.js, Python, or .NET web application.
* **The Solution:** Use **Azure App Service**. You don't create a VM; you don't install IIS/Nginx. You just deploy the code.
* **Scenario:** You need a database.
* **The Solution:** Use **Azure SQL Database** or **Cosmos DB**. You get a connection string, and Azure handles the backups and updates.

### IaaS: The "Strict Control" Option
Use this only when you are forced to access the Operating System directly.
* **Scenario:** You have a legacy application that requires a specific registry change or a custom installation on the C: drive.
* **The Solution:** Use **Azure Virtual Machines**. It is like having a remote computer where you must install and configure everything manually.

### SaaS: Integration over Creation
Don't reinvent the wheel. If a feature exists as a service, integrate it.
* **Scenario:** You need a login screen and user management.
* **The Solution:** Use **Microsoft Entra ID**. Don't write your own auth database.
* **Scenario:** You need to host your Git repositories.
* **The Solution:** Use **Azure DevOps** or **GitHub**.

### Developer Decision Matrix

| Your Requirement | Service Model | Azure Example |
| :--- | :--- | :--- |
| "I have a standard API or Web App." | **PaaS** | Azure App Service |
| "I need to run a single function (e.g., resize image)." | **PaaS (Serverless)** | Azure Functions |
| "I need a database." | **PaaS** | Azure SQL / Cosmos DB |
| "I have a legacy .exe that needs OS registry access." | **IaaS** | Azure Virtual Machine |
| "I am using Docker Containers." | **PaaS** | Azure Kubernetes (AKS) / Container Apps |
| "I need to send emails." | **SaaS** | SendGrid / M365 Integration |