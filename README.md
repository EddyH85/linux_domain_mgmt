<h1>Linux Active Directory Domain Mangement</h1>
This is an Ansible role to automaticaly join or leave a Active Directory Domain with a Linux Machine using Kerberos and SSSD.
This role is tested on RedHat/CentOS 7-9, Ubuntu LTS releaeses 16-22 and Debian 10, 9, 8 as well as open(SUSE) 11-15.

# Requirements

- Ansible >= 2.6
- Active Directory Service-User
- Configured NTP-Client
- DNS configuration and correct entries

# Installation

ansible-galaxy install EddyH85.linux_domain_mgmt

# Role Variables

file: defaults/main.yml
The Role uses the following variables, which you should override in your playbook:

```yaml
join_domain: true # true/ flase - join or leave Active Directory Domain
DomainName: linuxlab.local # replace linuxlab.local with your Domainname
realm: LINUXLAB.LOCAL # replace this value with your Domainname in Uppercase
Join_OU: OU=Server,OU=Germany,DC=linuxlab,DC=local # replace this Value with your LDAP path
# Credentials
Join_User: ADMDOMAIN
Join_User_Pass: admdomainpassword

# Permissions
PermitAdminUsers: Administrator # set here your administrative Users comma separates
PermitAdminGroups: LinuxAdmins # set here your administrative Groups comma separates
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
    Join_User: ServiceUser
    Join_User_Pass: ServiceUserPWD
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
