## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

! Network diagram: https://github.com/pbruhin/Projectw13/blob/main/Diagrams/Week%2012%20net%20diagram.jpg

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

  - https://github.com/pbruhin/Projectw13/blob/main/Ansible/Metricbeat-Config.yml
  - https://github.com/pbruhin/Projectw13/blob/main/Ansible/filebeat-playbook.yml
  - https://github.com/pbruhin/Projectw13/blob/main/Ansible/install-elk.yml
  - https://github.com/pbruhin/Projectw13/blob/main/Ansible/metricbeat-playbook.yml
  - https://github.com/pbruhin/Projectw13/blob/main/Ansible/pentest.yml
  
  This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.
- What aspect of security do load balancers protect? What is the advantage of a jump box?_
- Load balancers protect the availability of the servers by spreading the requests across multiple machines.  The advantage of a jump box is that it is a secure computer that admins first connect to before launching any administrative task or use as an origination point to connect to other servers or untrusted environments.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the data and system logs.
- What does Filebeat watch for?_ Filebeat monitors the log files or locations that you specify, collects log events, and forwards them either to Elasticsearch or Logstash for indexing.
- What does Metricbeat record?_ Metricbeat helps you monitor your servers by collecting metrics from the system and services running on the server.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name      | Function      | IP Address     | Operating System |
|-----------|---------------|----------------|------------------|
| Jump Box  | Gateway       | 10.0.0.4       | Linux            |
| Web 1     | Server        | 10.0.0.5       | Linux DVWA       |
| Web 2     | Server        | 10.0.0.6       | Linux DVWA       |
| Web 3     | Server        | 10.0.0.7       | Linux DVWA       |
| RedTeamLB | Load Balancer | 20.121.222.144 |                  |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the load balancer machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- _100.19.115.100_

Machines within the network can only be accessed by SSH.
- Which machine did you allow to access your ELK VM? What was its IP address?_My terminal is allowed to reach the ELK VM. My terminal IP is 100.19.115.100, the ELK IP address is 20.62.89.232

A summary of the access policies in place can be found in the table below.

| Name         | Publicly Accessable | Allowed IP Addresses |
|--------------|---------------------|----------------------|
| Jump Box     | No                  | My host machine      |
| Web 1        | No                  | 10.0.0.4             |
| Web 2        | No                  | 10.0.0.4             |
| Web 3        | No                  | 10.0.0.4             |
| Elk-Stack-VM | No                  | My host machine      |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- What is the main advantage of automating configuration with Ansible?_ simplicity

The playbook implements the following tasks:
- Gets docker install file
- Install python3-pip
- Use pip to install docker
- Increases memory
- downloads and installs elk docker container
- Makes docker enabled on boot

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

https://github.com/pbruhin/Projectw13/blob/main/Images/ekk_stack_docker_ps.png

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.0.4 ansible_python_interpreter=/usr/bin/python3
- 10.0.0.5 ansible_python_interpreter=/usr/bin/python3
- 10.0.0.6 ansible_python_interpreter=/usr/bin/python3


We have installed the following Beats on these machines:
- Filebeat and Metricbeat

These Beats allow us to collect the following information from each machine:
- In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. 
- Filebeat monitors the log files or locations that you specify, collects log events, and forwards them either to Elasticsearch or Logstash for indexing. Filebeat watches for changes to specified logs.
- Metricbeat helps you monitor your servers by collecting metrics from the system and services running on the server.


### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the config.yml file to /etc/ansible.
- Update the config.yml file to include ELK private ip.
- Run the playbook, and navigate to the Kibana site to check that the installation worked as expected.

_ Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_YAML files are the playbook, and are copied into the /etc/ansible directory.
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_Edit the hosts file to include the ip addresses of the machines.

- [webservers]
- 10.0.0.5 ansible_python_interpreter=/usr/bin/python3
- 10.0.0.6 ansible_python_interpreter=/usr/bin/python3
- 10.0.0.7 ansible_python_interpreter=/usr/bin/python3
-
- [elk]
- 10.2.0.4 ansible_python_interpreter=/usr/bin/python3

- _Which URL do you navigate to in order to check that the ELK server is running? http://20.62.89.232:5601/app/kibana

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
