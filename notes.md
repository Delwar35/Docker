# 
## Task 
- Create an ec2 instance with ansible
- download docker onto the ec2 instance 
- Get Nginx page working

### Creating Ansible vault
- cd to `/etc/ansible`
- create a directory called group_var `sudo mkdir group_var`
- cd into group_var
- create a directory called all `sudo mkdir all`
- cd into all
- create a .yml file which will be the ansible vault `ansible-vault create pass.yml`
- once you create the pass.yml file add your aws access key and you secret key
- > before you enter your aws keys it will ask you to create a password for your vault.
- > when you enter pass.yml file you will be in vim to same and exit press the *esc* button and then enter `!qw `

To check if the vault was created `ls` on the all directory and you should see the pass.yml file.
When you `cat pass.yml` the content should be encrypted 

### Run a playbook with vault
- `sudo ansible-playbook --ask-vault-pass playbook-name.yml` e.g. `sudo ansible-playbook --ask-vault-pass install_nodejs.yml`
- it will then ask you to enter your vault password

> `ansible-playbook --ask-vault-pass playbook-name.yml --syntax-check` - to check syntax in playbook


## Creating an EC2 instance using anisble playbook

```
---
- name: ec2 laucher
  hosts: local
  connection: local
  become: true

  tasks:
    - name: Create ec2 instance
      ec2:
        key_name: eng99
        instance_type: t2.micro
        image: ami-07d8796a2b0f8d29c
        region: eu-west-1
        wait: yes
        count: 1
        vpc_subnet_id: subnet-0e9b6138ff1ce18f2
        assign_public_ip: yes
        group_id: sg-0991bd349b39977fa
        instance_tags:
          Name: eng99_delwar_ansible_ec2
        aws_access_key: access-key
        aws_secret_key: secret-key

```
### Run playbook

`sudo ansible-playbook --ask-vault-pass create_ec2_instance.yml -e 'ansible_python_interpreter=/usr/bin/python3'`

## Install docker on ec2

`sudo apt install docker.io`

### Running dockerfile
```
sudo docker build -t my-nginx:latest .
sudo docker run -d -p 80:80 my-nginx
```
> location of index.html file /usr/share/nginx/html

