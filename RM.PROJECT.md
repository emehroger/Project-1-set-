## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![diagram](https://github.com/emehroger/Project-1-set-/blob/master/Diagrams/Project%201%20Diagram.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _install-ekl.yml playbook file may be used to install only certain pieces of it, such as Filebeat.

 

### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly distributed, in addition to restricting traffic to the network.
- _: What aspect of security do load balancers protect? What is the advantage of a jump box?Load Balancers defend the organisation against (DDoS)_
The Jump Box can help to block the public IP address associated with the VM. It helps to  improve security.
Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the file and system logs.
- _TODO: What does Filebeat watch for?# log files or the locations that you specify,collects logs events and forwards them either to Elasticsearch or logstash_
- _TODO: What does Metricbeat record?_periodically collect metrics from the operating system and from services running on the server.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.13   | Linux           |
| Web-1    | server     10.0.0.14   | Linus                 
| Web-2     | Server    10.0.0.15   | linus          |                  
| Elk   |     Monitor   10.0.0.4    | linus                 

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- _TODO: Add whitelisted IP addresses_Home IP and  Jump IP 

Machines within the network can only be accessed by Jump Box.
-  Which machine did you allow to access your ELK VM? What was its IP address?52.249.88.34_

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | yes    52.249.188.34   |My Home IP 92.199.10.32
| Web-1      No |   10.0.014        
|  web-2     No |   10.0.0.15       
Elk          No     10.1.0.4
### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _TODO: What is the main advantage of automating configuration with Ansible? 
  - IT admins can begin automating away the drudgery from their daily tasks. It avoid repetitive work.

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- ..- Install docker.io
- Install python-pip
- Install docker
- sysctl module to expand/use more memory
- Download and launch the docker container Elk.
- ...

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.
root@vm-monitor:/home/azadmin# docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                                                                              NAMES
a7190506d73e        sebp/elk:761        "/usr/local/bin/star…"   12 hours ago        Up 2 minutes        0.0.0.0:5044->5044/tcp, 0.0.0.0:5601->5601/tcp, 0.0.0.0:9200->9200/tcp, 9300/tcp   elk


### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: List the IP addresses of the machines you are monitoring
- Web1  10.0.0.14, 
  Web 2 10.0.0.15_

We have installed the following Beats on these machines:
- _TODO: Specify which Beats you successfully installed_
- Filebeat
- Metricbeat
-

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc.
- _Use the syslog input to read events over TCP, UDP, or a Unix stream socket, this input will parse BSD (rfc3164) event and some variant. Example ... filebeat.inputs: - type: syslog protocol.udp.
- Metricbeat analysis the among of CPU, MEMORY AND OTHER BACKGROUND SERVICES

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the Configurationfile to /etc/Ansible/.
- Update the _Host line in the configuration____ file to include. Elk IP..
- Run the playbook, and navigate to _Kibana page then to the filebeat page to see the data___ to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_Filebeat.yml  the playbook and was copied into /etc/filebeat/filebeat.yml
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_Edit the host line the configuration file to add the Elk IP
- _Which URL do you navigate to in order to check that the ELK server is running?
-http://http://23.98.156.182:5601/app/kibana

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
- ssh azureuser@JumpBoxPublicIP
 - ssh-keygen
 - curl https://gist.githubusercontent.com/slape/5cc350109583af6cbe577bbcc0710c93/raw/eca603b72586fbe148c11f9c87bf96a63cb25760/Filebeat > filebeat-configuration.yml
 - curl https://gist.githubusercontent.com/slape/58541585cc1886d2e26cd8be557ce04c/raw/0ce2c7e744c54513616966affb5e9d96f5e12f73/metricbeat > metricbeat-config.yml
 - sudo su
 - Docker start upbeat_lederberg
 - Docker attach upbeat_lederberg
 - nano filebeat-configuration.yml
 - nano metricbeat-config.yml
 - nano install-elk.yml
 - nano filebeat.yml
 - nano metricbeat.yml
 - ansible-playbook install-elk.yml
 - ansible-playbook filebeat.yml
 - ansible-playbook metricbeat.yml