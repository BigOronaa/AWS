# **AWS Research Project**

## **1. What is Cloud Computing?**
Cloud computing is the delivery of computing services like servers, storage, databases, networking, and software over the internet ("the cloud"). It allows users to access resources on demand without needing to own or manage physical hardware.  

**Key characteristics:**  
- **On-demand access:** Resources are available whenever needed.  
- **Scalability:** Can easily increase or decrease resources based on demand.  
- **Pay-as-you-go:** Users only pay for what they use.  
- **Accessibility:** Access from anywhere with an internet connection.  

**Difference from on-premise:**  
Traditional on-premise infrastructure requires purchasing and maintaining physical servers. Cloud computing, however, shifts this to virtual resources managed by providers like AWS, reducing upfront costs and maintenance.

---

## **2. Types of Cloud Computing Services**

| Type | Description | Example | Use Case |
|------|--------------|----------|-----------|
| **IaaS (Infrastructure as a Service)** | Provides virtualized computing resources like servers and storage. | Amazon EC2, Google Compute Engine | Hosting websites or applications where you manage OS and runtime. |
| **PaaS (Platform as a Service)** | Offers an environment to build and deploy applications without managing the underlying hardware. | AWS Elastic Beanstalk, Google App Engine | Developing and deploying web apps quickly. |
| **SaaS (Software as a Service)** | Delivers software applications over the internet on a subscription basis. | Gmail, Salesforce | Using ready-made applications like email or CRM tools. |

---

## **3. Cloud Deployment Models**

| Model | Description | Example Scenario |
|--------|--------------|------------------|
| **Public Cloud** | Services are hosted and managed by a third-party provider and shared by multiple users. | Startups hosting apps on AWS or Azure for scalability. |
| **Private Cloud** | Dedicated infrastructure for one organization, either on-premise or hosted by a third party. | Banks and government institutions needing high security. |
| **Hybrid Cloud** | Combination of public and private clouds to balance flexibility and control. | Large companies storing sensitive data privately while using public cloud for general operations. |

---

## **4. Benefits of Cloud Computing**
- **Cost Efficiency:** No upfront cost for hardware; pay only for usage.  
- **Scalability:** Instantly add or remove resources as demand changes.  
- **Reliability:** Redundant data centers ensure high uptime.  
- **Speed of Deployment:** Applications and services can be deployed in minutes.  
- **Global Reach:** Services can be accessed and deployed worldwide.  

---

## **5. Concerns around Cloud Computing**
- **Data Security:** Risk of unauthorized access to stored data.  
- **Compliance Issues:** Must meet laws like GDPR or HIPAA for data privacy.  
- **Vendor Lock-in:** Difficult to move workloads between providers.  
- **Downtime:** Internet dependency and potential service outages.  

---

## **6. Basic Cloud Architecture**

**Diagram (Text Representation):**

      +------------------+
      |     Internet     |
      +--------+---------+
               |
       +-------+--------+
       |   AWS VPC       |
       | (Virtual Network)|
       +-------+--------+
               |
 +-------------+-------------+
 |                           |


**Explanation:**  
- **EC2 (Compute):** Runs virtual servers for applications.  
- **S3 (Storage):** Stores application data, backups, and files.  
- **VPC (Networking):** Creates a secure virtual network for communication between services.

---

## **7. Explanation of Terms**

- **Fault Tolerance:** System’s ability to continue functioning even when part of it fails. *(Example: AWS Auto Scaling replacing failed EC2 instances.)*  
- **High Availability:** Ensures uptime and minimal downtime. *(Example: Deploying in multiple AWS Availability Zones.)*  
- **Scalability:** Ability to handle increased workload by adding more resources. *(Example: Scaling EC2 instances based on traffic.)*  
- **Cost Optimization:** Using resources efficiently to reduce cloud spending. *(Example: Using AWS Cost Explorer or Reserved Instances.)*  
- **Serverless Computing:** Running code without managing servers. *(Example: AWS Lambda executing code on triggers.)*

---

## **8. Compliance Considerations in Cloud Computing**
Compliance ensures cloud operations follow data protection laws and industry standards. It’s crucial for maintaining trust and avoiding penalties.

**Key compliance measures:**  
- **Data Encryption:** Encrypt data in transit (SSL/TLS) and at rest.  
- **Access Controls:** Use IAM roles and least privilege principles.  
- **Audit Trails:** Enable logging and monitoring (e.g., AWS CloudTrail).  
- **Compliance Monitoring:** Continuously check compliance status using AWS Config.  

**Examples of Regulations:** GDPR (Europe), HIPAA (Healthcare), ISO 27001 (Security).

---

## **9. Choosing between Cloud and On-Premise Computing for Hosting a Java Containerized Application**

**Decision:**  
I would choose **Cloud Computing (AWS)** over on-premise because:  
- **Scalability:** Easily handle up to 500 users during peak times using auto-scaling.  
- **Cost:** Pay only for active usage instead of buying expensive servers.  
- **Flexibility:** Quickly deploy updates and scale infrastructure.  
- **Reliability:** High uptime with AWS’s global data centers.

**Basic Architecture Diagram:**

       +------------------------+
       |        Users (500)     |
       +-----------+------------+
                   |
           +-------+--------+
           |   AWS Load     |
           |   Balancer     |
           +-------+--------+
                   |
    +--------------+---------------+
    |                              |


**Explanation:**  
- Users connect through a **Load Balancer**.  
- **EC2 Instances** host the Java containers (e.g., via Docker).  
- **S3 or RDS** stores data and assets.  
- Auto-scaling ensures smooth performance even at 500 users peak load.
