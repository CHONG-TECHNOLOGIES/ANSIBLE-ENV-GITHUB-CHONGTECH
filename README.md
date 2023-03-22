# ANSIBLE
this section explain about ansible. 
- https://www.ansible.com/
- https://docs.ansible.com/

<br><br>

# GETTING STARDED
In this section you can talk about:
1.	What is ansible
2.	Concepst of Ansible 
3.	Installation
4.  Ansible Commands
5.  Inventory
6.  Important Modules
7. Ansible Collections

<br><br>

## WHAT IS ANSIBLE?
- Ansible is infra as code open source command line for automation to help teams to manage resources, installations,configurations etc etc, ansible can help you demonstrate value, connect teams, and deliver efficiencies for your organization. Built on open source, Red Hat® Ansible® Automation Platform is a hardened, tested subscription product that offers full life cycle support for organizations. Explore how Ansible can help you automate today—and scale for the future.
Ansible works with OPENSSH and has written by python

![alt text](https://chongtech.blob.core.windows.net/chongtechgithubimages/ansible.jpg)

<BR><BR>

## CONCEPTS OF ANSIBLE
### PLAYBOOK
- Is a list of plays with various tasks to run in a specific order defined in yaml file.
- Each task runs modules that perfoms action on list of hosts at inventory
- Can be tracked by control version

<br>

### INVENTORY
- REFERENCES: https://docs.ansible.com/ansible/latest/inventory_guide/intro_inventory.html

<br>

### PLAYBOOK COMMANDS
- <ins>ansible-playbook playbook.yml -b -i inventory --private-key ~/.ssh/kafka_key.pem --syntax-check --ask-vault-pass<ins>

<br>

- <ins>ansible-playbook playbook.yml --limit zookeepers --private-key ~/.ssh/kafka_key.pem -b<ins> ---> apply only for group zookeepes

<br>

- <ins>ansible-playbook playbook_user.yml -b -i inventory -e "user_name=teste" --private-key ~/.ssh/kafka_key.pem -b<ins> ---> Passando variaveis para o playbook

<BR><BR>

## INSTALLATION ANSIBLE
- References:
  . https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html#control-node-requirements
- Ansible is an agentless automation tool that you install on a single host (referred to as the control node). From the control node, Ansible can manage an entire fleet of machines and other devices (referred to as managed nodes) remotely with SSH, Powershell remoting, and numerous other transports, all from a simple command-line interface with no databases or daemons required.
<BR><BR>

#### Control node requirements
- For your control node (the machine that runs Ansible), you can use nearly any UNIX-like machine with Python 3.9 or newer installed. This includes Red Hat, Debian, Ubuntu, macOS, BSDs, and Windows under a Windows Subsystem for Linux (WSL) distribution. Windows without WSL is not natively supported as a control node
- The managed node (the machine that Ansible is managing) does not require Ansible to be installed, but requires Python 2.7, or Python 3.5 - 3.11 to run Ansible library code. The managed node also needs a user account that can SSH to the node with an interactive POSIX shell.
<BR><BR>

#### Managed node requirements
- The managed node (the machine that Ansible is managing) does not require Ansible to be installed, but requires Python 2.7, or Python 3.5 - 3.11 to run Ansible library code. The managed node also needs a user account that can SSH to the node with an interactive POSIX shell. 

<br>

- Update all packages that have available updates <br>
<ins>sudo apt update -y</ins>

<br>

- Install Python 3<br>
<ins>sudo apt install -y python3.8</ins> or 
<ins>sudo apt-get update & sudo apt-get install python3</ins> or 

<br>

- Install pip3 <br>
<ins>sudo apt install -y python3-pip</ins> or 

<br>

- Upgrade pip3 <br>
<ins>sudo pip3 install --upgrade pip</ins>

<br>

- Install Ansible <br>
<ins>sudo apt -y install ansible</ins> or <br>
<ins>pip3 install "ansible"</ins> or<br>
<ins>pip3 install "ansible==2.9.17"</ins>

<br><br>

## ANSIBLE ADOC COMMNANDS
### VERSION
- <ins>ansible --version</ins>     ------------> return info about installation and configuration like inventory file etc,etc.Normal path is /etc/ansible/ansible.cfg

<br>

### INVENTORY
- <ins>ansible-inventory -y --list</ins>           ------------> check inventory details
<br>

- <ins>ansible host_name --list-hosts</ins>        ------------> verify machine presence in inventory
<br>

- <ins>ansible-inventory -i inventory --list</ins> ------------> list hosts in inventory file

<br>

### GET DOC
- <ins>ansible-doc -l | grep search_word</ins>     ------------> list all modules
<br>

- <ins>ansible-doc module_nameg</ins>              ------------> get detail about modules por example ping

<br>

### RUN MODULES ADOC
- <ins>ansible all -m ping -i inventory  --private-key ~/.ssh/kafka_key.pem </ins>  ----------> run module ping on all destinations hosts

<br>

- <ins>ansible all -m service -i inventory  --private-key ~/.ssh/kafka_key.pem  -a "state=started name=sshd"</ins>----------> run module services on all destinations hosts to check if sshd service was starded

<br>

- <ins>ansible all -m user -i inventory  --private-key ~/.ssh/kafka_key.pem  -a "name=user_name uuid=4000 state=present password=password"</ins>----------> run module user to create new user on all destinations hosts if not exists

<br>

- <ins>ansible all -m package -i inventory  --private-key ~/.ssh/kafka_key.pem -b -a "name=httpd state=present"</ins>----------> run module package on all destinations hosts to check if httpd package was installed

<br>

- <ins>ansible all -m yum -i inventory  --private-key ~/.ssh/kafka_key.pem -b -a "name=httpd state=present"</ins>----------> run module package on all destinations hosts to check if httpd package was installed at linux distro

<br>

- <ins>ansible all -m apt -i inventory  --private-key ~/.ssh/kafka_key.pem -b -a "name=httpd state=present"</ins>----------> run module package on all destinations hosts to check if httpd package was installed at ubuntu distro


<br><br>

## MODULES
- References:
  . https://docs.ansible.com/ansible/latest/modules/modules_by_category.html

### AZURE
- REFERENCES : <br>
 . https://github.com/Azure/azure_modules <br>
 . https://learn.microsoft.com/en-us/azure/developer/ansible/ <br>
 . https://github.com/ansible-collections/azure <br>
 . https://learn.microsoft.com/en-us/azure/developer/ansible/create-ansible-service-principal?tabs=azure-cli

- INSTALL: <br>
  1 - <ins>ansible-galaxy install azure.azure_modules</ins> or <br>
  2 - <ins>sudo pip3 install ansible[azure]</ins> or <br>
  3 - <ins>ansible-galaxy collection install azure.azcollection</ins><br>

- Upgrade Azure Python SDKs required by new Azure modules: <br>
  <ins>sudo pip install -r ~/.ansible/roles/azure.azure_modules/files/requirements-azure.txt</ins> or <br>
- To upgrade to the latest version of Azure collection: <br>
  <ins>ansible-galaxy collection install azure.azcollection --force</ins><br>

- Create Service Princiapl to work with ansible<br>
.https://learn.microsoft.com/en-us/azure/developer/ansible/install-on-linux-vm?tabs=azure-cli#file-credentials<br>
. https://learn.microsoft.com/en-us/azure/developer/ansible/create-ansible-service-principal?tabs=azure-cli

<br><br>

### NETWORK
- https://docs.ansible.com/ansible/2.9/modules/list_of_network_modules.html#network-modules


<br><br>

## ANSIBLE VAULT - PROTECTING SENSITIVE DATA
- <ins>ansible-vault</ins>

<br>

- <ins>ansible-vault create file_name</ins>

<br>

- <ins>ansible-vault view file_name</ins>

<br>

- <ins>ansible-vault create file_name</ins>

<br>

- <ins>ansible-vault edit file_name</ins>

<br>

- <ins>ansible-vault encrypt file_name</ins> -----> encrypt file there already exist

<br>

- <ins>ansible-vault decrypt file_name</ins>

<br>

- <ins>ansible-vault rekey file_name</ins>--------> change a password of an encrypted file 

<br><br>

## ANSIBLE COLLECTIONS

- References:
  . https://cn-ansibledoc.readthedocs.io/zh_CN/latest/user_guide/collections_using.html<br>

- List all collections <br> 
<ins>ansible-galaxy collection list</ins>

<br>