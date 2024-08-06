# Installation on EC2 Instance

Install Jenkins, configure Docker as agent, set up cicd and much more.

## AWS EC2 Instance
- Go to AWS Console
- Instances(running)
- Launch EC2 instances

![image](https://github.com/user-attachments/assets/41bd626d-ec7c-4f73-bd7b-3c90dc70499f)

**Security Group(Ports need to be opened)**

<img width="1440" alt="Screenshot 2024-08-07 at 1 23 05 AM" src="https://github.com/user-attachments/assets/2cf532c9-b623-4884-9d15-2f6764906fbb">


## Jenkins

**Pre-Requisites:**

Java (JDK)

Run the below commands to install Java and Jenkins

Install Java


````
sudo apt update
sudo apt install openjdk-11-jre
````

Now check whether Java has been successfully installed in your local

```
java --version
```

Install Jenkins(based on your system requirement)

```
curl -fsSL https://pkg.jenkins.io/debian/jenkins.io-2023.key | sudo tee \
  /usr/share/keyrings/jenkins-keyring.asc > /dev/null
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
  https://pkg.jenkins.io/debian binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt-get update
sudo apt-get install jenkins
```

To install for your specific system: https://www.jenkins.io/doc/book/installing/

Once Jenkins has been sucessfully installed in your local, let's run it

```
sudo systemctl start jenkins
sudo systemctl status jenkins
```
**Login to Jenkins using the below URL:**
http:[Public IP address]//:8080 [You can get the ec2-instance-public-ip-address from your AWS EC2 console page]

Note: If you are not interested in allowing All Traffic to your EC2 instance 

1. Delete the inbound traffic rule for your instance
2. Edit the inbound traffic rule to only allow custom TCP port 8080

After you login to Jenkins, 
- Run the command to copy the Jenkins Admin Password
- sudo cat /var/lib/jenkins/secrets/initialAdminPassword
- Enter the Administrator password

![image](https://github.com/user-attachments/assets/ac6d575e-c8bb-4914-9dfa-a05da4f1c688)

**Click on Install suggested plugins**

![image](https://github.com/user-attachments/assets/2a4d0d33-9a96-409c-a87b-2353b6c2e7f1)

**Wait for the Jenkins to Install suggested plugins**

![image](https://github.com/user-attachments/assets/71f84696-ce20-4b1b-918b-efe34a1134e1)

**Create First Admin User or Skip the step [If you want to use this Jenkins instance for future use-cases as well, better to create admin user]**

![image](https://github.com/user-attachments/assets/413a38d5-3408-4cf2-a2be-f615aa44ad5a)

**Jenkins Installation is Successful. You can now starting using the Jenkins**

![image](https://github.com/user-attachments/assets/da874fb0-7fff-4ca5-89db-3e7fc3212a8f)

**Login to Jenkins by provided previously created credentials**

<img width="1440" alt="Screenshot 2024-08-07 at 1 04 17 AM" src="https://github.com/user-attachments/assets/3f47714c-e5dc-4dcc-a380-bc8671385593">

**The dashboard will look like this after successfully creating pipeline**

<img width="1440" alt="Screenshot 2024-08-07 at 1 06 22 AM" src="https://github.com/user-attachments/assets/ebcb701a-8ff6-4f49-88b5-24f1b79fcffd">


## Install the Docker Pipeline plugin in Jenkins:

- Log in to Jenkins.
- Go to Manage Jenkins > Manage Plugins.
- In the Available tab, search for "Docker Pipeline".
- Select the plugin and click the Install button.
- Restart Jenkins after the plugin is installed.

<img width="1440" alt="Screenshot 2024-08-07 at 1 16 26 AM" src="https://github.com/user-attachments/assets/204a467f-aae5-404e-80e6-eef7df97db80">


Wait for the Jenkins to be restarted.



## Docker Slave Configuration

Run the below command to Install Docker

```
sudo apt update
sudo apt install docker.io
```

Grant Jenkins user and Ubuntu user permission to docker deamon.
```
sudo su - 
usermod -aG docker jenkins
usermod -aG docker ubuntu
systemctl restart docker
```
Once you are done with the above steps, it is better to restart Jenkins.
```
http://<ec2-instance-public-ip>:8080/restart
```
The docker agent configuration is now successful.
