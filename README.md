## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

Diagrams/Week 13 Diagram.PNG

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the kibana file may be used to install only certain pieces of it, such as Filebeat.

  Playbook: Ansible/install-elk.yml

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly balanced, in addition to restricting access to the network.
- A load balancer is able to evenly distribute all incoming network traffic across multiple servers to keep balance and order and help prevent downtime. A load balancer can even create new servers if needed to spread out network traffic more. This helps protect networks from denial of service (DOS) attacks. The main advantage of a jump box server is that, if properly configured and secured, they serve as a single access point between the user and their virtual machines and thus help prevent any potential loopholes or backdooors into these machines.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the jumpbox and system network.
-Filebeat watches for and logs events in the file system (usually for specific files such as Microsoft Azure and Apache), such as when files have been added or removed or edited in any way. It then sends this log data over to Elasticsearch and Logstash.
-Metricbeat records machine metrics and statistics such as uptime and memory usage.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| Web-1    |Webserver | 10.0.0.5   | Linux            |
| Web-2    |Webserver | 10.0.0.6   | Linux            |
| Web-3    |Webserver | 10.0.0.7   | Linux            |
| ELK      | Data Log | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
-72.182.40.80

Machines within the network can only be accessed by Jumpbox.

-My personal workstation has access to Jumpbox via IPv4 address 72.182.40.80

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 72.182.40.80-Port80  |
|   ELK    | Yes                 | 72.182.40.80-Port5601|
|          |                     |                      |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- Automatically configuring our ELK machine using Ansible is a lot more efficient than manually configuring it as it is much less time-consuming and using an already verified and functional configuration helps ensure our new machine will also work and function as needed.

The playbook implements the following tasks:
- Configure ELK VM with Docker
- Gather facts and data
- Install docker.io
- Install python3-pip
- Install Docker module
- Increase virtual memory
- Download and launch ELK docker container
- Enable service docker on boot

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

Images/ELK-SERVER.PNG

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web-1: 10.0.0.5
- Web-2: 10.0.0.6
- Web-3: 10.0.0.7

We have installed the following Beats on these machines:
- Filebeats
- Metricbeats

These Beats allow us to collect the following information from each machine:
- Filebeats collects system log data (such as events when files and applications in the system are changed, added, or removed) and forwards that data to Elasticsearch.
- Metricbeats monitors and reports data metrics on systems such as CPU and memory usage and top processses used.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the playbook file (EX: install-elk.yml) to the /etc/ansible directory.
- Update the hosts file (command: nano /etc/ansible/hosts to add a specified group to run the playbook on (EX: create ELK group to run the install-elk.yml playbook)
- Run the playbook (command: ansible-playbook install-elk.yml), and navigate to http://[your.ELK-VM.External.IP]:5601/app/kibana to check that the installation worked as expected.
