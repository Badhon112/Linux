## Linux

1. How do you check free disk space?
   - du -sh directory_name
2. How do you compress a file using gzip
   - gzap filename
3. How do you decompress a gzip file
   - gunzip filename.gz
4. How do you archive multiple files using tar?
   - tar -czvf _archive.tar.gz_ file.txt file2.txt
5. how do you extract a tar.gz files?
   - tar -xzvf _archive.tar.gz_
   - tar is an archiver(bundler file without reducing file).
   - gzip is a compressor (Shrinks a single file but can't bundle folder).
   - zip is a hybrid utility that both compress and bundle.
6. How do you mount a filesystem
   - mount device_name mount_point
7. How do you unmount a filesystem
   - unmount mount_point
8. How do you create a symbolic Link?
   - ln -s target_file link_name
9. How do you view file types in a directory?
   - file filename
10. What is a firewall, and how do you configure it on Linux?
    - A firewall is a network security system that monitoring and controls incoming and outgoing network traffic. In Linux, you can configure a firewall using iptables or firewalld.

---

## Jenkins

- The 3 major element is
  - Pipeline : The Block of script contents
  - Agents : Defines where the pipeline will start running from
  - Stage : The pipeline contain several steps enclosed in the block called stage

```bash
pipeline{
agent any
   stages{
      stage("Code Pull"){
         steps{
            // Statement
         }
      }
   }
}
```

---

## Ansible

- Ansible Playbook

```bash
---
- name: Install and start Nginx
  hosts: webservers
  become: true
  tasks:
    - name: Install nginx package
      apt:
        name: nginx
        state: present
        update_cache: yes
    - name: Start nginx service
      service:
        name: nginx
        state: started
        enabled: yes

```
