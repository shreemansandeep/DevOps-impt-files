The main components of Ansible are playbooks, configuration management, deployment.

Ansible uses playbooks to deploy, manage, build, test and configure anything from full server environments to custom compiled source code for applications.

Ansible was written in Python.

Ansible Features :

Ansible manages machines in an agent-less  manner  using  SSH. Built on top of Python and hence provides a lot of Python’s functionality. YAML-Based Playbooks

Uses SSH for secure connections.

Follows Push based architecture for sending configurations.
server
--------

yum install epel-release

yum update -y

yum install git python2 python2-devel python2-pip openssl ansible
or
yum install python -y
yum install openssl -y
yum install ansible -y


ansible --version

cd /etc/ansible 
--------------------

vi ansible.cfg
-----------------
inventory
sudo_user

vi hosts
-----------

[batch37]
ip
ip
ip
hostname
..
..

[group1]
ip
ip
...
...
...

adduser devops37
passwd devops37

visudo
-------
devops37 ALL=(ALL)  NOPASSWD: ALL




client
-------

adduser devops37
passwd devops37

visudo
-------
devops37 ALL=(ALL)  NOPASSWD: ALL

su - devops37

server
--------

su - devops37

ssh-keygen -t rsa

ls -la

scp src root@ip:/path
scp -r src root@ip:/path

ssh-copy-id devops37@client-ip

ssh client-ip

ansible batch37 -m ping

-------------------------------------------------------------------

ansible all -a "ls -l /opt"

ansible all -a "cat /etc/passwd"

ansible 192.168.58.131 -a "cat /etc/passwd"

ansible batch36 -b -a "touch /opt/sony1"

ansible batch36 -a "mkdir /opt/test678" -b

ansible all -m copy -b -a "src=path/of/file dest=/path"

ansible all -m yum -b -a "name=git"
ansible all -m yum -b -a "name=git state=preasent"

ansible all -a "yum install git -y" -b
ansible all -b -a "yum install git -y"

ansible all -m yum -b -a "name=git state=present"

ansible all -m yum -b -a "name=git state=absent"

ansible all -b -a "yum remove git -y"

ansible all -m yum -b -a "name=httpd state=present"

ansible all -m service -b -a "name=httpd state=started"

ansible all -b -a "service httpd start"

ansible batch38 -b -a "service httpd start"
ansible all -m service -b -a "name=httpd state=started"
Ex: reloaded, restarted, started, stopped

ansible all -b -a "useradd user1"
ansible all -m user -b -a "name=user3 state=present"

ansible all -m yum -b -a "name=java state=latest"
ansible all -b -a "yum install java -y"


ansible all -b -a "useradd user1"

ansible all -m user -b -a "name=alekhya state=present"

ansible batch36 -b -a "userdel user1"

ansible all -m user -b -a "name=alekhya state=absent"

ansible all -b -a "mkdir /opt/ooooo1"

ansible all -b -a "touch /opt/abc"

ansible all -m file -b -a "path=/opt/123abc state=touch"

ansible all -m file -b -a "path=/opt/456dir state=directory"


==================================================
playbook's     yaml or yml
===========

sudo vim play1.yaml
----------------------------
---
- hosts: all
  become: yes
  tasks:
  - name: Installing git package
    yum: name=git state=latest

:wq!

ansible-playbook play1.yaml
or

ansible all -m yum -b -a "name=git state=present"

sudo vim play2.yml
-------------------------
---
- hosts: all
  become: yes
  tasks:
  - name: Installing HTTPD package
    yum: name=httpd state=present


sudo vim play3.yml
--------------------------

---
- hosts: all
  become: yes
  tasks:
  - name: Installing HTTPD package
    yum: name=httpd state=absent

sudo vim play4.yml
--------------------------
---
- hosts: all
  become: yes
  tasks:
  - name: Installing HTTPD package
    yum: name=httpd state=present
  - name: removing HTTPD package
    yum: name=httpd state=absent
  - name: installing wget package
    yum: name=wget

sudo vim play5.yml
--------------------------
ansible all -m service -b -a "name=httpd state=started"

---
- hosts: all
  become: yes
  tasks:
  - name: Installing HTTPD package
    yum: name=httpd state=present
  - name: Starting httpd services
    service: name=httpd state=started
  - name: stopping httpd services
    service: name=httpd state=stopped
  - name: reloading httpd services
    service: name=httpd state=reloaded
  - name: remove httpd package
    yum: name=httpd state=absent


---
ansible all -m copy -b -a "src=path/of/file dest=/path"

---
- hosts: all
  become: yes
  tasks:
  - name: copying rpm files from ansible server to client
    copy:
         src: /opt/jenkins-2.235.2-1.1.noarch.rpm
         dest: /opt
  - name: Installing rpm
     yum:
          name: /opt/jenkins-2.235.2-1.1.noarch.rpm
          state: present

sudo vim play6.yml
-------------------------------
---
- hosts: all
  become: yes
  tasks:
  - name: Installing no.of package
    yum: name=git,httpd,wget,java,ansible state=present

---
- hosts: all
  become: yes
  tasks:
  - name: Installing no.of package
    yum: state=absent name=git,httpd,wget,java

or

sudo vim play7.yml
-------------------------------
---
- hosts: all
  become: yes
  tasks:
  - name: Installing no.of packages
    yum: state=latest name={{item}}
    with_items:
    - git
    - httpd
    - ansible
    - wget



https://docs.ansible.com/ansible/latest/modules/list_of_all_modules.html

ansible batch36 -m copy -s -a "src=path/of/file dest=/path"


sudo vim play8.yml
-------------------------------

---
- hosts: all
  become: yes
  tasks:
  - name: copying data from ansible server
    copy: src=/home/ansible/play4.yml dest=/tmp


URL: https://docs.ansible.com/ansible/latest/modules/list_of_all_modules.html



TOWER  
Roles  ***
