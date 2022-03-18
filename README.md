# Oluwatosin-Agbetunsin
This repository that will serve as place where I store my scripts, diagrams or other documentation that you I have worked on throughout this course. Additionally I will be uploading the README file, network diagram, and other associated files that i have created during the ELK Stack project.
These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the repository file may be used to install only certain pieces of it, such as Filebeat.
image

Description of the Topology
Access Policies
ELK Configuration
Beats in Use
Machines Being Monitored
How to Use the Ansible Build
Description of the Topology
The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network. Load balancer protect the application layer of the OSI model. one advantage of Jumpbox is that it forces all traffic through a single node

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the configuration and system application.

_Filebeat is a lightweight stripper and is used for forwarding and centralizing log data,it is installed as an agent on your server. it collects, monitors log data and forwards such data to Elastic search or Logstash.
Metricbeat records for system-level CPU usage,memory,file system,disk IO and network IO statistics.
The configuration details of each machine may be found below. Note: Use the Markdown Table Generator to add/remove values from the table.

Name | Function | IP Address | Operating System
Jump Box | Gateway | 10.1.0.4 | Linux
Web-1 | Webserver | 10.1.0.7 | Linux
Web-2 | Webserver | 10.1.0.8 | Linux
ELK-Server | Monitoring | 10.0.0.4 | Linux

Access Policies
The machines on the internal network are not exposed to the public Internet.

Only the Jump-box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses: 20.127.132.122

Machines within the network can only be accessed by Jumpbox,Elk server and the Load balancer -The machines that have access to the ELK server are the web-1 and web-2 server and the ip address of the ELK server is 10.0.0.4
A summary of the access policies in place can be found in the table below.

Name | Publicly Accessible | Allowed IP Addresses
Jump Box | Yes | 20.127.132.122
Web-1 | No | 10.1.0.7
Web-2 | No | 10.1.0.8
ELK-server | No | 104.40.87.149 for public, while private is 10.0.0.4

Elk Configuration
Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous

-Because it eliminates the chance of human error and can simplify the process of configuring potentially thousands of machines identically all at once. The playbook implements the following tasks:
-TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc. Installed Docker and Ansible on the Jumpbox machine, enabling playbook automation to push software services to other machines Added ELK VM to Hosts file under a separate Group header (elk) Run Playbook file via ansible-playbook command, therefore pushing tasks to all machines assigned/configured to receive

Target Machines & Beats
This ELK server is configured to monitor the following machines:

It is configured to monitor the DVWA -VM-1 10.1.0.7 and DVWA-VM-2 10.1.0.8
We have installed the following Beats on these machines: Filebeat and Metricbeat was succesfully installed on the machines

These Beats allow us to collect the following information from each machine: Filebeat is a light weight shipper for forwarding and centralizing log data,it is installed as an agent on the server. it collects, monitors and forwards logs like (system logs,server logs and audit logs ) to elastic search and logstash._ Metricbeat helps with providing info on CPU usage,memory output and usage, it is a lightweight shipper that can be installed on servers to periodically collect metrics from the operating system and from services running on the server. E.g. Apache, MySQL, Redis, CPU, RAM, MEMORY.

Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned:

SSH into the control node and follow the steps below:

*Copy the install-elk.yml file to /etc/ansible.
*Update the /etc/ansible/hosts to include webservers 10.1.0.7 , 10.1.0.8 and ELK server 10.0.0.4
*Run the playbook, and navigate to http://[ELK-VM.IP]:5601 to check that the installation worked as expected.

Answer the following questions to fill in the blanks:

-Which file is the playbook? Where do you copy it?/etc/ansible/install-elk.yml
-Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?/etc/ansible/hosts
-Which URL do you navigate to in order to check that the ELK server is running?http://[your.ELK-VM.External.IP]:5601/app/kibana
