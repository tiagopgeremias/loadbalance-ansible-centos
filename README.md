# Load Balance HA

*Provisionamento de Cluster Load Balance com Keepalived & Nginx.*

## Objetivo:
Provisionar toda instalação e configuração do Cluster Load Balance utilizando **Ansible 2.4** que se comunique com servidores internos rodando Apache ou Nginx na porta 80.


## Ambiente
**@lb_master**

 - CentOs 7
 - 512mb de memória
 - Acesso ssh com chave para o usuário **ansible**
 - Configuração de Sudo sem senha para o usuario **ansible**

**@lb_backup**

 - CentOs 7
 - 512mb de memória
 - Acesso ssh com chave para o usuário **ansible**
 - Configuração de Sudo sem senha para o usuario **ansible**

## Configurações do Playbook

 1. Definir IP dos servidores Load Balancer no arquivo **hosts**
 2. Setar na variável "**keepalived_virtual_ip**" localizada em **group_vars/all.yml** o IP Virtual (VIP)
 3. Setar na variável "**keepalived_auth_pass**" localizada em **group_vars/all.yml** a senha de comunicação Keepalived.
 4. Setar na variável "**webservers_node**" localizada em **group_vars/lb_servers.yml**
	- Lista (Array) contendo as informações dos servidores web
	- Ex: {ip_port: '0.0.0.0:80', weight: '5'}

## Iniciando o provisionamento

    ansible-playbook -i hosts instalacao.yml

 
    
