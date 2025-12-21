                                                          JENKINS PRODUCTION ASSIGNMENT

<img width="940" height="497" alt="image" src="https://github.com/user-attachments/assets/c23869e1-a8c1-4e75-bfb7-cbc6f04cf88c" />


To meet the requirements of "Assignment 1" using Azure(I’m using Azure Cloud), we will set up a Jenkins Master and two separate Jenkins Slave Nodes (Agents).
Since the assignment emphasizes a "Production-Grade" and "Resilient" setup, we will use SSH to connect the Master to the Agents.
Phase 1: Azure Infrastructure Setup
You need to create three Virtual Machines (VMs) in the Azure Portal. Use Ubuntu 22.04 LTS for all of them for consistency.
1.	Jenkins-Controller (Master):
o	Size: Standard_B2s (2 vCPUs, 4GB RAM).
o	Networking: Open ports 8080 (Jenkins UI) and 22 (SSH).
2.	Jenkins-Agent-01:
o	Size: Standard_B2s (2 vCPUs, 1GB RAM).
o	Networking: Open port 22.
3.	Jenkins-Agent-02 (The "Trick" Node):
o	Size: Standard_B1s (This matches the requirement: 2 vCPU, 1GB RAM).
o	Networking: Open port 22.

Phase 2: Install Jenkins on the Controller
SSH into your Jenkins-Controller VM and run the following to install Java and Jenkins:
Bash
sudo apt update
sudo apt install fontconfig openjdk-17-jre -y
sudo wget -O /usr/share/keyrings/jenkins-keyring.asc \
  https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key
echo "deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
  https://pkg.jenkins.io/debian-stable binary/" | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt update
sudo apt install jenkins -y
sudo systemctl start Jenkins
########################################
azureuser@Jenkins-Master:~$ uname -n
Jenkins-Master
azureuser@Jenkins-Master:~$ java --version
openjdk 17.0.17 2025-10-21
OpenJDK Runtime Environment (build 17.0.17+10-Ubuntu-122.04)
OpenJDK 64-Bit Server VM (build 17.0.17+10-Ubuntu-122.04, mixed mode, sharing)
azureuser@Jenkins-Master:~$
azureuser@Jenkins-Master:~$
azureuser@Jenkins-Master:~$ systemctl status jenkins
● jenkins.service - Jenkins Continuous Integration Server
     Loaded: loaded (/lib/systemd/system/jenkins.service; enabled; vendor preset: enabled)
     Active: active (running) since Sun 2025-12-21 03:50:58 UTC; 18min ago
   Main PID: 5390 (java)
      Tasks: 49 (limit: 4691)
     Memory: 1013.8M
        CPU: 44.269s
     CGroup: /system.slice/jenkins.service
             └─5390 /usr/bin/java -Djava.awt.headless=true -jar /usr/share/java/jenkins.war --webroot=/var/cache/jenkins/war --httpPort=8080

Dec 21 03:57:38 Jenkins-Master jenkins[5390]: 2025-12-21 03:57:38.516+0000 [id=259]        INFO        jenkins.InitReactorRunner$1#onAttained: Listed all plugins

<img width="940" height="476" alt="image" src="https://github.com/user-attachments/assets/2b5e58ce-9aeb-4f81-8052-8e08fba90b7f" />

#########################################

•	Access Jenkins: Go to http://<Your-VM-IP>:8080.
•	Unlock: Use sudo cat /var/lib/jenkins/secrets/initialAdminPassword to get the key.


 

Phase 3: Prepare the Agents
On BOTH Agent VMs, you only need to install Java (Jenkins needs it to run the agent .jar file):
Bash
sudo apt update
sudo apt install openjdk-17-jre -y

#########################################
azureuser@Jenkins-Slave-01:~$ uname -n
Jenkins-Slave-01
azureuser@Jenkins-Slave-01:~$ java --version
openjdk 17.0.17 2025-10-21
OpenJDK Runtime Environment (build 17.0.17+10-Ubuntu-122.04)
OpenJDK 64-Bit Server VM (build 17.0.17+10-Ubuntu-122.04, mixed mode, sharing)

################################################

azureuser@Jenkins-Slave-02:~$ uname -n
Jenkins-Slave-02
azureuser@Jenkins-Slave-02:~$ java --version
openjdk 17.0.17 2025-10-21
OpenJDK Runtime Environment (build 17.0.17+10-Ubuntu-122.04)
OpenJDK 64-Bit Server VM (build 17.0.17+10-Ubuntu-122.04, mixed mode, sharing)

1. Create and Enable a Swap File
Connect to each agent VM via SSH and run the following commands to create a 2GB swap file:
•	Create the file: sudo fallocate -l 2G /swapfile
•	Secure the file: sudo chmod 600 /swapfile
•	Format as swap: sudo mkswap /swapfile
•	Enable the swap: sudo swapon /swapfile
2. Make Swap Permanent
To ensure the swap space remains available after a reboot, add it to your system configuration:
•	Add to fstab: echo '/swapfile none swap sw 0 0' | sudo tee -a /etc/fstab

<img width="940" height="352" alt="image" src="https://github.com/user-attachments/assets/39ed419f-70c3-4c8a-a83f-e1fa055e4e05" />

##########################################################################################

Task 02

Enable RBAC with Matrix Authorization strategy

<img width="638" height="256" alt="image" src="https://github.com/user-attachments/assets/e8208834-0729-43a3-aaa3-2514ed131bba" />

Created 3- Roles : admin(full Access), Developer(can trigger builds but not modify jobs), Auditor(read only access)

<img width="851" height="350" alt="image" src="https://github.com/user-attachments/assets/3fdf3009-577e-4e34-91a9-2819ee4ac862" />



<img width="909" height="425" alt="image" src="https://github.com/user-attachments/assets/98c69544-d8f6-4dc7-9ba6-e172591aa845" />






