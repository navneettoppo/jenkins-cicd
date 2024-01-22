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

On the left-hand side, select Manage Jenkins, and then select Manage Plugins.

Select the Available tab, and then enter Amazon EC2 plugin at the top right.

Select the checkbox next to Amazon EC2 plugin, and then select Install without restart.

Jenkins Plugin Manager showing available plugins.
Once the installation is done, select Back to Dashboard.

Select Configure a cloud if there are no existing nodes or clouds.

Jenkins Dashboard showing configure a cloud.
If you already have other nodes or clouds set up, select Manage Jenkins.

Jenkins dashboard if there are existing clouds.
After navigating to Manage Jenkins, select Configure Nodes and Clouds from the left hand side of the page.

Manage nodes and clouds option from Manage Jenkins page
From here, select Clouds.

Configure clouds option in navigation.
Select Add a new cloud, and select Amazon EC2. A collection of new fields appears.

Adding Amazon EC2 cloud to Jenkins.
Click Add under Amazon EC2 Credentials

Adding EC2 credentials in Configure Cloud.
From the Jenkins Credentials Provider, select AWS Credentials as the Kind.

Choosing Kind AWS Credentials.
Scroll down and enter in the IAM User programmatic access keys with permissions to launch EC2 instances and select Add.

Adding AWS Credentials.
Scroll down to select your region using the drop-down, and select Add for the EC2 Key Pair’s Private Key.

Set Region and add Private Key.
From the Jenkins Credentials Provider, select SSH Username with private key as the Kind and set the Username to ec2-user.

Set Kind to SSH Username with private key.
Scroll down and select Enter Directly under Private Key, then select Add.

Set Private Key to Enter Directly.
Open the private key pair you created in the creating a key pair step and paste in the contents from "-----BEGIN RSA PRIVATE KEY-----" to "-----END RSA PRIVATE KEY-----". Select Add when completed.

Enter Private Key.
Scroll down to "Test Connection" and ensure it states "Success". Select Save when done

Test Connection.
You are now ready to use EC2 instances as Jenkins agents.