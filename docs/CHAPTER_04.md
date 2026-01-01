# CHAPTER 04: When and Why to Use Public Cloud

For many companies today, managing a data center is not their main job. A retail company wants to sell products, and a bank wants to manage money. They use IT to run their business, but they don't want to be in the "Data Center Business." 

Moving to the public cloud is about **shifting responsibility**. It allows you to focus on your business while the cloud provider handles the difficult infrastructure.

---

## 1. Shifting Responsibility: Focusing on the Business

When you move to the cloud, even at the basic level called **Infrastructure as a Service (IaaS)**, you stop worrying about physical problems.

* **No more physical hardware:** You don't have to manage physical servers, cables, or storage disks (SANs).
* **No more facility management:** You don't need to worry about cooling (AC), electricity, or backup generators.
* **Modernization:** The cloud makes it easy to move to better technologies like **Containers**, **App Services**, or **Serverless**. 



By shifting these responsibilities to a provider like Azure, you can spend your time on what really matters: **your applications and your customers.**

---

## 2. The "Utility" Model: Computing Like Electricity

In the old days, factories had to build their own generators to get electricity. Later, power companies started providing electricity as a service. Because these companies were so big, they could provide power much cheaper and more reliably.

**Computing is exactly the same today.** It is a "utility." Very few companies can run a data center as efficiently as a "Mega Cloud" provider like Microsoft.

### Efficiency and the Environment (PUE)
Cloud providers use a metric called **PUE (Power Usage Efficiency)** to measure how much power is actually used for computing versus cooling. 
* **Azure's PUE:** Azure is very efficient and stays close to **1.0**. This means almost all the electricity goes to the servers. 
* **Cost Savings:** Some companies spend more on their electricity bill for an old data center than they would spend on their entire Azure bill.

---

## 3. The Power of Elasticity: The "Trabzonspor" Example

Public cloud is great because it is **elastic**. It can grow or shrink based on your needs. Let’s look at a football club like **Trabzonspor** to understand why this is important.

### The Championship Peak
Imagine you manage the official **TS Club** online store:
1.  **Normal Days:** On a Tuesday morning, only a few fans are buying jerseys. You only need 1 or 2 servers.
2.  **Match Days:** On match days, more fans visit the site. You scale up to 5 servers.
3.  **The Championship Night:** The night Trabzonspor wins the Championship, hundreds of thousands of fans flood the site at the same time to buy a "Championship Jersey." 

### Why the Cloud Wins
* **On-Premises:** You would have to buy 100 servers just for that one championship night. For the rest of the year, those servers sit idle and waste money.
* **In the Cloud:** You scale up to 100 servers for that specific night. Once the celebration ends, you delete the extra resources. **You only pay for what you use.**

<img width="385" height="218" alt="image" src="https://github.com/user-attachments/assets/e38eb212-4a43-4d67-b043-20669cfd4ae0" />

---

## 4. Key Business Benefits

### Pay-As-You-Go (Consumption Model)
In the cloud, you are charged for what you consume. If you use a Virtual Machine for 12 hours, you pay for 12 hours—not for the whole month. If you buy a physical server, you are stuck with it for 3 to 5 years. In the cloud, if your needs change, you can delete a resource and create a new one instantly.

### Startups and "Failing Fast"
For a new company, the cloud is perfect:
* **No big upfront cost:** You don't need millions of dollars to start.
* **Scale with success:** As you get more customers, your bill grows, but so does your revenue.
* **Low risk:** If the business idea fails, you just turn off the cloud resources. You haven't lost money on expensive hardware.

### Predictable and Unpredictable Spikes
* **Predictable:** You know you will be busy every Friday night, so you schedule your servers to scale up.
* **Unpredictable:** A player's goal goes viral on social media, and suddenly your site gets a million hits. The cloud sees the high CPU usage and adds more servers automatically.

---

## 5. Summary: Why Choose Public Cloud?

| Advantage | What it means for you |
| :--- | :--- |
| **Global Reach** | You can place your app near your fans, whether they are in Trabzon or London. |
| **Resiliency** | Better options for Backup and Disaster Recovery (DR). |
| **Flexibility** | Change your server type or service type in minutes. |
| **Cost Efficiency** | No more paying for idle servers that you aren't using. |

> **Key Takeaway:** The public cloud allows you to modify your resources based on the work coming in. This is the most efficient and flexible way to run a modern business.
