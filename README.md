Automated ELK Stack Deployment
------------------------------

The files in this repository were used to configure the network depicted below.

**Note**: The following image link needs to be updated. Replace `Diagram.png` with the name of your diagram image file.

https://drive.google.com/file/d/19a84gdNCeeRhTcAYZMsFdUyGDxCh-f3q/view?usp=sharing (Link to Diagram, could not get image in Readme File for some reason)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the PLAYBOOK file may be used to install only certain pieces of it, such as Filebeat.

-   elk-playbook.yml

This document contains the following details: 
- Description of the Topologu
- Access Policies 
- ELK Configuration 
  - Beats in Use 
  - Machines Being Monitored  
- How to Use the Ansible Build

### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D\*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly AVAILABLE, in addition to restricting ACCESS to the network. 

------
Load Balancers are able protect the system from DDOS style attacks by shifting the attacking traffic across servers. The main advantage of a jump box is to give access to the user from a single node or point which can easily be secured and checked. 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the NETWORK and system LOGS. 

------
Filebeat checks for information in the file system that has been changed and notes when it has been changed. Metricbeat take the statistcs/metrics and sends them to an output that has been chosen. 

The configuration details of each machine may be found below. *Note: Use the* [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) *to add/remove values from the table*.

| Name        | Function | IP Address | Operating System |
|-------------|----------|------------|------------------|
| Jump Box    | Gateway  | 10.0.0.1   | Linux            |
| Web 1 DVWA  | Server   | 10.1.0.10  | Linux            |
| Web 2 DVWA  | Server   | 10.1.0.9   | Linux            |
| ELK Stack   | Server   | 10.2.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet.

Only the JUMPBOX machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses: 76.181.198.35

Machines within the network can only be accessed by JUMPBOX. - 20.98.70.85

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses      |
|----------|---------------------|---------------------------|
| Jump Box | Yes                 | IP - Home                 |
| Web 1    | No                  | 52.250.52.51 (RedTeam-LB) |
| Web 2    | No                  | 52.250.52.51 (RedTeam-LB) |
| ELK      | Yes                 | IP - Home                 |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...

------

The main advantage of automating configuration with Ansible is that it guarantees that human errors do not occur during configuration

The playbook implements the following tasks: 
docker.io
Install pip3
Increase Virtual Memory
Launch a docker elk container
Install Docker Python Module

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

**Note**: The following image link needs to be updated. Replace `docker_ps_output.png` with the name of your screenshot image file.

https://drive.google.com/file/d/1BNxqbHeUCNMes_tjEL5eBjCMagamOO6X/view?usp=sharing (Link to screenshot could not get image in Readme File for some reason)

### Target Machines & Beats

This ELK server is configured to monitor the following machines: - 

------
Web-1 10.1.0.10
Web-2 10.1.0.9

We have installed the following Beats on these machines: - 

------
Metricbeat
Filebeat

These Beats allow us to collect the following information from each machine:

------
Filebeat: Collects data such as SSH Logins, New Users/Groups, and admin Commands. Performs Log Management

 Metricbeat: Tracks Memory, CPU Usage, # of Containers. Connected to DVWA

### Using the Playbook

In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned:

SSH into the control node and follow the steps below: 
- Copy the YML file to CONTROL NODE.
- Update the HOST file to include IP ADDRESSES ON NETWORK 
- - Run the playbook, and navigate to http://[ELK AP Address]:5601/app/kibana to check that the installation worked as expected.

------
Which file is the Playbook? Where do you copy it? elk-playbook, copy is /etc/ansible
Which file do you update to make Ansible run the playbook on a specific machine? elk-playbook
How do I specify which machine to install the ELK Server on versus which to install Filebeat on? IP Address
Which URL do you navigate to in order to check that the ELK Server is running? http://[ELK AP Address]:5601/app/kibana

*As a Bonus, provide the specific commands the user will need to run to download the playbook, update the files, etc.*
