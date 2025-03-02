# -gcp-auto-scaling-manual
GCP Auto-Scaling VM Setup (Manual Deployment)

This repository contains documentation for **manually** setting up an **auto-scaling VM instance group** in **Google Cloud Platform (GCP)**.

---

## 1. Project Details  
- **Cloud Provider:** Google Cloud Platform (GCP)  
- **Project Name:** `vcc-assignment-2-452218`  
- **Compute Instance:** `instance-group-1-h1s6`  
- **Deployment Method:** **Manual (GCP Console + gcloud CLI)**  
- **Auto-Scaling Metric:** CPU utilization **above 50%**  
- **Firewall Rules:** Allow **HTTP (80)** and **SSH (22)**  

---

##  2. Architecture Design  
Below is the **architecture diagram** representing the **Auto-Scaling VM setup in GCP**.

📌 **Architecture Diagram will be uploaded soon.**  

---

## 3. Steps to Deploy Auto-Scaling in GCP  

### **🔹 1. Authentication & IAM Setup**  
1. Authenticate using:  
   ```bash
   gcloud auth login

	2.	Set the active project:

gcloud config set project vcc-assignment-2-452218


	3.	Assign IAM roles:

gcloud projects add-iam-policy-binding vcc-assignment-2-452218 \
    --member=user:M23AID019@iitj.ac.in --role=roles/compute.admin

🔹 2. Create a Compute Instance in GCP Console
	1.	Go to Compute Engine > VM Instances in GCP Console.
	2.	Click “Create Instance”, and configure:
	•	Machine Type: e2-medium
	•	Boot Disk: Ubuntu 22.04 LTS
	•	Firewall: ✅ Allow HTTP, ✅ Allow HTTPS
	3.	Click “Create”.

🔹 3. Configure Firewall Rules
	1.	Go to VPC Network > Firewall.
	2.	Create a firewall rule to allow HTTP and SSH traffic.

🔹 4. Test Auto-Scaling by Increasing CPU Load
	1.	SSH into the instance:

gcloud compute ssh instance-group-1-h1s6 --zone=asia-south1-c


	2.	Run a CPU stress test to trigger auto-scaling:

sudo apt install -y stress-ng
stress-ng --cpu 2 --timeout 600 &


	3.	Monitor auto-scaling:
	•	Go to Compute Engine > Instance Groups.
	•	You should see new instances being created as CPU load increases.



This repository contains documentation for manual deployment of an auto-scaling VM in GCP. It does not include Terraform scripts since the deployment was done via GCP Console and gcloud CLI.

