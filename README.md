# 🔐 Configure Authentication for an Azure Web App

This project demonstrates how I implemented user authentication on an Azure-hosted web application using **Azure App Service Authentication/Authorization** (also known as Easy Auth). This is essential for securing access to web apps without writing any custom authentication logic.

---

## 🎯 Objective

To protect access to a deployed Azure web application by configuring authentication via Microsoft identity provider (Azure Active Directory), allowing only authenticated users to access the app.

---

## 🚀 What I Did

### 1. **Created and Deployed an Azure Web App**
- Used Azure App Services to deploy a simple web app.
- Selected the runtime stack and region.
- ![image](https://github.com/user-attachments/assets/b3c0b531-1b09-4f8b-a573-49c005970e2c) ![image](https://github.com/user-attachments/assets/22647472-2911-48a2-a718-70f41a5c58d3)
- ![image](https://github.com/user-attachments/assets/d931c867-ecf2-424d-9dcd-90a3b991060e)

### 2. **Enabled Authentication on the Web App**
- Enable authentication by using Microsoft Entra ID | Configure Microsoft Entra ID for the web app by using Microsoft as the identity provider.
- ![image](https://github.com/user-attachments/assets/84de7ada-ffba-42ed-aabf-e38e937afded) ![image](https://github.com/user-attachments/assets/09b9f56c-a0eb-454c-8005-0622d22d0f82)
- ![image](https://github.com/user-attachments/assets/142a0a1e-9c82-4767-a1bc-de91cdf3f742)
- •	Verify that the app has been registered in Microsoft Entra ID ![image](https://github.com/user-attachments/assets/40429952-7cd4-4ef2-95b3-66fc821345da)
  
### Configure Virtual Network Connectivity by Using Peering
![image](https://github.com/user-attachments/assets/9456b68a-c57b-44e1-9ef4-8547f7e450b9) ![image](https://github.com/user-attachments/assets/19bcec51-630f-4d6a-a618-1f8c38569704)
![image](https://github.com/user-attachments/assets/6466f1fa-da2b-4d66-b6b3-62309d1b7141) ![image](https://github.com/user-attachments/assets/a0bb474d-7e3a-4824-9cf4-eac549b76699)
![image](https://github.com/user-attachments/assets/62afeabb-05b7-4a8f-a85f-1188f7bc1583)

### Create a virtual network by using Azure Cloud Shell
![image](https://github.com/user-attachments/assets/9cab8680-5a77-45b2-bc09-61ae7a39f86b) 
Create a virtual network by using the az network vnet create Azure CLI command ![image](https://github.com/user-attachments/assets/568441e6-acde-4a78-83c3-db3e64cde85c)
az network vnet show command ![image](https://github.com/user-attachments/assets/a33bf993-44c8-4f93-b754-e92fc560850d) 
Configure peering connections between the virtual networks | Create virtual network peering connections from webVNET to appVNET
![image](https://github.com/user-attachments/assets/21584d89-6e71-4acf-ae77-06cefd0911e3) ![image](https://github.com/user-attachments/assets/0d86235f-bfc2-4266-abe0-573531f58bdd)
![image](https://github.com/user-attachments/assets/8e22d572-4c20-4600-aebf-9032379c4312) ![image](https://github.com/user-attachments/assets/d98a709e-b976-4d6e-8eef-2c14df36007d)
•	Verify that the webVNET-to-appVNET peering connection status is Connected ![image](https://github.com/user-attachments/assets/16022fd7-d8dd-4692-bbf0-545f72e83352)

### Configure an Application Security Group
![image](https://github.com/user-attachments/assets/0bb06a04-d227-40d2-bd19-a12574674972) ![image](https://github.com/user-attachments/assets/63eca946-46d7-494b-9562-3feab1531044)
![image](https://github.com/user-attachments/assets/d7ab3466-fd18-41e9-8e41-dc845c168476) 
Creating a Network security group ![image](https://github.com/user-attachments/assets/caa4849e-9098-45f3-a979-87ceb49bc9dd)
Add an inbound security rule to webNSG to allow HTTP and HTTPS traffic
![image](https://github.com/user-attachments/assets/5a117f43-081b-4afa-bc77-ea545965b925) ![image](https://github.com/user-attachments/assets/b00dbf93-d991-4482-846a-18b0f2492741)
•	Associate the network security group to the web subnet in webVNET ![image](https://github.com/user-attachments/assets/2aec8480-bebf-407a-9a64-196166ddb89a) 
![image](https://github.com/user-attachments/assets/9637959a-fd47-4681-b472-e729edb9a795) 

### Create an Azure virtual machine 
![image](https://github.com/user-attachments/assets/3b2e3fe0-8d44-439a-8bb3-0ff52e319bde) 
![image](https://github.com/user-attachments/assets/f5e75b8c-1e60-4a83-848a-6fba6bfc120b)
![image](https://github.com/user-attachments/assets/29c8eee1-335d-4ce5-9ddb-7d2bc8cd9910)
Validation passed now we can deploy the virtual machine ![image](https://github.com/user-attachments/assets/24136129-e9d1-4827-ad47-cf4cc1eee6ad)
![image](https://github.com/user-attachments/assets/44faeb12-fa34-4843-b76f-4c59930e9069) Deployed
•	Associate the webASG application security group with the VM1 virtual machine NIC.
![image](https://github.com/user-attachments/assets/5d18f50b-34d6-4b09-ad14-cdceb5c048a7) ![image](https://github.com/user-attachments/assets/20344986-2fa8-4d36-8092-e5dce46f44ad)
Connect to VM1 through RDP ![image](https://github.com/user-attachments/assets/fc5499d6-2d9f-4d0f-99ec-d3cb1f5863b4) ![image](https://github.com/user-attachments/assets/0167329b-8d1a-4ffb-b17a-b81c67028919)
![image](https://github.com/user-attachments/assets/eb1b5239-c575-4729-ba1f-5dbf8e552b16)
On VM1, run the following command in Windows PowerShell® to install Internet Information Services (IIS):
![image](https://github.com/user-attachments/assets/6923490b-c8a3-45d7-af0b-95010b6cdb33) ![image](https://github.com/user-attachments/assets/0c4d17a5-0ed5-43db-83d2-ebd1897e671c)

























 










---

## 🔧 Tools & Services Used

- Microsoft Azure App Services
- Azure Active Directory (App Registrations)
- GitHub (for deployment)
- VS Code (code editing and publishing)

---

## ✅ Key Learnings

- How to enforce user authentication in an Azure-ho
