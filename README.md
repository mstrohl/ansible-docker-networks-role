# docker-networks
An Ansible Docker network role for yum,apt and pip installation.

It includes network's removal when not defined in the list

## Prerequisites

python >= 2.6

docker-py >= 1.7.0

The docker server >= 1.9.0

## Usage

Include the folder in your roles directory. You can edit the configuration in, for example, your group_vars, like this:

```
 docker_networks:
   - name: internal
     appends: True       # la liste ci-dessous est traité en ajout si False => seul les containers ci-dessous
     connected:          # seront connectés au réseau (tout container non référencé sera exclu)
       - container1
       - container2
     driver: bridge
     state: present      
   - name: external
     state: absent # En cas de suppression si des containers sont connectés au réseau il ne sera pas supprimé sauf avec l option force
     force: True
```
## Parameters

Parameters are some of ansible's module docker_network parameters that fit my needs(http://docs.ansible.com/ansible/latest/modules/docker_container_module.html)
```
#global params
playbook_debug: 
enable_remove_unwanted_networks:  
# network definition  
  - name: 
    appends: 
    connected: 
    driver: 
    state: 
    force: 
```
## Author

STROHL Matthieu <postmaster@smartdeploy.io>

## License

MIT