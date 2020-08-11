## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted in ELK_Architecture.png



These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook.yml file may be used to install only certain pieces of it, such as Filebeat.



This document contains the following:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting unauthorized access to the network.

Access is granted to the network using a JumpBox, which allows our VMs to not be public facing to further prevent unwanted access to our network.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to log data and system metrics using Filebeat and Metricbeat on our server.

The configuration details of each machine may be found below.

| Name     | Function  | IP Address | Operating System |
|----------|---------- |------------|------------------|
| Jump Box | Gateway   | 10.1.0.4   | Linux            |
| Web-1    | VM        | 10.1.0.5   | Linux            |
| Web-2    | Redundancy| 10.1.0.6   | Linux            |
| ELK      | Monitoring| 10.0.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the JumpBox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 99.61.185.130 (Home Network)

Machines within the network can only be accessed by Secure Shell from the Jumpbox. 


A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 99.61.185.130        |
| Web-1    | No                  | 10.1.0.4             |
| Web-2    | No                  | 10.1.0.4           |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because this would allow future networks to be built similarly, with much more automation.

The playbook implements the following tasks:
- Install docker.io
- Install pip3
- Install Docker python module
- Increase virtual memory
- Download and launch a docker ELK container


See Docker_PS.png for confirmation the ELK container is running.


### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web-1 (10.1.0.5)
- Web-2 (10.1.0.6)

We have installed the following Beats on these machines:
- Filebeat
- Metricbeat

These Beats allow us to collect the following information from each machine:
- Filebeat - log files, locations, and events.
- Metricbeat - system metrics and services running.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the install-elk.yml file to /etc/ansible.
- Update the /etc/ansible/hosts file to include the [elk] group and the VM under the elk group. 
- Run the playbook, and navigate to the load balancer ip (52.186.141.227) to check that the installation worked as expected. See dvwa.png for the success page.