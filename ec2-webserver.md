Certainly! Here's the complete content in Git readme.md file format:

markdown
Copy code
# Installing Apache HTTP Server on Amazon Linux 2

This guide provides step-by-step instructions to install and configure the Apache HTTP Server (httpd) on Amazon Linux 2 using the `yum` package manager.

## Update the System, Install Apache HTTP Server, Start the httpd service, Enable httpd to start on boot, Verify that httpd is running.
```
sudo yum update -y
sudo yum install -y httpd
sudo systemctl start httpd
sudo systemctl enable httpd
sudo systemctl status httpd
```