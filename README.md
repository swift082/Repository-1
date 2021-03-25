# Repository-1
Cybersecurity Bootcamp Week 1-13 Repository
Automated ELK Stack Deployment
The files in this repository were used to configure the network depicted below.

Diagrams/Homework 13 Diagram

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

Playbook: ELK.yml

This document contains the following details:

Description of the Topologu
Access Policies
ELK Configuration
Beats in Use
Machines Being Monitored
How to Use the Ansible Build
Description of the Topology
The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly balanced, in addition to restricting access to the network.

Load balancers protect systems from DDOS by shifting attack traffic. The advantage of a Jumpbox is to give access to the uswer from a single node.
Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the to the jumpbox and system network.

What does Filebeat watch for? Logged events, which are forwared to Elasticsearch.
What does Metricbeat record? Metrics and statistics.
The configuration details of each machine may be found below. Note: Use the Markdown Table Generator to add/remove values from the table.

Name	Function	IP Address	Operating System
Jump Box	Gateway	10.0.0.6	Linux
Web 1	Site Host	10.0.0.7	Linux
Web 2	Site Host	10.0.0.8	Linux
ELK	Monitor	10.1.0.4	Linux
Access Policies
The machines on the internal network are not exposed to the public Internet.

Only the Jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:

24.167.14.47
Machines within the network can only be accessed by Jump Box.

My workstation has access to the ELK machine using IP: 24.167.14.47
A summary of the access policies in place can be found in the table below.

Name	Publicly Accessible	Allowed IP Addresses
Jump Box	Yes	24.167.14.47
ELK	Yes	24.167.14.47
Elk Configuration
Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...

The reason we use automation is for ease and repeatablity quickly and accurately.
The playbook implements the following tasks:

Install Docker
Download images
Run container
The following screenshot displays the result of running docker ps after successfully configuring the ELK instance.

Images/Image 1

Target Machines & Beats
This ELK server is configured to monitor the following machines:

10.0.0.7
10.0.0.8
We have installed the following Beats on these machines:

Filebeats
Metricbeats
These Beats allow us to collect the following information from each machine:

Filebeats allows us to collect logs of system events to be sent to Elasticsearch.
Metricbeats monitors system health and records events for archiving.
Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned:

SSH into the control node and follow the steps below:

Copy the playbook file (*.yml) to ansible directory.
Update the playbook file to include what you want to install and change.
Run the playbook, and navigate to machine to check that the installation worked as expected using command "Docker ps".
