# elk-ansible

This is an ansible project for deployment of ELK Stack, Elasticsearch, Kibana, Filebeat, Metricbeat on multiple hosts as per the host configuration file.



## Steps to use this project

    *Update host list in each of the environments
    *Setup your own ansible vault with ES_PWD and KIBANA_PWD values

## To Deploy ELK Component run the following commands

    *ansible-playbook --private-key <your_key_file> -e role=[filebeat | metricbeat | elasticsearch] -i <env_name> deploy_playbook.yml

### Ansible Vault
Keep vaulted variables safely visible
You should encrypt sensitive or secret variables with Ansible Vault. However, encrypting the variable names as well as the variable values makes it hard to find the source of the values. You can keep the names of your variables accessible (by grep, for example) without exposing any secrets by adding a layer of indirection:

Create a group_vars/ subdirectory named after the group.

Inside this subdirectory, create two files named vars and vault.

In the vars file, define all of the variables needed, including any sensitive ones.

Copy all of the sensitive variables over to the vault file and prefix these variables with vault_.

Adjust the variables in the vars file to point to the matching vault_ variables using jinja2 syntax: db_password: {{ vault_db_password }}.

Encrypt the vault file to protect its contents.

Use the variable name from the vars file in your playbooks.