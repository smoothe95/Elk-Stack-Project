[README.md](https://github.com/smoothe95/Elk-Stack-Project/files/7124942/README.md)
# Elk-Stack-Project
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![(Images/diagram_filename.png)]

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the configuration file may be used to install only certain pieces of it, such as Filebeat.

  - ELK-Stack-Project/Ansible/

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available for customers, in addition to restricting access to the network.
- They protect against DDOS attacks and enable user access from  a single secure node that can be tracked and monitored.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the application and system logs.
- Filebeat monitors log files or locations specified, collect log events, and forwards them either to Elasticsearch or Logstash for indexing.
- Metricbeat is an extremely reliable metric shipper for monitoring your system and the processess running on it.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function     | IP Address | Operating System |
|----------|--------------|------------|------------------|
| Jump Box | Gateway      | 10.0.0.4   | Linux            |
| Web-1    | VM via Docker| 10.0.0.7   | Linux            |
| Web-2    | VM via Docker| 10.0.0.6   | Linux            |
| Elk-VM   | Server       | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 5061 Kibana Port

Machines within the network can only be accessed by Jump-Box_Provisioner.

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 168.61.221.36        |
| Web-1    | No                  | 10.0.0.9             |
| Web-2    | No                  | 10.0.0.9             |
|Elk-VM    | Yes (HTTP)          | 10.1.0.9             |
### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- it is easily to install and prevents against any easily overlook vulnerabilities.

The playbook implements the following tasks:
- Install docker.io
- Install python3-pip
- Install Docker module
- Increase virtual memory

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![[Images/dockerps.png)]

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- | Name  | IP Address  |
  |-------|-------------|
  | Web-1 | 10.0.0.7    |
  | Web-2 | 10.0.0.6    |


We have installed the following Beats on these machines:
- Filebeat
- Metricbeat

These Beats allow us to collect the following information from each machine:
- filebeat collects log data and shows them in the monitoring clusters.
- metricbeat collects metrics and statistics and shows them in the output specified, for example Elasticsearch or Logstash.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the ansible.cfg file to "/etc/ansible/"
- Update the hosts file to include...
- Run the playbook, and navigate to Elk Server VM to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- Playbook is install-elk.yml
- Update the hosts file to include webservers and ELK. Put the IPs for the webservers 10.0.0.6 and 10.0.07.
- Run the playbook  ad navigate to Kibana to chck that the installation worked as expected. [(http://52.233.89.60:5601/app/kibana/)]

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
