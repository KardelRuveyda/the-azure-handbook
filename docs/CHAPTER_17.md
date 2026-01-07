# CHAPTER 17: The Bridge Between Local AD and Entra ID

This chapter explains how we move users from your local servers (Active Directory) to the cloud (Microsoft Entra ID) using the story of a tech company: **"Nova Innovations."**

---

## 1. The Main Rule: "The Boss" (Source of Truth)
In a hybrid setup, your local Active Directory (AD) is the **Source of Truth**. This means AD is the "Boss."

> **Example:** **Nova Innovations** undergoes a rebranding. Every employee needs their "Department" attribute changed from **"Sales"** to **"Global Growth."** The IT manager updates this in the **Local AD**.

* **Data Flow:** The bridge sees this change and moves it: **Local AD → Entra ID**. 
* **The Overwrite Rule:** If an employee, **John**, tries to change his department back to "Sales" in the Cloud Portal (because he likes the old name), the sync engine will catch him. It will say: *"The Boss (Local AD) says you are in Global Growth,"* and it will **delete John's change** to match the local server during the next sync.
* **Why?** We need one "Master Record" so that data stays consistent across the entire company.



---

## 2. The Tools: How do we do it?
**Nova Innovations** has two "engines" to choose from to build this bridge:

### A. Entra Connect Sync (The Classic "Heavy" Engine)
Think of this as a **Large Factory** installed on a Windows Server.
* **Internal Mechanics (The Kitchen):**
    1.  **Connector Spaces:** These are "Waiting Rooms." One room holds a mirror of the local AD data; the other holds a mirror of the cloud data.
    2.  **The Metaverse:** This is the "Engine Room" in the middle. It takes the data from both waiting rooms and **merges** them into one single identity. 
* **Maintenance:** You are the factory manager. You must manage the Windows OS, handle the database, and perform manual software updates.



### B. Entra Cloud Sync (The Modern "Light" Engine)
Think of this as a **Small Remote Sensor**. You install a tiny "agent" instead of a big factory.
* **Disconnected Forests:** Nova Innovations just bought a startup in London. The London office has its own network that **cannot talk** to the New York office. **Cloud Sync** can connect both networks to the same cloud tenant. The "Heavy Factory" (Connect Sync) cannot do this.
* **Tier 0 Security:** This agent can create and change users. Therefore, the server it lives on must be treated as a **Tier 0 Asset**—the highest security level. If a hacker gets into this server, they control the identity of your whole company.



---

## 3. The Rules of the Bridge (Topologies)
Microsoft has strict "laws" for **Nova Innovations** regarding how they connect:

* **The 1:1 Rule:** One cloud tenant can only have **one active** sync engine instance (Entra Connect) talking to it. 
* **The Staging Server:** Nova Innovations keeps a second server in **Staging Mode**. It watches the data but doesn't send it. If the main factory crashes, the Staging server is "promoted" to active to take over.
* **One AD to Many Clouds:** If Nova has a "Commercial Cloud" and a "Government Cloud," they can sync their local users to **both** using separate sync instances.
* **The "Write-back" Warning:** Only **one** cloud is allowed to send data *back* (Write-back) to the local AD. If both clouds tried to update John's local account at the same time, his account would be corrupted.

---

## 4. Automation: The HR Connection
Nova Innovations uses an **HR System** (like Workday) to automate the "Joiner-Mover-Leaver" process:

1.  **Alice** is hired. The HR manager enters her details into **Workday**.
2.  Workday tells Entra ID via the **Provisioning API**.
3.  Entra ID tells the **Local Agent** on Nova's server.
4.  The Agent creates Alice in the **Local AD**.
5.  The Bridge syncs Alice back up to **Entra ID**.
* **Result:** Alice is ready to work on day one without IT doing any manual work!

---

## 5. Summary Table 

| Feature | Entra Connect Sync | Entra Cloud Sync |
| :--- | :--- | :--- |
| **Complexity** | High (Heavy software + SQL) | Low (Lightweight agent) |
| **Maintenance** | High (You manage updates) | Low (Managed by Microsoft) |
| **Disconnected Networks** | No | **Yes (Big Advantage)** |
| **Internal Logic** | Metaverse & Connector Spaces | Cloud-based Logic |
| **Security** | Tier 0 Asset | Tier 0 Asset |

---