# Documentação Servidor

Esse documento descreve como foi feita a configuração do servidor e porque tais configurações foram escolhidas bem como as ferramentas nela instaladas. Tambem é descrito no mesmo todo processo (checklist) do handering para promover segurança e estabilidade no servidor.

## Hardware e Sistema Operacional
Para este servidor em especifico foi utilizado o hardware ofercido pela instituição e como se trata de um laboratorio código livre será usado o FreeBSD &reg; para manter o servidor.

Hardware|Especificação
-|-
Processador | 1 socket, 2 núcleos
Memória RAM | 2 GiB
Interface de rede | Virtualizada
Disco Rígido | 32 GB

Sistema| Versão
-|-
FreeBSD &reg;| 1803

## Particionamento do disco rígido
Utilizamos o modo de particionamento autómatico (UFS), e o esquema de particionamento GUID Partition Table (GPT).  

Partição | Tipo | Tamanho | Propósito
-|-|-|-
Partição 1 | freebsd-boot | 512 KB | BOOT Kernel
Partição 2  | freebsd-ufs| 28 GB | Armazenamento Principal
Partilçao 3 | freebsd-swap | 1 GB | SWAP

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
hostname | equipe02
DNS | localhost.localdomain
IPv4 DNS #1 | 8.8.8.8
IPv4 DNS #2 | 8.8.4.4

## Configuração IPv4
Configuração | Valor
-|-
DHCP | Desativado
Endereço IP | 192.168.1.71
Máscara de sub-rede | 255.255.255.0
Default Router | 192.168.1.1
  
## Configuração IPv6
IPv6 não foi configurado nessa máquina.

## Serviços de boot configurados
Serviço | Descrição
-|-
sshd | Secure shell daemon
dumpdev | Habilita os despejos da memória do kernel para /var/crash

## Hardening
Opções de hardening para segurança do sistema habilitadas no momento da formatação:  
- Desabilitar leitura das mensagens do buffer do kernel para usuário sem privilégios.  
- Desabilitar processos de depuração para usuários sem privilégios.  
- Limpar o diretório /tmp em toda inicialização do sistema.

## Usuários
Login | senha
-|-
root | Redes@123
equipe02 | alunoruy2018

## Atualizações do sistema

 > Ultima atualização 28/09/2018 via portsnap update.

## Firewall
 > Firewall não foi configurado, deixando assim as configurações padrões.

## Estado das portas
> Todas as portas estão fechadas menos a 80 (HTTP), 443 (SSL), 21 (FTP), 3389 (Remote Desktop), [49841,49686,49671] usadas pelo sistema. ( Verificar Portas FreeBSD)

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
Webmin|Gerenciar recursos do servidor| Habilitado por equipe02
