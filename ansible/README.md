## Ansible Module for installation Telegraf
​ 
#### Prerequisite

- ansible 2.9 
- vim

### 1.) Create Directory for Elasticsearch 
```shell 
mkdir -p /data/ansible/telegraf/source/
cd /data/ansible/telegraf
vi install-telegraf-1-14-4-1.yaml
vi inventory
```
### 2.) Run Ansible Playbook  
```shell 
ansible-playbook -i inventory install-telegraf-1-14-4-1.yaml
