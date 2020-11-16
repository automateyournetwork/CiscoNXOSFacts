# CiscoNXOSFacts

Ansible Playbooks to gather and transform Cisco NXOS Facts into human readable documentation automatically

[![published](https://static.production.devnetcloud.com/codeexchange/assets/images/devnet-published.svg)](https://developer.cisco.com/codeexchange/github/repo/automateyournetwork/CiscoNXOSFacts)

## Written by John Capobianco

Using the Ansible NXOS_facts module these playbooks first gather facts, displays the facts to the screen, saves RAW JSON, Nice JSON, Nice YAML, CSV, Markdown, and interactive HTML Mind Map files from the returned stateful data. 

### Prerequisites

1) Install Ansible

    $ pip install --user ansible

    Centos:

    yum install python

    yum install ansible

2) Check version of Ansible

    $ansible --version

    ansible 2.9.1

3) Install JMESPATH

    pip install --user jmespath

4) Install node.js and npm

    curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -

5) Clone the Repository

    git clone https://github.com/automateyournetwork/CiscoNXOSFacts.git

### CUSTOMIZE

In the hosts file replace the dummy CORE (AGG) / ACCESS hostnames with your own hostnames.
Ensure Linux host running Ansible playbook can SSH into targetted hosts using prompted username and password.

### Run the playbook

After updating the hosts file with the proper hostnames run the playbook.

cd CiscoNXOSFacts

cd playbooks

ansible-playbook CiscoDCCoreFacts.yml

<answer prompts for credentials> 

<playbook gathers facts>

<playbook creates files>

cd ..

cd documentation/DC/FACTS/CORE/

ls

Review files

Run CiscoAccessFacts.yml after customizing hosts and gather facts and create reports for that logical layers.

### Topology

![Toplogy](/topology.png?raw=true")

### Output files

The following files are created per host:

NXOS Facts - General 

(inventory_hostname)_NXOS_Facts_RAW.json - ALL RAW JSON returned data

(inventory_hostname)_NXOS_Facts_Nice.json - All JSON returned data filtered to Nice JSON

(inventory_hostname)_NXOS_Facts.yml - All returned data in Nice YAML

(inventory_hostname)_NXOS_facts.csv - Custom fields in CSV

(inventory_hostname)_NXOS_facts.md - Custom fields in Markdown

(inventory_hostname)_NXOS_facts.html - Custom fields interactive HTML mind map

NXOS Facts - IP Addresses

(inventory_hostname)_IP_facts.csv - All IP addresses in CSV

(inventory_hostname)_IP_facts.md - All IP addresses in Markdown

(inventory_hostname)_IP_facts.html - All IP Address interactive HTML mind map

NXOS Facts - Interfaces

Includes physical interfaces, SVIs, port-channels, subinterfaces, tunnel interfaces, and loopback interfaces

(inventory_hostname)_Interface_facts.csv - All interfaces in CSV

(inventory_hostname)_Interface_facts.md - All interfaces in Markdown

(inventory_hostname)_Interface_facts.html - All interfaces interactive HTML mind map

NXOS Facts - Neighbors

Includes all CDP detected neighbors

(inventory_hostname)_Neighbor_facts.csv - All neighbors in CSV

(inventory_hostname)_Neighbor_facts.md - All neighbors in Markdown

(inventory_hostname)_Neighbor_facts.html - All neighbors interactive mind map

NXOS Facts - Fans

(inventory_hostname)_Fan_facts.csv - All Fans in CSV

(inventory_hostname)_Fan_facts.md - All Fans in Markdown

(inventory_hostname)_Fan_facts.html - All Fans interactive mind map

NXOS Facts - Features

(inventory_hostname)_Feature_facts.csv - All Features in CSV

(inventory_hostname)_Feature_facts.md - All Features in Markdown

(inventory_hostname)_Feature_facts.html - All Features interactive mind map

NXOS Facts - Modules

(inventory_hostname)_Module_facts.csv - All Modules in CSV

(inventory_hostname)_Module_facts.md - All Modules in Markdown

(inventory_hostname)_Module_facts.html - All Modules interactive mind map

NXOS Facts - Power Supplies

(inventory_hostname)_PowerSupply_facts.csv - All Power Supplies in CSV

(inventory_hostname)_PowerSupply_facts.md - All Power Supplies in Markdown

(inventory_hostname)_PowerSupply_facts.html - All Power Supplies interactive mind map

NXOS Facts - VLANs

(inventory_hostname)_VLAN_facts.csv - All VLANs in CSV

(inventory_hostname)_VLAN_facts.md - All VLANs in Markdown

(inventory_hostname)_VLAN_facts.html - All VLANs interactive mind map

#### DEVELOPMENT NOTES

Developed with VS Code, Ansible, CentOS

Tested at vertical scale (1+n devices in the CORE / DIST / ACCESS groups) and horizontally against:

Cisco Nexus 9000, 7000, 5000 + 2000 FEX hardware platforms
