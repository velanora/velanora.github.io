+++
date = '2026-03-06T18:51:13+05:00'
draft = false
title = 'Setting Up a Virtual Machine on Cloud platform (Microsoft Azure) with SSH'
description = "This blog explains the basics of **virtual machines, cloud platforms, and SSH keys**, and shows how to create and connect to a virtual machine on **Microsoft Azure**. It also demonstrates how to perform basic tasks inside the VM, such as updating the system, installing tools, and running a simple Python program."

showToc = true
tags =  [ "Cloud platform" ,"SSH key", "Virtual machine", "Microsoft Azure account", "Ubuntu 24.04", "Cloud Computing", "Python", "Beginner guide", "linux"]
categories= [ "DevOps basics" ,"Virtual machine","Cloud Computing" , "tech guides"]


+++ 
---
# 1. Introduction :
## Key Terminologies :

- ### Virtual Machine
virtual machine is a computer inside a computer. It behaves like a real computer despite being virtual. But in this guide we will use our VM on a cloud platform instead of running everything locally on computer.

- ### Cloud platform 
Cloud computing means using computing services over the internet instead of using them locally on your own computer. Microsoft Azure, Google cloud infrastructure and AWS are some of the examples of cloud platforms.

- ### SSH key
SSH (secure shell) is a secure network protocol. It is used to connect and control remote computer through the command line.

## In this guide:

It is a beginner friendly guide, Microsoft Azure is a cloud computing platform over which we will create our virtual machine. And then, we will access it through SSH.

--- 
# 2. Steps to create a Virtual machine connect it via SSH key :

## 1- Create Microsft Azure Account
To setup a Virtual machine on any cloud platform, you need to have an account on that platform. So, first create an Microsoft azure account.

## 2- Setting up your first Azure Resource
1. Click the menu icon on the top left corner and select **Virtual machine**.

2. Click on **Create a resource**.
![Create a Resource](/images/first-VM-azure/first-VM-azure1.png)

### - Project Details

1. Select your subscription, mine is **Azure for students**.
2. Select or create a new resource group.


### - Instance details

1. Name your Virtual machine, For instance **FirstVM**.
2. Select the nearest region from your location.
3. Choose **No infrastructure redundancy required** in availabilty options.
4. Go with **standard** security type.
5. Pick the ISO image you want.
6. Click the **x64** version of VM architecture.
7. Select the appropriate size.
![Project and instance details](/images/first-VM-azure/first-VM-azure2.png)


### - administrator account

1. Opt for **SSH public key** as a authentication type.
2. Enter your username.
3. For SSH key type, go with **RSA SSH Format**.
4. Name your key pair.
![Administrator account](/images/first-VM-azure/first-VM-azure3.png)


### - Inbound port rules.
1. Allow selected ports.
2. Select **SSH (22), HTTP (80)** ports
3. Click **Review + create**.
![Inbound port rules](/images/first-VM-azure/first-VM-azure4.png)


## 3- Launching the virtual machine on Azure
1. Now review the VM specifications and then click create.
2. Download the private key and create the resource.
3. Wait for the virtual machine to be deployed.
4. Once the deployment is completed, click **Go the Resource**.
![Create a Resource](/images/first-VM-azure/first-VM-azure5.png)



## 4- Connecting to the VM using SSH key
1. Open the terminal and navigate to the directory where you SSH key pair was downloaded.
```
cd Downloads/

```
2. Make the private key readable by only you (owner) and no one else.
```
chmod 400 pair_key_name.pem
```
3. Connect to the VM via SSH key:
```
ssh -i pair_key_name.pem username@your_ip
```
- Replace the pair_key_name.pem with the name you choosed for your pair key.
- Enter your username.
- Under the **connect** tab, your Vm's IP address is available. Copy it and paste it at the place of your_ip in the above given command.

4. When asked, type **Yes** and press **Enter**.
--- 
# 3. Working inside the Virtual machine:

## 1- Verify the system
```
uname -a
```
It displays the following information about system.
- Operating system
- kernel version
- System architecture (e.g x64)
- Hostname of the machine

```
lsb_release -a
```
This command the given information about the linux distribution installed on virtual machine.
- linux distrbution (e.g ubuntu,kali).
- Release version
- description of the OS


## 2- Update your VM 
Then, update and upgrade your Ubuntu OS.
```
sudo apt update
```

```
sudo apt upgrade -y
```


## 3- Install tools
You can install any tools according to your needs.
For instance,we will install tools for python language.
```
sudo apt install python3 python3-pip git -y
```
- **Python3**  -----> Python 3 interpreter.
- **Python3-pip**  -----> Python package manager,
- **git**  -----> a version control system.
- **-y**  -----> automatically answers "yes".

## 4- Create and run a simple python program
1. Create a file named as hello.py 
```
nano hello.py
```
2. Stuff this file with the content.
![Create a Resource](/images/first-VM-azure/first-VM-azure6.png)

3. Save (Ctrl + O)---> Enter ----> Exit (Ctrl + X) the file.
4. Run the program.
```
python3 hello.py
```
5. The output will be displayed in the terminal.


--- 
# 4. log Out the VM :
After working in the virtual machine, logout from it by using the given command.

```
logout
```
![Terminal](/images/first-VM-azure/first-VM-azure7.jpeg)

--- 
# 5. Conclusion :
In this guide, we successfully created and connected to a virtual machine on **Microsoft Azure using an SSH key**. We verified the system, updated the VM, installed essential tools, and ran a Python program. This process demonstrates how cloud platforms make it easy to create and manage computing environments remotely.



