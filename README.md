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

**If you sign-in again the following screen will be displayed**





