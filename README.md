# Simple deploy elasticsearch cluester 

## Installation
1. add hosts as many as you need to /etc/ansible/staging inventory in group elasticsearch_cluster or create your host inventory named elasticsearch_cluster
2. install ansible & and edit config file to acclaim your preferences
3. ssh-keygen on master-host (only first run)
4. scp \~/.ssh/id\_rsa.pub <user>@<hostanme>:~/.ssh/new via all hosts
5. on hosts: cat ~/.ssh/new >> ~/.ssh/authorized_keys && rm -f ./new
6. parametrize /etc/ansible/roles/elastic_cluster/defaults/main.yml

## How to deploy roles via playbooks:
* dry run with diff on default staging inventory via limit host `ansible-playbook /etc/ansible/playbook/elastic_cluster.yml -C -D --limit=<hosts or group>`
* one host or group install `ansible-playbook /etc/ansible/playbook/elastic_cluster.yml --limit=<host or group>`
* via defaut inventory: `ansible-playbook /etc/ansible/playbook/elastic_cluster.yml --limit=elastic_cluster`
