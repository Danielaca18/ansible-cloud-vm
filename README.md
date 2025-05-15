Ansible Cloud VM
=========

An Ansible Role to create an Ubuntu Cloud VM on Proxmox.

[![Ansible Role](https://img.shields.io/badge/ansible--galaxy-ansible--role-blue.svg)](https://galaxy.ansible.com/)

Requirements
------------

This role requires community.general collection to be installed.

Required Variables
------------------

The ansible host, proxmox token id and token are required to connect to the proxmox server. The token id is the name of the token, and the token is the actual token string.
```yaml
ansible_host: ""
proxmox_user: ""
proxmox_token_id: ""
proxmox_token: ""
```

Role Variables
--------------

Available variables are listed below, along with default values (see defaults/main.yml):

```yaml
cloud_vm_pve_node: "pve"
cloud_vm_image_name: noble-server-clouding-amd64.img
cloud_vm_image_url: "https://cloud-images.ubuntu.com/jammy/current/{{ cloud_vm_image_name }}"
cloud_vm_storage_pool: pve1
cloud_vm_storage_size: 150G
```

The cloud vm image name and url are required to download the image. The storage pool is the name of the storage pool where the vm will be created. The storage size is the size of the disk for the vm.

```yaml

timezone: America/Edmonton
locale: en-US
keyboard_layout: us

```
The timezone, locale and keyboard layout are used to set the timezone, locale and keyboard layout for the vm.

```yaml

cloud_vm_user: ubuntu
cloud_vm_pass: password

```
The cloud vm user and password are used to set the username and password for the vm.

```yaml
ssh_authorized_keys:
  - ssh-rsa key user@host
```
The ssh authorized keys are used to set the ssh keys for the vm.

```yaml

cloud_vm_packages:
  - qemu-guest-agent
  - git
  - htop
  - curl
  - unzip
  - python3-pip
  - emacs

cloud_vm_cmds:
  - /usr/local/bin/start-qga.sh

```

The cloud vm packages are the packages that will be installed on the vm. The cloud vm cmds are the commands that will be run on the vm after it is created.


Dependencies
------------

None.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: username.rolename, x: 42 }

License
-------

BSD

Author Information
------------------

This role was created in 2023 by Daniel Castro
