# Implantação de Monitoramento Zabbix com Grafana pelo Docker Compose

## Introdução

Neste projeto, uma máquina virtual do Vagrant é provisionada pelo Ansible, que executará as roles docker e zbxgrafana.

A role docker instala o Docker, Docker Compose e as bibliotecas Python docker e docker-compose, para que o Ansible consiga se comunicar com o Docker e execute o módulo docker\_compose.

O arquivo [docker-compose.yml](./docker-compose.yml) define os serviços db, server, frontend e grafana, que por sua vez, contêm as especificações para a criação de containers do MySQL, Zabbix Server, Zabbix Frontend e Grafana.

A role zbxgrafana executa o comando para iniciar os serviços definidos no arquivo docker-compose.yml.

## Como usar este projeto

Para iniciar a máquina virtual, execute:

`vagrant up`

Para acessar o Zabbix Frontend, digite na barra de pesquisa de um navegador web:

`192.168.56.2:8081`

Assim que aparecer a tela de login do Zabbix, digite as seguintes credenciais:

Nome do usuário: Admin

Senha: zabbix

Para acessar o Grafana, digite na barra de pesquisa de um navegador web:

`192.168.56.2:3000`

Assim que aparecer a tela de login, digite as seguintes credenciais:

Nome do usuário: admin

Senha: admin

Para fins de teste, pule a criação de uma nova senha, clicando em "Skip"
