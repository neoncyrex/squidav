# squidav

The role configures squid to deliver catagory filtering and antivirus protection.


## Features


## Requirements
- Ansible version: 1.4 or higher
- OS: RHEL 7.x, CentOS 7.x
- Proper OS image (squid, dansguardian,clamav, c-icap, squidguard are installed and configured)

## Role Variables
    ldaphost: ldap.example.com
    customerou: ou=customer1,dc=example,dc=com
    disable_antivirus: false


## Installation (CentOS 7.x or RHEL 7.x)
```
# yum install -y git ansible
# mkdir -p /etc/ansible/roles
# cd /etc/ansible/roles
# git clone https://github.com/neoncyrex/squidav.git
# vi /etc/ansible/hosts
```
## Usage and Examples

### 1. Configure a single squid server to use ldap auth
If variables are not set in the yaml file - default values will be used
> $ cat squid.yaml
```
	- hosts: all
	  sudo: true
          roles:
		- { role: squidav, ldaphost: ldap.example.com, customerou: "ou=customer1,dc=example,dc=com", disable_antivirus: false }
```
> $ ansible-playbook squid.yaml

### 1. Configure a single squid server to use ldap auth (variables in CLI)

> $ cat squid.yaml
```
	- hosts: all
	  sudo: true
          roles:
		- { role: squidav }
```
> $ ansible-playbook  -e 'ldaphost=ldap.example.com, disable_antivirus: true, customerou="ou=customer1,dc=example,dc=com"' squid.yaml

## Author Information
Name: Artemii Kropachev
