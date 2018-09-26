# Documentação Servidor

Esse documento descreve como foi feita a configuração do servidor e porque tais configurações foram escolhidas bem como as ferramentas nela instaladas. Tambem é descrito no mesmo todo processo (checklist) do handering para promover segurança e estabilidade no servidor.

## Hardware e Sistema Operacional
Para este servidor em especifico foi utilizado o hardware ofercido pela instituição e como se trata de um laboratorio código livre será usado o FreeBSD &reg para manter o servidor.

Processador | Descrição | Motivo
-|-|-
?|?|Fornecido pela instiuição para desenvolver as atividades 

Memória| Descrição | Paginação
-|-|-
Memoria xGB com yMHz| Marca tal, usa tecnologia DDRz,  foram usados k placas para formar essa quantidade de memória | Das ? quantidade de memória estão disponiveis ? para uso e foi definido ? como quantidade de memória virtual
  
  
Memória secundária|Descrição| Motivo
-|-|-
?|?|?
  
  
Sistema| Versão | Particionamento
-|-|-
FreeBSD &reg;| 1803| Utilizamos o modo de particionamento autómatico (UFS), e o esquema de particionamento GUID Partition Table (GPT).

## Particionamento do disco rígido
Partição | Tamanho | Propósito
-|-|-
Partição 1 - freebsd-boot | 512 KB | BOOT Kernel
Partição 2  - freebsd-ufs| 28 GB | Armazenamento Principal
Partilçao 3 - freebsd-swap | 1 GB | SWAP

## Distribuições Instaladas
Componentes do sistema opcionais que foram instalados no processo de formatação da máquina.

Componentes do sistema | Descrição
-|-
base-dbg | Base System (Debugging)
doc | Additional Documentation
kernel-dbg | Kernel (Debugging)
lib32-dbg | 32-bit compatibility libraries (Debugging)
lib32 | 32-bit compatibility libraries
ports | Ports tree
src | System source tree

## Configurações de Rede
Configuração | Valor
-|-
hostname | equipe03
Interface de rede | Intel(R) PRO/1000 Legacy Network Connection 1.1.0
DNS | localhost.localdomain
IPv4 DNS #1 | 8.8.8.8
IPv4 DNS #2 | 8.8.4.4

  ## Configuração IPv4
  Configuração | Valor
  -|-
  DHCP | Desativado
  Endereço IP | 192.168.1.51
  Máscara de sub-rede | 255.255.255.0
  Default Router | 192.168.1.1
  
  ##Configuração IPv6
  IPv6 não foi configurado nessa máquina.

## Atualizações do sistema

 > Ultima atualização 01/09/2018 via Windows update.
 

## Firewall
 Está sendo usado o firewall nativo do windows, não foi instalado nenhum firewall externo em outros dispositivos ou para.
> Versão do firewall: ????
## Estado das portas
> Todas as portas estão fechadas menos a 80 (HTTP), 443 (SSL), 21 (FTP), 3389 (Remote Desktop), [49841,49686,49671] usadas pelo sistema.

##### Log netstat:

  Proto  |Endereço local       |  Endereço externo      | Estado
 -|-|-|-
  TCP  |  192.168.15.123:3389  |  DESKTOP-DTF118I:51112|  ESTABLISHED
  TCP|    192.168.15.123:49671 |  13.89.217.116:https |   ESTABLISHED
  TCP   | 192.168.15.123:49686 |  52.173.28.179:https|    ESTABLISHED
  TCP |   192.168.15.123:49841  | 64.4.54.254:https   |   TIME_WAIT
  TCP  |  [::1]:49842        |    WIN-FEDRIF0MEGQ:47001 | TIME_WAIT

## Serviços instalados

Nome|Funçao|Instalado por
-|-|-
Remote Desktop|Permite a utilização do servidor via area de trabalho remota| Habilitado por Almir
