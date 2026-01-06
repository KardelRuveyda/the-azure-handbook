# CHAPTER 06: Exploring Azure Services

Once you start your journey in Azure, you will quickly see that it is not just one thing. Azure is a **massive toolbox** with hundreds of different services. Whether you need to run a simple website, analyze huge amounts of data, or build the next great AI, Azure has a tool for you.

Because there are so many services, it can feel a bit confusing at first. In this chapter, we will break down the most important categories so you can choose the right tool for your project.

---

## 1. The Main Categories of Azure

Microsoft organizes its services into categories. This helps you find what you need quickly. Here are the most common areas:

* **Compute:** These are the "engines" that run your applications (Virtual Machines, Containers).
* **Networking:** This is how your services talk to each other and the internet.
* **Storage:** This is where you keep your files, disks, and data.
* **Databases:** Organized systems for managing your information (SQL, NoSQL).
* **AI + Machine Learning:** Tools for building "smart" applications.
* **Analytics:** Services for processing and understanding big data.
* **Security:** Tools to protect your identity and your resources.

<img width="1579" height="944" alt="image" src="https://github.com/user-attachments/assets/f3bb3803-2963-4fa0-8e92-d50958410dbf" />

---

## 2. Compute: Running Your Applications

Compute is usually where most people start. Azure offers many ways to run your code, depending on how much control you want.

### Virtual Machines (VMs)
You can run **Windows** or **Linux** virtual machines. If you already use **VMware** in your own office, you can even run VMware-based services directly in Azure.

### Scale Sets
If you expect a lot of traffic (like our Trabzonspor example), you can use **Virtual Machine Scale Sets**. These automatically add or remove VMs based on how busy your application is.

### Containers and Modern Apps
If you want to be more modern, Azure offers:
* **Azure Kubernetes Service (AKS):** For managing complex container environments.
* **Azure Container Apps:** A simpler way to run containers without managing the underlying servers.

<img width="771" height="434" alt="image" src="https://github.com/user-attachments/assets/7ed12156-f60a-4898-9227-1da3d0f1e4ec" />

---

## 3. The New Frontier: AI and Machine Learning

The transcript mentions that AI is one of the most exciting parts of Azure today. Microsoft provides many "ready-to-use" AI services so you don't have to be a scientist to use them.

* **Azure OpenAI Service:** This gives you access to powerful large language models (like the ones used for ChatGPT).
* **AI Search:** This is great for creating "semantic indexes." It helps your applications find and understand information more like a human does.
* **Bot Services:** For creating intelligent chat bots.
* **Video Indexer:** A service that can "watch" a video and tell you what is happening, who is speaking, and what words are being used.

<img width="333" height="151" alt="image" src="https://github.com/user-attachments/assets/7f5a2d21-b832-4346-a87e-4ef919804d35" />


---

## 4. Databases and Storage

Every application needs to save data. Azure offers many different "flavors" of databases:
* **Relational Databases:** Like Azure SQL, MySQL, and PostgreSQL. These are great for structured data.
* **NoSQL Databases:** Like **Azure Cosmos DB**. This is perfect if you need a database that works globally with very high speed.
* **Caching:** Tools like **Azure Cache for Redis** help your applications run faster by keeping frequently used data in memory.

<img width="1112" height="552" alt="image" src="https://github.com/user-attachments/assets/46586ffb-3369-40ec-b89c-a2db66bede4c" />

---

## 5. How to Choose? (The Right Tool for the Job)

With so many options, how do you decide what to use?
1.  **Understand your needs:** Do you need full control over the Operating System? (Use VMs). Or do you just want to upload your code? (Use App Services).
2.  **Take your time:** The transcript says, "It’s going to take you some time" to understand everything. Don't try to learn all 200+ services in one day.
3.  **Start with the basics:** Learn Compute, Networking, and Storage first. Everything else is built on top of those three.


