_Ansible_ : It is an automation Tool.

- _Ansible Component_
  - Inventory : Provide the information about the server.
  - Playbook : The File where the Module has been write and execute it. We can add multiple module in a playbook
  - Module : Small program to do a task. E.x: Install Nginx, Start Docker, Start a server, Create a file.

_Server SetUP_

```bash
# On Test Server
$ sudo useradd -m -s /bin/bash newuser
$ sudo passwd newuser
$ sudo usermod -aG wheel newuser
$ groups newuser
$ sudo nano /etc/ssh/sshd_config
# Changed on PasswordAuthentication yes
$ sudo systemctl restart sshd
$ sudo systemctl status sshd

---
# On Main Server
$ ssh-keygen
$ ssh-copy-id newuser@13.232.107.70
$ ssh 'newuser@13.232.107.70'
```

_Install Ansible On Linux_

```bash
$ sudo dnf install epel-release
$ sudo dnf install ansible
$ ansible --version
$ ansible localhost -m ping
$ cd /etc/ansible/
$ sudo ansible-config init --disabled -t all | sudo tee ansible.cfg > /dev/null
$ sudo chown ec2-user:ec2-user ansible.cfg
$ sudo chown -R ec2-user:ec2-user /etc/ansible
```

_PlayBook_

```bash
# first.yaml
---
- name: Install and Start The Services
  hosts: localhost

  tasks:
    - name: Installing nginx
      yum:
        name: nginx
        state: present
    - name: Starting the nginx service
      service:
        name: nginx
        state: started
        enabled: true


---
$ ansible-playbook --syntax-check first.yaml
$ ansible-playbook first.yaml
```

---

### Overview of Ansible Playbook

```bash
---
- name: Install and Start nginx
  hosts: webserver # Assuming 'webserver' is defined in your Ansible inventory
  become: true

  tasks:
    - name: Install Nginx
      yum: # Using the yum module for package management module for package
        name: nginx # Name of the package
        state: present # Ensure the package is installed
    - name: Start Nginx
      service: # Using the service module to manage the service
        name: nginx
        state: started
        enabled: true # Ensure Nginx is enabled to start on boot

```

---

## Remote Server

```bash
$ cd /etc/ansible
$ sudo nano hosts
  [webservers]
  server1 ansible_host=13.232.xxx.xxx ansible_user=ec2-user
$ ansible webservers -i hosts -m ping
$ ansible-playbook -i hosts remote_install.yaml
```

---

_Copy Files on Remote Server_

```bash
---
- name: Copying files to remote
  hosts: all

  tasks:
    - name: Copy files
      copy:
        src: /etc/ansible/first.yaml
        dest: /tmp/
        owner: newuser
        group: newuser
        mode: 0777
        backup: true

```

---

_Create , Delete & Permission on Remote Server_

```bash
---
- name: File Module
  hosts: all

  tasks:
    - name: Creating a File
      file:
        path: /tmp/newfile.txt
        state: touch
        owner: newuser
        group: newuser
        mode: 777
    - name: Creating a directory
      file:
        path: /tmp/myFolder
        state: directory

```

---

_Run Script_
