
# AWS Research and Critical Thinking Questions

## Introduction to Cloud Computing Concepts

---

## 1. What is Cloud Computing?

Cloud computing is the delivery of computing resources—such as servers, storage, databases, networking, software, and analytics—over the internet (“the cloud”) instead of maintaining physical hardware on-premises.  
**Basic Characteristics:**  
- **On-Demand Access:** Users can access resources anytime without human intervention.  
- **Scalability:** Resources can be scaled up or down depending on usage.  
- **Elasticity:** Automatically adjusts to workload changes.  
- **Pay-as-you-go:** Users pay only for what they use.  
- **Global Reach:** Cloud providers offer data centers around the world for better performance and reliability.  

**Difference from On-Premise Infrastructure:**  
Traditional infrastructure requires buying and managing physical servers, storage, and networking equipment. Cloud computing eliminates this need by offering virtualized, scalable resources that are maintained by cloud providers.

---

## 2. Types of Cloud Computing Services

### **Infrastructure as a Service (IaaS):**
Provides virtualized hardware resources like compute, storage, and networking.  
**Example:** Amazon EC2, Google Compute Engine, Microsoft Azure Virtual Machines.  
**Use Case:** Hosting virtual machines or servers.

### **Platform as a Service (PaaS):**
Provides an environment for developers to build, test, and deploy applications without managing infrastructure.  
**Example:** AWS Elastic Beanstalk, Google App Engine.  
**Use Case:** Building web applications quickly with managed services.

### **Software as a Service (SaaS):**
Provides fully functional applications over the internet.  
**Example:** Google Workspace, Salesforce, Microsoft 365.  
**Use Case:** Business productivity tools and CRM platforms.

---

## 3. Cloud Deployment Models

### **Public Cloud:**
Owned and operated by third-party providers (e.g., AWS, Azure). Multiple organizations share the same infrastructure.  
**Use Case:** Startups or small businesses needing cost efficiency and scalability.

### **Private Cloud:**
Exclusive cloud environment for a single organization, either hosted internally or externally.  
**Use Case:** Enterprises with strict security or compliance requirements.

### **Hybrid Cloud:**
Combination of public and private clouds, enabling data and application portability.  
**Use Case:** Businesses balancing sensitive workloads and flexible computing needs.

---

## 4. Benefits of Cloud Computing

- **Cost Efficiency:** Reduces capital expenditure by using a pay-as-you-go model.  
- **Scalability:** Dynamically scale resources based on demand.  
- **Reliability:** Cloud providers ensure redundancy and disaster recovery.  
- **Speed of Deployment:** Launch applications faster with automated provisioning.  
- **Innovation:** Enables rapid experimentation with minimal risk.

---

## 5. Concerns around Cloud Computing

- **Data Security:** Risks of data breaches and unauthorized access.  
- **Compliance Issues:** Challenges in meeting industry standards like GDPR or HIPAA.  
- **Vendor Lock-In:** Difficulty in migrating between providers due to proprietary technologies.  
- **Downtime:** Service outages may affect business operations.  
- **Data Privacy:** Risk of losing control over data stored on third-party infrastructure.

---

## 6. Basic Cloud Architecture

**Diagram Description:**  
```
[User] → [Internet] → [VPC] → [EC2 Instances]
                        ↳ [S3 Bucket for Storage]
                        ↳ [Load Balancer]
```

- **EC2 (Compute):** Hosts web or application servers.  
- **S3 (Storage):** Stores application files, images, and backups.  
- **VPC (Networking):** Provides isolated networking environment with subnets and routing.  
- **Load Balancer:** Distributes traffic across multiple EC2 instances for performance and reliability.

---

## 7. Explanation of Key Terms

- **Fault Tolerance:** System continues functioning even when components fail (e.g., multiple availability zones).  
- **High Availability:** Ensures minimal downtime with redundant components.  
- **Scalability:** Ability to handle increased workloads by adding resources.  
- **Cost Optimization:** Reducing costs through right-sizing and using reserved or spot instances.  
- **Serverless Computing:** Running code without provisioning servers (e.g., AWS Lambda).

---

## 8. Compliance Considerations in Cloud Computing

Compliance ensures that cloud operations meet legal, industry, and data protection requirements.  

**Key Requirements and Measures:**  
- **Data Encryption:** Protects data in transit and at rest using encryption keys.  
- **Access Controls:** Uses IAM (Identity and Access Management) to limit permissions.  
- **Audit Trails:** Tracks actions performed within the cloud environment for accountability.  
- **Compliance Monitoring:** Continuous assessments using tools like AWS Config and CloudTrail.

**Common Frameworks:** GDPR, ISO 27001, HIPAA, SOC 2.

---

## 9. Choosing between Cloud and On-Premise for a Java Containerized Application

### **Decision-Making Process:**
1. **Scalability:** Cloud provides auto-scaling for variable user loads.  
2. **Cost:** Pay for resources only when used.  
3. **Flexibility:** Easier deployment and CI/CD integration with container orchestration tools.  
4. **Reliability:** Built-in redundancy and managed services for uptime.  

**Choice:** Host in **Cloud (AWS ECS or EKS)** for agility, scalability, and lower maintenance.

### **Proposed Architecture for 500 Users (Peak Period):**
```
[Users] → [Application Load Balancer] → [ECS Cluster with 3 Containers]
                                           ↳ [RDS MySQL Database]
                                           ↳ [S3 Storage for Media]
                                           ↳ [CloudWatch for Monitoring]
```

---

