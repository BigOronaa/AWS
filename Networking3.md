# Configuring a Secure AWS Environment to Meet Vendor A’s Security Requirements


The goal of this project is to design a secure and compliant network architecture that enables Kubernetes services hosted in a private AWS subnet to communicate with Vendor A’s systems. Vendor A requires that all communication occurs over a **site-to-site VPN connection** and that **all outbound requests originate from a single, specific private IP address**.

This solution describes how to configure the environment to meet these security and connectivity requirements effectively.

---

## **1. Network Infrastructure Design**

A dedicated **Virtual Private Cloud (VPC)** should be set up to host the Kubernetes cluster and supporting network components.

### **Key Steps:**

1. **Create a VPC**
   - Define a CIDR block, for example, `10.0.0.0/16`.
   - Ensure sufficient IP range for future scaling.

2. **Create Subnets**
   - **Public Subnets**: For resources that require limited internet or external access (e.g., NAT instance, VPN gateway).
   - **Private Subnets**: For internal resources such as Kubernetes worker nodes and services.

3. **Configure Route Tables**
   - Public route table routes traffic to the **Internet Gateway (IGW)**.
   - Private route table routes outbound traffic via a **NAT instance** for controlled egress.

4. **Deploy Security Groups and Network ACLs**
   - Restrict access based on least privilege.
   - Allow necessary traffic only between trusted networks.

---

## **2. Kubernetes Cluster Deployment**

A **Kubernetes cluster** should be deployed within the private subnets to ensure that no public exposure occurs.

### **Configuration Guidelines:**
- Use **Amazon EKS** or a self-managed cluster on EC2 instances.
- Deploy an **NGINX Ingress Controller** to manage internal traffic flow.
- Configure cluster networking with **Amazon VPC CNI Plugin** for direct pod-level networking within the VPC.

This setup ensures that workloads operate securely and privately while maintaining flexibility in traffic management.

---

## **3. Site-to-Site VPN Configuration**

A **site-to-site VPN connection** ensures encrypted communication between the AWS VPC and Vendor A’s network.

### **Configuration Steps:**

1. **Create a Customer Gateway (CGW)**
   - Use Vendor A’s public IP and ASN details.

2. **Create a Virtual Private Gateway (VGW)**
   - Attach the VGW to the AWS VPC.

3. **Establish VPN Connection**
   - Configure the tunnel with shared keys or certificates.
   - Use **static** or **dynamic routing (BGP)** based on Vendor A’s preference.

4. **Update Route Tables**
   - Add routes in private subnets pointing Vendor A’s network (e.g., `172.16.0.0/16`) to the VPN connection.

This setup encrypts data in transit and establishes a direct, secure communication link between both environments.

---

## **4. NAT Instance for Outbound Traffic Control**

To satisfy the single private IP whitelisting requirement, a **custom NAT instance** should be deployed.

### **Setup Steps:**

1. **Launch an EC2 Instance**
   - Use Amazon Linux 2 AMI.
   - Place the instance in a public subnet.
   - Assign a **static private IP** (e.g., `10.0.1.10`) for Vendor A to whitelist.

2. **Modify Instance Attributes**
   - Disable **Source/Destination Check**.
   - Enable **IP forwarding** in the instance configuration.

3. **Configure iptables for SNAT**
   ```bash
   sudo sysctl -w net.ipv4.ip_forward=1
   sudo iptables -t nat -A POSTROUTING -o eth0 -j SNAT --to-source 10.0.1.10
   ```

4. **Ensure High Availability**
   - Use an Auto Scaling Group or Launch Template to replace failed NAT instances.
   - Optionally use **AWS Transit Gateway** for scalable multi-VPC routing.

This configuration ensures all outbound traffic appears from the single private IP approved by Vendor A.

---

## **5. Routing Configuration**

The route tables must direct Kubernetes traffic correctly through the NAT instance and VPN connection.

### **Routing Design:**
- Private subnet routes → NAT instance → VPN Gateway → Vendor A’s network.
- Ensure no conflicting routes exist that bypass the VPN.

Example route table entry:
```
Destination: 172.16.0.0/16
Target: nat-instance-id
```

---

## **6. Connectivity Testing and Verification**

Once the setup is complete, connectivity testing validates compliance and functionality.

### **Testing Steps:**
1. Deploy a test pod in the Kubernetes cluster.
2. Attempt to access Vendor A’s internal endpoint.
3. Ask Vendor A to verify that all requests appear from the whitelisted private IP.
4. Use `traceroute` or `curl` commands inside the pod for path verification.

Successful testing confirms that both VPN and NAT configurations function correctly.

---

## **7. Security and Monitoring Enhancements**

To ensure long-term security and observability:

- Enable **VPC Flow Logs** and send them to **CloudWatch** or **S3** for monitoring traffic.
- Apply strict **IAM roles and policies** to restrict access to VPN and NAT configurations.
- Regularly rotate VPN credentials and review routing rules.
- Use **AWS Config** and **GuardDuty** for continuous compliance monitoring.

---

## **8. Expected Outcome**

By implementing the described configuration:

- All traffic between AWS and Vendor A travels over a secure VPN tunnel.
- Vendor A receives traffic from a single, consistent private IP address.
- The architecture maintains confidentiality, integrity, and security of all transmitted data.

---

## **Conclusion**

The proposed architecture enables a secure, scalable, and compliant network connection between AWS-hosted Kubernetes services and Vendor A’s environment.  
It meets both **VPN encryption** and **private IP whitelisting** requirements while maintaining best practices in cloud networking, routing, and access control.
