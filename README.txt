## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.



These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the ELK file may be used to install only certain pieces of it, such as Filebeat.

  - Filebeat_Metricbeat_Installation.yml

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.
- Load balancers help to maintain availability.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the files and system metrics.
- Filebeat watchs for changes to any files on the system, then stores the changes and originals.
- Metricbeat is for the monitor and recording of system metrics.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.1   | Linux            |
| Web1     |Container | 10.0.0.5   | Linux            |
| Web2     |Container | 10.0.0.6   |                  |
| ELKVM    |ELK Container| 10.1.0.5   | Linux         |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 75.163.226.65

Machines within the network can only be accessed by SSH.
- My laptop is the only computer allowed to SSH into this, the IP is 192.168.1.140

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 192.168.1.140        |
| Web1-2   | No                  |  75.163.226.65       |
| ELKVM    | No                  | 10.0.0.5 10.0.0.6    |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- With automation you can deploy multipul systems in minutes instead of days.

The playbook implements the following tasks:
- Set up the ELK stack
- Configure Metricbeat and Filebeat 
- Connect them all to eachother

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

~/Images/docker_ps_output.png

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
-10.0.0.5, 10.0.0.6 

We have installed the following Beats on these machines:
- Filebeat and Metricbeat

These Beats allow us to collect the following information from each machine:
- Filebeat allows us to collect and monitor information in files. Metricbeat allows us to monitor the metrics of the systems.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the Filebeat-config file to your WebVM.
- Update the Filebeat-config file to include the IP address of the ELK machine.
- Run the playbook, and navigate to Kali to check that the installation worked as expected.


- .yml files are playbook files that can be run with Ansible, they're copied into a container where ansible is installed to be deployed.
- Hosts file allows for grouping of machines so you can dictate where you want resources to be deployed.
- You would visit [the vm's public IP:5601/app/kibana]
