## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

(https://github.com/NatalieTiona/Natalie-Cybersecurity/tree/main/Diagrams)


These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

 (https://github.com/NatalieTiona/Natalie-Cybersecurity/blob/main/Ansible/filebeat-playbook.yml)

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available in addition to restricting access to the network.
- Load balancing is effective at preventing DDoS attacks. The advantage of the Jump Box is to provide a gateway router to your private network ensuring that all of your other machines in the network do not directly face the internet. This then provides a more secure network.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the network and system logs.
- Filebeat collects data about the file system logs, which files have changed and when they changed.
- Metricbeat collects machine metrics, such as uptime.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.6   |Linux            |
| WEB-1    |DVWA container| 10.0.0.7  |Linux               
| WEB-2    |DVWA container| 10.0.0.8  |Linux                 
| Elk-Web  |Log analyzer  | 10.1.0.4  |Linux             |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the JumpBox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- The IP address I have whitelisted is my personal IP

Machines within the network can only be accessed by
- The ELK server can be accessed from the WEB-1, WEB-2, and Jump Box machines

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box |No                  |Personal IP           |
| Web-1    |No                  |20.185.45.94,10.0.0.7|                    
| Web-2    |No                  |20.185.45.94,10.0.0.8|
| ELK      |No                  |137.135.27.83

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
-The main advantage of automating configuration with Ansible is that it enables IT administrators the ability to automate your daily work tasks  

The playbook implements the following tasks:
-Configure Elk VM with Docker
Install docker.io
Install pip3
Download and launch a docker elk container
The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![docker.ps](https://github.com/NatalieTiona/Natalie-Cybersecurity/blob/main/ps%20.png)

 
### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- WEB-1 Web Server 10.0.0.7
- Web-2 Web Server 10.0.0.8

We have installed the following Beats on these machines: I have successfully installed and ran filebeats on both web-1 and web-2 VM

These Beats allow us to collect the following information from each machine:
-  Filebeat will collects and monitors all log files or specific locations that are specified.
Metricbeats will periodically collect metrics from the operating system and from services running on the server. 
 
### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the elk_install.yml file to /etc/ansible/roles/elk_install.yml
- Update the hosts file to include (IP ansible_python_interpreter=/usr/bin/python3
-Run the playbook, and navigate to http://[your_elk_server_ip]:5601/app/kibana to check that the installation worked as expected
