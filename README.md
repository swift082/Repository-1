## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

Diagrams/Week 13 Diagram.PNG

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

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
- A load balancer is able to distribute all incoming network traffic across multiple servers to keep balance and order. A load balancer can even create new servers if needed to spread out network traffic more. This helps protect networks from denial of service (DOS) attacks. The main advantage of a jump box server is that, if properly configured and secured, they serve as a single access point between the user and their virtual machines and thus help prevent any potential loopholes or backdooors into these machines.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the jumpbox and system network.
- _TODO: What does Filebeat watch for? Filebeat watches for and logs events in the file system (usually for specific files such as Microsoft Azure and Apache), such as when files have been added or removed or edited in any way. It then sends this log data over to Elasticsearch and Logstash.
- _TODO: What does Metricbeat record? Metricbeat records machine metrics and statistics such as uptime and memory usage.

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
-My personal computer has access to Jumpbox via IPv4 address 72.182.40.80

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 72.182.40.80         |
|   ELK    | Yes                 | 72.182.40.80         |
|          |                     |                      |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- Automatically configuring our ELK machine using Ansible is much more efficient that manually configuring it as it is much less time-consuming and using an already verified and functional configuration helps ensure our new machine will also work and function as needed.

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
- _TODO: List the IP addresses of the machines you are monitoring_

We have installed the following Beats on these machines:
- _TODO: Specify which Beats you successfully installed_

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the _____ file to _____.
- Update the _____ file to include...
- Run the playbook, and navigate to ____ to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- _Which URL do you navigate to in order to check that the ELK server is running?

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
