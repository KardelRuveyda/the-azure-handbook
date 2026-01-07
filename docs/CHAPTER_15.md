# CHAPTER 15: Security Groups and Dynamic Membership Logic

Groups are the primary tool for managing access to resources, applications, and licenses. Granting permissions directly to individual users leads to "ever-creeping" sets of permissions.

---

## 1. Types of Groups
* **Security Groups:** Used for granting permissions, access to apps, and assigning licenses.
* **Microsoft 365 Groups:** Best for collaboration, providing access to SharePoint, Teams, and shared mailboxes.


<img width="1393" height="686" alt="image" src="https://github.com/user-attachments/assets/040a2deb-bb98-4bad-bfb9-dd2d067ee3e0" />

## 2. Membership Types: Assigned vs. Dynamic
* **Assigned:** Manual management where you specifically add or remove members.
* **Dynamic (User or Device):** Membership is controlled by automated **Rules** based on attributes. If an attribute changes, Entra automatically puts the user "in or out" of the group.

<img width="1221" height="692" alt="image" src="https://github.com/user-attachments/assets/8856be4b-8589-4cdb-ab6b-3a8b54a24c10" />


## 3. Dynamic Logic: The "Galactic Exploration Corps" Example
Dynamic groups allow for powerful, automated governance based on job roles and timelines.

### Example A: Job Titles (The Exploration Corps)
* **The Rule:** `(user.jobTitle -startsWith "Explorer")`.
* **The Mechanics:** Any user with a job title starting with "Explorer" (e.g., Explorer-Commander, Explorer-Pilot) is automatically added to the **Galactic Corps Group**.
* **The Exit:** If an explorer retires and their title changes to **"Base Archivist,"** they no longer match the rule. They fall out of the group immediately and lose all permissions associated with being an active explorer.

### Example B: Employee Hire Dates
* **The Rule:** `(user.employeeHireDate -ge (System.DateTime.Now - 365 days))`.
* **The Logic:** This rule targets "New Joiners." Anyone whose hire date is within the last year is a member.
* **The Automation:** Once they pass their 365th day at the company, they automatically lose access to "New Joiner" resources because they no longer fit the criteria.

<img width="755" height="651" alt="image" src="https://github.com/user-attachments/assets/77bf2b36-e333-41df-8b88-f843531cb746" />


---
