1. add hosts to /etc/ansible/staging inventory in group elasticsearch_3_nodes or create your host inventory with name elasticsearch_3_nodes 
2. install ansible &
3. ssh-keygen (only first run)
4. scp \~/.ssh/id\_rsa.pub <user>@<hostanme>:~/.ssh/new via all hosts
5. on host: cat ~/.ssh/new >> ~/.ssh/authorized_keys && rm -f ./new
6. parametrize /etc/ansible/roles/elastic_3_nodes/defaults/main.yml

## How to deploy roles via playbooks:
* dry run with diff on default staging hosts via limit host `ansible-playbook /etc/ansible/playbook/<file>.yml -C -D`
* `ansible-playbook /etc/ansible/playbook/elastic_3_nodes.yml --limit=elastic_3_nodes`
* one host install `ansible-playbook /etc/ansible/playbook/elastic_3_nodes.yml -i /etc/ansible/elastic_3_nodes --limit=nsk-bsv-rmq01`
