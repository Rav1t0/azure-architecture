# azure-architecture
Repositório criado como parte do desafio do módulo 2 do bootcamp Microsoft Azure AZ-900 da DIO. Aqui contém anotações e práticas relacionadas à arquitetura e serviços do Azure.

## Introdução
Este repositório contém anotações e práticas relacionadas à arquitetura e serviços do Azure. O Objetivo é reforçar conceitos fundamentais de nuvem e aplicar na prática recursos básicos de organização, rede e computação no Azure.

## Conceitos
Regiões, Pares de regiões e Regiões Soberanas
- Regiões: Localizações físicas que agrupam datacenters.
- Pares de Regiões: Regiões associadas a cada região, para replicação e recuperação de interrupções.
- Regiões Soberanas: Atendem requisitos específicos de governos ou regulamentações locais.

Recursos do Azure
- Menor unidade de gerenciamento dentro da nuvem
- Armazenamento, máquinas, VMs, etc..

Grupos de Recursos
- Úteis para organizar recursos em uma única unidade ou em grupos específicos, sabendo onde localizá-los.
- Nome de cada RG não pode ser alterado, porém os recursos podem ser movidos de um grupo à outro.
- Recursos podem existir em: apenas um RG; em diferentes regiões.
- Aplicações podem utilizar vários RG.

## Passo a Passo dos Recursos
1. **Grupo de Recursos - Resource Group (RG)**

    1. Acesse o Portal do Azure
    2. Clique em Create a Resource > Pesquise por "Resource Group" > Create
    3. Selecione:
        - Assinatura, ou deixe a atual
        - Nome do Grupo
        - Região
    4. Clique em Next
        - (Opcional) Adicione a Tag (etiqueta) para recursos nesse grupo
    5. Clique em "Review + create" > Create   

  - **Ponto de dica:**   
    Sempre criar um RG separado entre ambientes de teste, pois basta excluir para limpar todos os recursos, sem deixar algo para trás.

2. **Rede Virtual - Virtual Network (VNet)**
    1. Clique em Create a Resource > "Virtual Network" > Create
    2. Selecione:
        - Assinatura
        - Resource Group
        - Nome da Virtual Network
        - Região
    3. Clique em Review + create > Create

3. **Máquina Virtual - Virtual Machine (VM)**
    1. Clique em Create a Resource > "Virtual Machine" > Create
    2. Selecione:
        - Assinatura
        - Resource Group
        - Nome da Virtual Machine
        - Região
        - Imagem
        - Tamanho
    3. Na seção de Rede (Networking)
        - Selecione a rede criada anteriormente ou crie uma nova
    4. Clique em Next
        - Preencha as demais configurações, se desejado.
    5. Clique em "Review + create" > Create\

  - **Ponto de dica:**   
    Se não for necessário acesso público, desabilitar a criação de IP Público e usar apenas rede privada ou VPN, ou se for necessário, marcar IP Público, caso contrário, só será possível o acesso por meio de VPN.
  - **Ponto de atenção:**   
    Ao excluir a VM, confirmar se também excluiu discos, IPs e serviços associados. Esses recursos podem gerar cobrança.

4. **Banco de Dados SQL - SQL Database**
    1. Clique em Create a Resource > "SQL Database" > Create
    2. Selecione:
        - Assinatura
        - Resource Group
        - Nome da SQL Database
        - Server ou crie um SQL Database Server, clicando abaixo em Create New
        - Redundância de Armazenamento de Backup
        - Compute + storage (para custo do ciclo do banco de dados)
    3. Clique em Next
        - Preencha as demais configurações, se desejado.
    4. Clique em "Review + create" > Create

## Estrutura Final do projeto prático
  - **Resource Group:** AZ-900_Lab_DIO
  - **Virtual Network:** vnet-dio
  - **Virtual Machine:** vm-lab-dio
  - **SQL Database:** sqldb-lab-dio
  - **SQL Server:** sqlserver-lab-dio

## Anotações Úteis
Modelos de Nuvem (IaaS, PaaS e SaaS)
- **IaaS (Infraestrutura como Serviço) ->** O cliente gerencia quase tudo, exceto a parte física (hosts, redes, datacenter).
- **PaaS (Plataforma como Serviço) ->** O cliente foca nas aplicações, o provedor cuida da infra e da plataforma.
- **SaaS (Software como Serviço) ->** O cliente apenas consome a nuvem, em modelo de assinaturas (ex.: Microsoft 365).

Modelo de Responsabilidade Compartilhada
- **Cliente** sempre responsável por: dados, dispositivos e identidades.
- O **provedor** sempre responsável por: hosts, redes e datacenter.
- As responsabilidade intermediárias variam conforme modelo.

Benefícios da Nuvem
- Alta confiabilidade
- Escalabilidade e Elasticidade
- Confiabilidade, Previsibilidade e Segurança
- Governança e Gerenciabilidade
