<h1>Linux Active Directory Domain Mangement</h1>
This is an Ansible role to automaticaly join or leave a Active Directory Domain with a Linux Machine using Kerberos and SSSD.
This role is tested on RedHat/CentOS 7.x, 8.x 6.6, Ubuntu 22, 20, 18, 16 and Debian 10, 9, 8 wie auch open(SUSE) 11.x, 12.x, 15.x.

# Requirements

- Ansible >= 2.6
- Active Directory Service-User

# Installation

ansible-galaxy install EddyH85.linux_domain_mgmt

# Role Variables

file: defaults/main.yml and vars/credentials.yml
The Role uses the following variables, which you should override in your playbook:

```yaml
file: defaults/main.yml

join_domain: true # true/ flase - join or leave Active Directory Domain
DomainName: linuxlab.local # replace linuxlab.local with your Domainname
realm: LINUXLAB.LOCAL # replace this value with your Domainname in Uppercase
Join_OU: OU=Server,OU=Germany,DC=linuxlab,DC=local # replace this Value with your LDAP path
PermitAdminUsers: Administrator # set here your administrative Users comma separates
PermitAdminGroups: LinuxAdmins # set here your administrative Groups comma separates
```

```yaml
file: vars/credentials.yml

Join_User: ADMDOMAIN
Join_User_Pass: admdomainpassword
```

 # Example Playbook
```yaml
---
- hosts: lx64*
  gather_facts: yes
  become: true
  roles:
    - EddyH85.linux_domain_mgmt

  vars:
    Join_User: tu-adjoin
    DomainName: linuxlab.de
    Join_User_Pass: Passw0rd
    realm: LINUXLAB.DE
    Join_OU: OU=Server,OU=Germany,OU=Linuxlab,DC=linuxlab,DC=de
    PermitAdminUsers: Administrator
    PermitAdminGroups: D_LINUX_ADMINs
    join_domain: true
```

## Testing

This role is tested on Linux distributions:

- (open)SUSE 12 and 15
- RHEL/CentOS 8
- RHEL/CentOS 7
- RHEL/CentOS 6
- Debian 10
- Debian 9
- Debian 8
- Ubuntu 22.04
- Ubuntu 20.04
- Ubuntu 19.10
- Ubuntu 18.04
- Ubuntu 16.04
