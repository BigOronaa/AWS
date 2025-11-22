# AWS Multi-Database Learning Project

This document captures my hands-on implementation of a learning project involving AWS databases, caching, serverless automation, analytics, monitoring, and cost optimization.

---

## **Implementation Steps**

### **1. Set Up an RDS Instance**
- I created a **MySQL RDS instance**.
- I Enabled **Multi-AZ deployment** for high availability.
- I Configured **automated backups and snapshots**.
- I Verified that the RDS instance was reachable and ready for integration.

---

### I added Screenshots
![alt text](images4/databasecreate.png)
![alt text](images4/dbinstance.png)
![alt text](images4/mySQL.png)
![alt text](images4/sqlTable.png)


### **2. Deploy a DynamoDB Table**
- I created the table **`users-nosql`** with a primary key and secondary indexes.
- I Inserted **sample records** using the **AWS CLI** and **Lambda functions**.
- I Enabled **on-demand scaling** to handle varying workloads.
- I Verified table accessibility and successful inserts.

---

### I added Screenshots
![alt text](images4/DynamoDBcreate.png)
![alt text](images4/indexcreate.png)
![alt text](images4/itemcreate.png)
![alt text](images4/)



### **3. Integrate ElastiCache for Caching**
- I deployed a **Redis cluster (`lab-redis`)** using ElastiCache.
- I Connected Redis with **RDS** to cache query results.
- I Configured **eviction policies** and **monitored cache usage**.
- I Tested cache invalidation triggered by Lambda updates.

---

### I added Screenshots
![alt text](images4/rediscluster.png)
![alt text](images4/redis-rds.png)
![alt text](images4/ttl.png)
![alt text](images4/pythontest.png)




### **4. Set Up Analytics Using Athena and S3**
- Instead of Redshift, I created an **S3 bucket** for storing structured data. Redshift did not give me access because of i am on free tier.
- I Configured **Athena** to query the S3 data.
- I Ran **analytical queries** for insights from large datasets.
- I Validated data retrieval and query execution.

---

### I added Screenshots
![alt text](images4/athenatable.png)
![alt text](images4/s3bucket.png)
![alt text](images4/query.png)
![alt text](images4/query2.png)
![alt text](images4/query3.png)
![alt text](images4/query4.png)
![alt text](images4/query5.png)
![alt text](images4/redshift.png)
![alt text](images4/uploadbucket.png)



### **5. Migrate Data Using AWS DMS**
- I set up **DMS** to migrate data to RDS.
- I Enabled **Change Data Capture (CDC)** for real-time synchronization.
- I Verified that migration was accurate and ongoing updates were captured.

---

### I added Screenshots
![alt text](images4/DMScreate.png)
![alt text](images4/taskcreated.png)
![alt text](images4/endpointscreate.png)



### **6. Automate Updates with AWS Lambda**
- I wrote a **Lambda function** to update DynamoDB from API requests.
- I Configured Lambda to **update RDS records** and **invalidate Redis cache** automatically.
- I Tested Lambda using PowerShell and API Gateway.
- I Confirmed data updates propagated correctly across RDS, DynamoDB, and Redis.

---

### I added Screenshots
![alt text](images4/lambda1.png)
![alt text](images4/lambdatest.png)
![alt text](images4/API.png)


### **7. Monitor Performance and Costs**
- I Enabled **CloudWatch monitoring** for RDS, DynamoDB, and Redis.
- I Created **alarms** for high query latency and high connections.
- I Reviewed metrics and ensured alarms triggered correctly.
- I Explored **cost optimization strategies**:
  - Reserved instances and auto-scaling for RDS/Aurora (limited by Free Tier).
  - Serverless Redis and auto-scaling for cost efficiency.

---

### I added Screenshots
![alt text](images4/rdsmonitor.png)
![alt text](images4/dynamoDBmonitor.png)
![alt text](images4/redismonitor.png)
![alt text](images4/alarm1.png)
![alt text](images4/alarm2.png)
![alt text](images4/dynamodbcost.png)
![alt text](images4)



### **Project Highlights**
- Implemented **multi-database architecture** with RDS, DynamoDB, and Redis.
- Built **serverless automation** using Lambda.
- Used **Athena + S3** for analytics instead of Redshift.
- Monitored performance via **CloudWatch** and configured alarms.
- Learned and applied **cost optimization strategies** in AWS.