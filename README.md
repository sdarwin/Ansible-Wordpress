
# Ansible Role: WordPress

Installs WordPress and all dependencies (including MySQL and Apache) on either Ubuntu or RedHat. 

The role is designed for long-term production use where an important focus will be ongoing deployment, rather than only installation. A deployment playbook is included in the role.

## Prerequisites

None. 

## Instructions

This role has an examples/inventories folder, which you should copy into your own ansible installation and modify as needed, such as with this command:
```
cp -rp examples/inventories /etc/ansible
```

The resulting directory structure is
```
inventories/
 ├── dev
 │   ├── group_vars
 │   │   └── all
 │   └── hosts
 ├── staging
 │   ├── group_vars
 │   │   └── all
 │   ├── hosts
 └── prod
    ├── group_vars
    │   └── all
    └── hosts
```

Customize and review all variables there. Every deployed environment (staging, production, and so on) may have it's own set of passwords, URL's, variables and hosts. Encrypt each group_vars/all file with ansible-vault for added security.

Next, here are the steps to install and deploy in each environment.

Dev Servers:

setup (likely only run once)
```
ansible-playbook --ask-vault-pass -i inventories/dev bootstrap.yml
```

deploy (every time code changes)
```
ansible-playbook --ask-vault-pass -i inventories/dev deploy.yml
```

Staging Servers:

setup (likely only run once)
```
ansible-playbook --ask-vault-pass -i inventories/staging bootstrap.yml
```

deploy (every time code changes)
```
ansible-playbook --ask-vault-pass -i inventories/staging deploy.yml
```

Production Servers:

setup (likely only run once)
```
ansible-playbook --ask-vault-pass -i inventories/prod bootstrap.yml
```

deploy (every time code changes)
```
ansible-playbook --ask-vault-pass -i inventories/prod deploy.yml
```

## License

GPLv2

## Author Information

By Sam Darwin, 2017

Feedback and bug reports welcome.
