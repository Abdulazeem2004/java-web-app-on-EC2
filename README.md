# java-web-app-on-EC2
<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Set Up a Web App in the Cloud

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-devops-vscode)

**Author:** Abdulazeem Badmus  
**Email:** badmusazeem05@gmail.com

---

## Set Up a Web App Using AWS and VS Code

![Image](http://learn.nextwork.org/grateful_gray_shy_mouse/uploads/aws-devops-vscode_7a1de541)

---

## Introducing Today's Project!

In this project, I will demonstrate how to build a web app in the cloud. I’m doing this project to learn how to design, deploy, and automate cloud-based applications using modern DevOps practices.

This project is part one of a series of DevOps projects where I'm building a CI/CD pipeline! I'll be working on the next project in next 24hrs.

I did this project because I wanted to better understand how cloud services like EC2, SSH, and web servers work together in a real-world setup.

### Key tools and concepts

Services I used were Amazon EC2 for hosting the virtual server, SSH for secure remote access, and VS Code Remote-SSH for managing and editing files on the server.
Key concepts I learnt include cloud virtual machines, secure authentication using key pairs, remote server access, basic Linux command-line operations, and how web applications are deployed and modified directly on a cloud server.

### Project reflection

This project took me approximately1hr. The most challenging part was modifying my key pair permission and also seeting a remote connection from vs code to the remote server to make use of the IDE. It was most rewarding to make sure the SSH config file is correct by making sure the path to my private key location is properly stated.

One thing I didn’t expect in this project was that configuring secure access to the server (key pairs, ports, users) would be more challenging than editing the web application itself.

---

## Launching an EC2 instance

### What I did in this step

In this step, I will be launching an EC2 instance. because this is the virtual server i will be using to create and host the web app.

I started this project by launching an EC2 instance because it provides a scalable and controllable compute environment to host the web application and allows me to configure the server, networking, and security settings just like in a real production setup.

![Image](http://learn.nextwork.org/grateful_gray_shy_mouse/uploads/aws-devops-vscode_7852fbf3)

### I also enabled SSH

SSH (Secure Shell) is a secure network protocol used to remotely access and manage a server over an encrypted connection. I enabled SSH so that I can securely connect to the EC2 instance and perform configuration, deployment, and troubleshooting tasks from my local machine.

### Key pairs

A key pair is a set of cryptographic keys (a public key and a private key) used to securely authenticate access to cloud resources such as an EC2 instance, allowing users to connect without passwords.

### Downloaded key pair file

Once I set up my key pair, AWS automatically downloaded the private key to my device. The file is a .pem file which stands for "Privacy Enhanced mail" .

---

## Set up VS Code

### What I did in this step

In this step, I will set up my terminal interface in vs code to commmunicate with the EC2 virtual server and also modifying the permission for the .pem file(the private key) to log into the server so i can communicate with it . because SSH requires strict permissions on private keys to prevent unauthorized access..

### What is VS Code?

VS Code is IDE(Integrated Development Environment) which is basically a text editor for writing code, managing application files and folders. it also has a terminal interface for executing commands, and networking

I installed VS Code to write the code for the web app, manage the app files and dependencies and also utilize the terminal interface to SSH into the EC2 server.

![Image](http://learn.nextwork.org/grateful_gray_shy_mouse/uploads/aws-devops-vscode_53d05e68)

---

## My first terminal commands

A terminal is a command line interface use to run command to instruct the computer to do something. The first command I ran for this project is "cd C:\Users\user\Desktop\DevOps" which i used to change the directory to where the private key is stored when modifying the permission of the file the terminal can easily locate the location of the file
.

### Updating file permissions

I also updated my private key's permissions by executing this comand "icacls "nextwork-keypair.pem" /reset
icacls "nextwork-keypair.pem" /grant:r "user:R"
icacls "nextwork-keypair.pem" /inheritance:r"
 this command resets the default permission of the file and lets me access the file.

![Image](http://learn.nextwork.org/grateful_gray_shy_mouse/uploads/aws-devops-vscode_9328ada1)

---

## SSH connection to EC2 instance

### What I did in this step

In this step, I will connect to the EC2 instance. because this will allow to me to get access to the virtual server to make configurations,  administration and troubleshooting.

### Connecting to EC2

To connect to my EC2 instance, I ran the command " ssh -i C:\Users\user\Desktop\DevOps\nextwork-keypair.pem ec2-user@ec2-18-246-43-131.us-west-2.compute.amazonaws.com".

### This command required an IPv4 address

A server's IPV4 DNS is s the public address for the EC2 server that the internet uses to find and connect to it. My local computer  will find and connect to the EC2 instance through this IPv4 DNS..

![Image](http://learn.nextwork.org/grateful_gray_shy_mouse/uploads/aws-devops-vscode_e3069dca)

---

## Maven & Java

### What I did in this step

In this step, I will install this two tools "Apache Maven" and " Amazon Corretto". because this tool will be use to build jave web app on the EC2 instance.

### Why I'm using Maven

Apache Maven is a tool that helps developers build and organize Java software projects. It's also a package manager, which means it automatically download any external pieces of code your project depends on to work.

Maven is required in this project because  it's really useful for kick-starting web projects! It uses something called archetypes, which are like templates, to lay out the foundations for different types of projects e.g. web apps

### Why I'm using Java

Java is a popular programming language used to build different types of applications, from mobile apps to large enterprise systems.

Java is required in this project because Maven, which we just downloaded, is a tool that NEEDS Java to operate. So if we don't install Java, we won't be able to use Maven to generate/build our web app .

---

## Create the Application

### What I did in this step

In this step, I will be creating the web app, because it forms the core of the project and provides a functional application that can be deployed, tested, and automated within the cloud environment.

### Creating the Java web app

I generated a Java web app using the command "mvn archetype:generate \
   -DgroupId=com.nextwork.app \
   -DartifactId=nextwork-web-project \
   -DarchetypeArtifactId=maven-archetype-webapp \
   -DinteractiveMode=false
".

### Installing Remote - SSH

I installed Remote - SSH, which is a Visual Studio Code extension that allows me to connect to and work on a remote server over SSH directly from my local editor. I installed it to easily access the EC2 instance, edit files, run commands, and manage the application without having to rely solely on the command line.

### SSH configuration details

Configuration details required to set up a remote connection include the remote server’s public IP address or DNS name, the SSH username, the path to the private key (.pem file), and the correct SSH port (typically port 22).

![Image](http://learn.nextwork.org/grateful_gray_shy_mouse/uploads/aws-devops-vscode_2939cf01)

---

## Create the Application

### Exploring the project structure

Using VS Code’s file explorer, I could see the project files directly on the EC2 instance, allowing me to edit, create, and manage files remotely as if they were on my local machine

“Two of the project folders created by Maven are src and webapp, which separate the Java source code, configuration files, and tests from the web components such as HTML, JSP files, CSS, and JavaScript, helping maintain a clean and structured project layout.

![Image](http://learn.nextwork.org/grateful_gray_shy_mouse/uploads/aws-devops-vscode_45f91fd7)

---

## Using Remote - SSH

### What I did in this step

In this step, I will be connecting my VS CODE to the EC2 instance. because this will allow me edit and manage the files in my EC2 instance locally from VS CODE making use of the full feature of the IDE to manage the project.

### Updating the web app

The index.jsp is the default entry point of the web application. It is a Java Server Pages (JSP) file responsible for handling the initial request from the user’s browser and generating dynamic web content. When the application is accessed, the server processes the index.jsp file, executes any embedded Java code, and returns the resulting HTML to the client for display.

I edited index.jsp by configuring it to how i want my web page to look like

![Image](http://learn.nextwork.org/grateful_gray_shy_mouse/uploads/aws-devops-vscode_7a1de541)

---

## Using nano

### Additional improvements

In this secret mission, I will be editing the web app in the terminal instead of the IDE because it helps me understand how applications are managed directly on a server environment, improves my command-line skills, and reflects real-world DevOps workflows where changes are often made on remote machines without a graphical interface.

### Terminal vs IDE

An alternative to using IDEs is the nano tool. To edit index.jsp, I ran the command "nano index.jsp.

Compared to using an IDE, editing index.jsp in the terminal felt old school because there is no syntax highlighting, auto-completion, or real-time error detection, making the process slower and more manual. I’d be more likely to use an IDE if I were doing frequent edits, complex logic changes, or needed faster feedback and debugging support.

### Verifying my work

To verify my editing work in the terminal, I refreshed the web application in the IDE to confirm that the changes were reflected correctly. It was possible to see my changes in VS Code right away because both the terminal and VS Code were connected to the same remote server, so any file saved on the server was instantly synchronized and visible.

![Image](http://learn.nextwork.org/grateful_gray_shy_mouse/uploads/aws-devops-vscode_a3324ad41)

---

---
