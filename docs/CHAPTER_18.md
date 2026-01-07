# CHAPTER 18: Understanding Authentication and Authorization in Microsoft Entra ID

This document explains the core concepts of identity management and the different ways Microsoft Entra ID handles user logins. 

---

## 1. Authentication vs. Authorization

It is common to mix these two terms, but they perform very different tasks in a security system.

<img width="850" height="380" alt="image" src="https://github.com/user-attachments/assets/f352b8b3-a45a-483c-966f-62c50adfef83" />


### **Authentication (AuthN): "Who are you?"**
Authentication is about **proving your identity**. You prove you are who you say you are by using one of these three factors:
* **Something you know:** Like a password or a PIN.
* **Something you have:** Like a smartphone to receive an SMS or a code from an app.
* **Something you are:** Biometric data like a fingerprint or a facial scan.

### **Authorization (AuthZ): "What can you do?"**
Authorization happens *after* you are authenticated. It defines what actions your identity is allowed to perform. For example, you are logged in, but are you allowed to delete a file or just read it?

---

## 2. Authentication Options in Entra ID

When you connect your office network (Active Directory) to the cloud (Entra ID), you have three main ways to check passwords:

### **A. Password Hash Sync (PHS) — *Most Recommended***
* **How it works:** Entra ID does not store your actual password. It takes a "fingerprint" (hash) of your password from your local server.
* **The Technical Process:** It creates a **"hash of the hash"** by adding a **per-user salt** and running it through **1,000 hashing iterations**. 
* **The "Fail-Safe":** If your office internet goes down, users can still log in because the cloud has its own "copy" to verify.

<img width="2004" height="839" alt="image" src="https://github.com/user-attachments/assets/955612c0-1f09-4582-96c7-8331f3169ab5" />


### **B. Pass-through Authentication (PTA)**
* **How it works:** Entra ID doesn't know your password at all. When you try to log in, Entra ID puts the request in a **Service Bus** queue. A small software **agent** on your local server picks it up, checks the password, and tells the cloud "Yes" or "No."
* **Benefit:** If you disable a user in your office, they are blocked from the cloud instantly.

<img width="3000" height="1434" alt="image" src="https://github.com/user-attachments/assets/6cb4c6e4-e057-42aa-a3f8-9f925b1a52d9" />


### **C. Federation**
* **How it works:** Entra ID sends the user to a completely different login page (like your company's own portal). That system checks the identity and gives the user a "token" to bring back to Entra ID.


---

## 3. Comparison Table

| Feature | Password Hash Sync (PHS) | Pass-through (PTA) | Federation |
| :--- | :--- | :--- | :--- |
| **Setup Complexity** | Very Low | Medium | High |
| **Dependency** | None (Cloud-based) | High (Local Servers) | Very High (External IdP) |
| **Dark Web Scanning**| Included | Not natively | Not natively |
| **Reliability** | **Highest** | Medium | Lowest |

---

## 4. The "Super Simple" Analogy: The Private Club


If Microsoft Entra ID was a **Private Nightclub**, here is how it would work:

### **Authentication vs. Authorization**
* **Authentication:** You show your ID to the bouncer at the door to prove you are "John Doe."
* **Authorization:** The bouncer looks at your wristband. If it’s gold, you can go to the VIP area. If it’s plastic, you stay on the dance floor.

### **The Three Hybrid Methods**
1.  **Password Hash Sync (PHS):** The bouncer has a **copy of the guest list** in his pocket. Even if the club's computer system crashes, he can still let you in because he has the list right there. (**Fastest and Safest**)
2.  **Pass-through Authentication (PTA):** The bouncer doesn't have a list. Every time someone arrives, he has to **use a walkie-talkie** to call the office inside the building to ask if you are allowed in. If the walkie-talkie breaks, no one gets in. (**Live Check**)
3.  **Federation:** The bouncer doesn't check IDs at all. He says, "Go to the hotel next door. If they give you a special coin, come back and show it to me, and I'll let you in." (**Complex and depends on the hotel**)

---

## 5. Final Recommendation
**Use Password Hash Sync (PHS).** It is the easiest to set up, it protects you from leaked passwords on the dark web, and it keeps working even if your local office has a power outage.
