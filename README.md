# jenkins-cicd
jenkins installtion and CICD steps

Downloading and installing Jenkins
Completing the previous steps enables you to download and install Jenkins on AWS. To download and install Jenkins:

Ensure that your software packages are up to date on your instance by using the following command to perform a quick software update:
```
sudo yum update –y
```
Add the Jenkins repo using the following command:
```
sudo wget -O /etc/yum.repos.d/jenkins.repo \
    https://pkg.jenkins.io/redhat-stable/jenkins.repo
```

Import a key file from Jenkins-CI to enable installation from the package:
```
sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key
sudo yum upgrade
```

Install Java (Amazon Linux 2023):
```
sudo dnf install java-17-amazon-corretto -y
```
Install Jenkins:
```
sudo yum install jenkins -y
```
Enable the Jenkins service to start at boot:
```
sudo systemctl enable jenkins
```
Start Jenkins as a service:
```
sudo systemctl start jenkins
```
You can check the status of the Jenkins service using the command:
```
sudo systemctl status jenkins
```



Configuring Jenkins
Jenkins is now installed and running on your EC2 instance. To configure Jenkins:
```
Connect to http://<your_server_public_DNS>:8080 from your browser. You will be able to access Jenkins through its management interface:
```

As prompted, enter the password found in /var/lib/jenkins/secrets/initialAdminPassword.
Use the following command to display this password:
```
cat /var/lib/jenkins/secrets/initialAdminPassword
```
The Jenkins installation script directs you to the Customize Jenkins page. Click Install suggested plugins.

Once the installation is complete, the Create First Admin User will open. Enter your information, and then select Save and Continue.

Create your first admin user.