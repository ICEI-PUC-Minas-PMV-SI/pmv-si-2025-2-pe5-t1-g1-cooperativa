# 2 PREPARAÇÃO DO AMBIENTE EM NUVEM E VIRTUALIZAÇÃO LOCAL

# 2.1 Serviços em Máquinas Virtuais Locais pelo VirtualBox 

## 2.1.1 Servidor DHCP (Dynamic Host Configuration Protocol) 

### 2.2.2.1 Introdução 

O **Servidor DHCP (Dynamic Host Configuration Protocol)** é um protocolo de rede utilizado para atribuir automaticamente endereços IP e outras configurações de rede, como máscara de sub-rede, gateway padrão e servidores DNS, aos dispositivos conectados. 

No contexto da Cooperativa de Crédito, foi configurada uma arquitetura em que uma matriz atua como Servidor DHCP e as filiais operam como Cliente DHCP. 

Com essa configuração ele simplifica a administração da rede, evitando a necessidade de configuração manual em cada máquina e garantindo que não haja conflitos de endereços IP entre os dispositivos. 

--- 

### 2.2.2.2 Topologia da Arquitetura 

**Tipo**: Centralizado 
**Rede VPC**: 172.31.0.0/16 
**Acesso permitido:**: 0.0.0.0/0 *(para testes - POC)* 
| Função | Nome da Instância | IPv4 Privado  |     Papel     | 
| ------ | ----------------- | ------------- | ------------- | 
| Matriz | DHCP Server       | 192.168.1.1/24| DHCP Server   | 
| Cliente| Cliente Windows   | 192.168.1.51  | DHCP Cliente  | 

> **Observação**: Ambiente configurado em **Ubuntu Server 22.04 LTS.** e **Windows Server 2025.**

---

### 2.2.2.3 Máquina Virtual 

Foi criada uma máquina virtual local no Virtual Box para atuar como Servidor DHCP da Matriz da Cooperativa de Crédito. A instância foi feita utilizando o Ubuntu Server 22.04 LTS como sistema operacional e com Windows Server 2025 como cliente que irá se conectar a rede. 

<img width="1917" height="926" alt="Image" src="https://github.com/user-attachments/assets/ec87c6a5-015d-43dc-98ee-3eca11fd329b" /> 

A configuração foi realizada de forma que os arquivos estivessem na pasta /etc/netplan/00-installer-config.yaml, permitindo que o server tenha acesso as configurações estipuladas. Endereços de IP: **192.168.1.1/24**, Gateway padrão: **10.0.2.15**, DNS´s padrão primário e secundários: **8.8.8.8, 1.1.1.1**. 

> Essa máquina representa o **servidor DHCP** da Cooperativa, responsável por disponibilizar informações de IP para os computadores que se conectam ao server.

> A segunda máquina representa o **cliente DHCP** da Cooperativa, que se conecta a faixa de IP disponibilizada pelo server.

---

### 2.2.2.4 Configuração do Servidor DHCP 

#### a) Visualização das Interfaces do Sistema: 

```
bash ifconfig 
``` 

imagem aqui 

A tela do comando ifconfig no **Ubuntu**, mostra informações detalhadas sobre todas as interfaces de rede do sistema, incluindo: Nome da Interface, Endereço IPv4, Máscara de sub-rede, Endereço IPv6, Endereço MAC, Status da Interface, Pacotes enviados e recebidos, e Informações de broadcast e multicast. 
Redes configuradas: 
**enp0s3** - IP 10.0.2.15 
**enp0s8** - IP 192.168.1.1 

#### b) Instalação do Serviço 

```
bash sudo apt install isc-dhcp-server -y 
``` 

#### c) Configuração do Arquivo /etc/netplan: 

```
bash sudo nano /etc/netplan00-instaler-config.yaml
```

imagem aqui

Para garantir que o servidor mantenha IP fixo na sua interface, foi configurado o arquivo de rede **/etc/netplan00-instaler-config.yaml**. Na tela, vemos duas interfaces de rede configuradas: 

**enp0s3**: está com o DHCP ativado (dhcp4: true), ou seja, o endereço IP é obtido automaticamente do servidor DHCP. 
**enp0s8**: está com o DHCP desativado (dhcp4: false), então foi configurado manualmente com: 
**Endereço IP fixo**: 192.168.1.1/24 
**Gateway**: 10.0.2.15 
**Servidores DNS**: 8.8.8.8 e 1.1.1.1 

#### d) Configuração do Serviço: 

```
bash sudo nano /etc/dhcp/dhcpd.conf
``` 

imagem aqui 

A tela mostra a configuração do serviço DHCP através do arquivo **/etc/dhcp/dhcpd.conf**, foi configurada a **rede** 192.168.1.0 com **máscara** 255.255.255.0, onde o **range de IP’s** vai de 192.168.1.11 a 192.168.1.254, o **gateway** definido foi 192.168.1.1 e os **servidores DNS´s** são 8.8.8.8, 1.1.1.1 e o **domínio** example.org. 

#### e) Configuração da Interface de Rede: 

```
bash sudo nano /etc/default/isc-dhcp-server
```
imagem aqui 

Para definir qual interface de rede será responsável por distribuir o range de IP’s configurado no servidor DHCP, é utilizado o comando **sudo nano /etc/default/isc-dhcp-server** para abrir o arquivo de configuração para informar a interface. Como eu só possuo a **INTERFACEv4**, eu coloco **“enp0s8”** para a interface que eu quero entregar esses IP’s. 

#### f) Reiniciação do Serviço: 

```
bash sudo service isc-dhcp-server restart
``` 

--- 

### 2.2.2.5 Configuração do Cliente DHCP 

#### a) Configuração da Ethernet: 

Acessei as configurações da Ethernet e defini as opções de IP e DNS para obtenção automática. --- ### 2.2.2.6 Teste de Funcionamento e Acesso 

#### a) Windows: 

Para validar o funcionamento do servidor DHCP, o acesso foi realizado diretamente pelo usuário Windows, utilizando o IP e DNS automáticos. 

```
cpp http://34.227.47.125/
```
imagem aqui 

Podemos testar a comunicação entre a máquina Windows e a máquina Ubuntu utilizando o comando **ping 192.168.1.1**, pois ambas estão conectadas à mesma rede. 

imagem aqui 

Com o comando **ipconfig**, podemos visualizar o IP, que corresponde ao mesmo IP configurado na máquina Ubuntu. 

#### a) Ubuntu: 

imagem aqui 

Após reiniciar a máquina com o comando **sudo service isc-dhcp-server restart**, e verificar o status da mesma com **sudo service isc-dhcp-server status**, podemos ver que o servidor está **active “(running)”**, ou seja, funcionando corretamente. 

---

## 2.1.2 Servidor AD (Active Directory)

### 2.1.2.1 Introdução


O **Servidor AD (Active Directory)** na CredValeDoce foi pensado para ser uma estrutura centralizada, que será utilizada para organizar e gerenciar os recursos de rede, como computadores, grupos, usuários e para o gerenciamento de permissões e políticas de seurança. Isso permite que a cooperativa de crédito tenha mais segurança em relação as suas informações e garante que apenas pessoas autorizadas possam ter acesso a dados sensíveis. Sendo assim o AD facilita a administração da rede, dando mais padronização, agilidade e segurança aos processos internos da CVD.

---

### 2.1.2.2 Topologia da Arquitetura

**Tipo**: Centralizado
**Rede VPC**: 172.31.0.0/16
**Acesso permitido:**: 0.0.0.0/0 *(para testes - POC)*

| Função | Nome da Instância | IPv4 Privado  | IPv4 Público  | Papel        |
| ------ | ----------------- | ------------- | ------------- | ------------ |
| Matriz | AD Server         | 172.16.100.20 | xxxxxxx       | AD Server    |
| Usuário| Cliente Windows   | xxxxxxx       | xxxxxxx       | Usuário      |

> **Observação**: Ambiente configurado em **Windows Server 2025.** e **Windows Pro 2012.**

---

### 2.1.2.3 Máquina Virtual

Foi criada uma máquina virtual local no Virtual Box para atuar como Servidor AD da Cooperativa de Crédito.

A instância foi feita utilizando o Windows Server 2025 como sistema operacional e com Windows Pro 2012 como usuário que irá se conectar a rede.

<img width="1917" height="926" alt="Image" src="https://github.com/user-attachments/assets/ec87c6a5-015d-43dc-98ee-3eca11fd329b" />

Para que fosse possível fazer a configuração é necessário instalar o AD DS no servidor. Mas ele requer que um servidor DNS seja instalado anteriormente. Por isso, a instalação do DNS deve ocorrer antes do AD. Depois de cumprir esses pré requisitos, o server foi renomeado, e foi feita a promoção do servidor a controlador de domínio e o domínio raiz se tornou o credevaledoce.coop.

As configurações de IP utilizadas foram IP 172.16.100.20, a máscara de sub-rede, 255.255.255.0 e o DNS 172.16.100.2.


> Essa máquina representa o **servidor AD** da Cooperativa, responsável por centralizar, organizar e gerenciar serviços de rede.

> A segunda máquina representa o **usuário AD** da Cooperativa, que se conecta ao domínio CREDVALEDOCE.

---

### 2.1.2.4 Instalação e Configuração do Windows Server

#### a) Mudança do nome do servidor

```bash
sudo apt update && sudo apt upgrade -y
```

#### b) Instalação DNS

```bash
sudo apt install apache2 -y
```

#### c) Instalação AD DS

```bash
sudo systemctl enbale apache2 
```

#### d) Promoção do servidor a controlador de domínio

```bash
sudo systemctl start apache2
```

#### e) Adição de nova floresta credvaledoce.coop

```bash
sudo systemctl status apache2
```

#### f) Adição de unidades organizacionais em ferramentas administrativas

```bash
sudo systemctl status apache2
```

#### g) Criação de usuário

```bash
sudo systemctl status apache2
```
#### g) Delegação de controle ao usuário

```bash
sudo systemctl status apache2
```
#### h) Gerenciamento de política de grupo

```bash
sudo systemctl status apache2
```
---


### 2.2.2.6 Teste de Funcionamento e Acesso Usuário Windows 2012

Para validar o funcionamento do servidor AD, o teste foi realizado pelo usuário Windows 2012, que como podemos observar ele encontra o domínio CREDVALEDOCE.
```cpp
http://34.227.47.125/
```

Foi realizado o cadastro do usuário na rede.

Podemos perceber que as politicas de grupo estão em funcionamento porque ele não consegue entrar no painel de controle e o CMD está oculto. 

---


# 2.2 Serviços em Máquinas Virtuais na Nuvem pela AWS


## 2.2.2 Servidor WEB

### 2.2.2.1 Introdução

O **Servidor Web (Apache HTTP Server)** é um serviço reponsável por hospedar e disponibilizar páginas e aplicações web acessíveis via navegador.

No projeto da Cooperativa de Crédito, o servidor Web foi ajustado para concentrar o acesso dos funcionários da Matriz e Filiais a um painel de informações institucional.

Através do Apache, é possível publicar sites, dashboards e sistemas internos que operam em rede local ou pela internet, com controle de acesso e fácil manutenção.

---

### 2.2.2.2 Topologia da Arquitetura

**Tipo**: Centralizado
**Rede VPC**: 172.31.0.0/16
**Acesso permitido:**: 0.0.0.0/0 *(para testes - POC)*

| Função | Nome da Instância | IPv4 Privado  | IPv4 Público  | Papel        |
| ------ | ----------------- | ------------- | ------------- | ------------ |
| Matriz | WEB-Server        | 172.31.23.242 | 34.227.47.125 | Servidor Web |

> **Observação**: Ambiente configurado em uma instância **AWS EC2** do **tipo t3.micro**, executando **Ubuntu Server 22.04 LTS.**

---

### 2.2.2.3 Máquina Virtual na Nuvem

Foi criada uma máquina virtual na nuvem (instância EC2) para atuar como Servidor Web da Matriz da Cooperativa de Crédito.

A instância foi provisionada na AWS (Amazon Web Services) utilizando o Ubuntu Server 22.04 LTS como sistema operacional, dentro da mesma VPC (Virtual Private Cloud) que conecta as demais filiais.

<img width="1917" height="926" alt="Image" src="https://github.com/user-attachments/assets/ec87c6a5-015d-43dc-98ee-3eca11fd329b" />

A configuração foi realizada de forma que o Apache hospedasse os arquivos HTML na pasta padrão do serviço /var/www/html, permitindo o acesso via navegador web através do endereço público da instância.

Para fins de prova de conceito (POC), a instância foi configurada com acesso SSH (porta 22) e HTTP (porta 80) liberados no grupo de segurança.

> Essa máquina representa o **servidor web central** da Cooperativa, responsável por disponibilizar informações corporativas e documentos para as filiais de forma online.

---

### 2.2.2.4 Instalação e Configuração do Apache

#### a) Atualização dos pacotes

```bash
sudo apt update && sudo apt upgrade -y
```

#### b) Instalação do Apache

```bash
sudo apt install apache2 -y
```

#### c) Habilitando Serviço

```bash
sudo systemctl enbale apache2 
```

#### d) Iniciando Serviço

```bash
sudo systemctl start apache2
```

#### e) Verificação do serviço

```bash
sudo systemctl status apache2
```

---

### 2.2.2.5 Configuração do Diretório e Página Web

O Apache, por padrão, utiliza o diretório /var/www/html como raiz do site.

Para este projeto, foi mantido o diretório padrão e substituído o arquivo inicial index.html por uma página personalizada.

#### a) Remoção do arquivo padrão

```bash
sudo rm /var/www/html/index.html
```

#### b) Criação da nova página HTML

```bash
sudo nano /var/www/html/index.html
```

#### c) Conteúdo

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Servidor</title>
</head>
<body>
    <h1>Teste Servidor</h1>
</body>
</html>
```

#### d) Permissões de acesso

```bash
sudo chown -R www-data:www-data /var/www/html
sudo chmod -R 755 /var/www/html
```

#### e) Reinício do serviço

```bash
sudo systemctl restart apache2
```
---

### 2.2.2.6 Teste de Funcionamento e Acesso Web

Para validar o funcionamento do servidor, o acesso foi realizado diretamente pelo navegador, utilizando o IP público da instância EC2:

```cpp
http://34.227.47.125/
```

A página HTML personalizada foi exibida corretamente, confirmando o pleno funcionamento do serviço Apache.

---

### 2.2.2.7 Configuração de Rede e Segurança

A conectividade entre a instância e os usuários externos dependeu das configurações de rede na **AWS**:

| Serviço | Porta | Descrição     | Origem Permitida |
| ------- | ----- | ------------- | ---------------- |
| SSH     | 22    | Acesso remoto | 0.0.0.0/0        |
| HTTP    | 80    | Acesso web    | 0.0.0.0/0        |
| ICMP    | -     | Ping/teste    | 0.0.0.0/0        |

>Em ambiente de produção, recomenda-se **restringir o acesso HTTP a endereços específicos** e utilizar **HTTPS (porta 443) com certificado SSL**.

## 2.X.X Serviço DNS (Domain Name System)



## 2.X.X Serviço de Banco de Dados (PostgreSQL)



## 2.X.X Serviço de AD (Active Directory)



## 2.2.4 Serviço FTP (File Transfer Protocol)

### 2.2.4.1 Introdução

O File Transfer Protocol (FTP) é um protocolo padrão para transferência de arquivos entre sistemas, que garante a entrega dos arquivos e permite controle de acesso.

O serviço foi configurado com um servidor atilizando o vsftpd (Very Secute FTP Daemon), e dois clientes, um Ubuntu e um Windows utilizando o FileZilla. Dessa forma foi possível demonstrar a transferência de arquivos entre diferentes sistemas operacionais.

### 2.2.4.2 Topologia da Arquitetura

| Função            | Nome          | IPv4 Privado  | Ferramenta    |
|-------------------|---------------|---------------|---------------|
| Servidor FTP      | UbuntuSRV01T  | 172.31.29.21  | vsftpd        |
| Cliente Ubuntu    | UbuntuCliente | 172.31.29.222 | ftp           |
| Cliente Windows   | Máquina local | externo       | FileZilla     |

> **Observação:** O "UbuntuSRV01T" e "UbuntuCliente" são instâncias na AWS EC2 do tipo t2.micro com Ubuntu Server 24.04. Já a "Máquina local" é um computador pessoal com Windows 11.

### 2.2.4.3 Máquinas Utilizadas

Foram criadas duas máquinas virtuais, utilizando o serviço EC2  na AWS (Amazon WEB Services), para a configuração e testes do serviço FTP. Sendo elas, uma instância server (UbuntuSRV01T) responsável por hospedar o serviço FTP via vsftpd. E uma instância cliente (UbuntuCliente) utilizada para testes de conexão e comandos via terminal.

Além disso foi utilizada um computador pessoal com Windows 11, empregada para validar o acesso via interface gráfica utilizando o cliente FileZilla.

<img width="1917" height="1031" alt="print1" src="https://github.com/user-attachments/assets/a59424ed-834a-40e0-90b0-3db5c2aaab9f" />

### 2.2.4.4 Configuração do Servidor FTP (UbuntuSRV01T)

#### a) Atualização da máquina e instalação do serviço

```bash
sudo apt update 
sudo apt upgrade
sudo apt update
sudo apt install vsftpd -y
sudo systemctl enable vsftpd
```
As três primeiras linhas se referem à atualização da máquina, a quarta à instalação do vsftpd, e a quinta por sua vez habilita o vsftpd iniciar sempre que a máquina reiniciar.

#### b) Liberação de portas

Foi realizada a liberação da porta para o SSH (22) para não se perder a conexão com a máquina, a ativação do firewall, e por fim a liberação das portas para o ftp, 20, 21, 990, e o intervalo de 30000 a 31000 para o uso do modo passivo. 
```bash
sudo ufw allow ssh
sudo ufw enable
sudo ufw allow 20,21,990/tcp
sudo ufw allow 30000:31000/tcp
```

<img width="482" height="218" alt="print2" src="https://github.com/user-attachments/assets/c0ea3598-b729-4101-8ff7-e7c756c78178" />

Pela máquina ser uma instância na AWS é necessário liberar as portas também no grupo de segurança da instância.

<img width="1209" height="244" alt="print3" src="https://github.com/user-attachments/assets/a3b886e5-66cc-4bcc-bf17-1f5cd14b326f" />

> **Observação:** Acesso permitido a todos com "0.0.0.0/0" apenas por ser ambiente de teste e prova de conceito.

#### c) Criação de usuário

```bash
sudo useradd srvWeb
sudo passwd srvWeb
```

#### d) Criação de diretórios e arquivos necessários

```bash
sudo mkdir /etc/vsftpd
```

Foi utilizado o editor VIM para criar e já editar o arquivo com os nomes dos usuários autorizados com o comando a seguir. Ao editar o arquivo é necessário escrever o nome de cada usuário no arquivo, um por linha.

```bash
sudo vim /etc/vsftpd/user_list
```

Continuando então com a criação e permissionamento das pastas de cada usuário.

```bash
sudo mkdir -p /home/srvWeb/dados
sudo chown srvWeb:srvWeb /home/srvWeb/dados
sudo chown srvWeb:srvWeb /home/srvWeb
```

#### e) Configuração do arquivo /etc/vsftpd.conf

Ao editar o arquivo de configuração do vsftpd foi retirada a marcação de comentário da linha a seguir:

```bash
write_enable=YES
```

E adicionado o seguinte no fim do arquivo.

```bash
userlist_deny=NO
userlist_file=/etc/vsftpd/user_list

tcp_wrappers=NO

local_root=/home/srvWeb/dados

chroot_local_user=YES

allow_writeable_chroot=YES

pasv_enable=YES
pasv_min_port=30000
pasv_max_port=31000
pasv_address=18.212.252.103
```

Significado das alterações:

write_enable=YES: habilita escrita e upload de arquivos pelo usuário.

userlist_deny=NO: somente usuários listados podem acessar.

userlist_file=/etc/vsftpd/user_list: indica local onde está o arquivo com a lista de usuários permitidos.

tcp_wrappers=NO: possibilita a listagem de arquivos.

local_root=/home/srvWeb/dados: entrega a pasta que deve ser carregada ao logar com o usuário, deve ser indicada para cada usuário criado.

chroot_local_user=YES: ter uma pasta home para cada usuário logado.

allow_writeable_chroot=YES: permite ao usuário escrever nesse local.

pasv_enable=YES: habilita o modo passivo.

pasv_min_port=30000: indica o inicio do intervalo de portas destinadas para o modo passivo.

pasv_max_port=31000: indica o fim do intervalo de portas destinadas para o modo passivo.

pasv_address=18.212.252.103: aponta o ip da máquina do servidor.

> **Observação:** O ip colocado no "pasv_address" foi o público para que fosse encontrado por maquinas fora da rede que o servidor se encontra. Por padrão no EC2 esse ip sempre é alterado ao reinciar a instância, logo nesse ambiente de teste devemos nos atentar de alterar esse valor sempre que ele mudar para que tudo funcione normalmente.

#### f) Reinicialização do serviço

```bash
sudo systemctl restart vsftpd
```

### 2.2.4.5 Configuração e testes do Cliente (UbuntuCliente e Máquina local)

#### a) Cliente Ubuntu (ftp)

Foi realizada apenas a atualização da máquina.

```bash
sudo apt update
sudo apt upgrade
sudo apt update
```

Foi realizada a conexão com o servidor com o comando a seguir.

```bash
ftp 18.212.252.103
```

Após a conexão é solicitada o login e senha do usuário, após a validação foi testado a listagem e criação de um diretório com os comandos a seguir.

```bash
ls
mkdir Teste
```

<img width="608" height="213" alt="print4" src="https://github.com/user-attachments/assets/7d556b18-afd6-4e2f-8b5e-5d9603b00baa" />

#### b) Cliente Windows (FileZilla)

Após a instação do software Filezilla é necessário indicar, nos campos destacados na imagem a seguir, o ip do servidor, login e senha do usuário. Com, a conexão estabelecida as pastas e arquivos do diretório serão listados e poderão ser manipulados.

<img width="1163" height="638" alt="print5" src="https://github.com/user-attachments/assets/ad577f5e-b0fc-4b60-8dda-4c6c4e751a43" />


## 2.2.5 Serviço NFS (Network File System)

### 2.2.5.1 Introdução

O **Network File System (NFS)** é um protocolo que possibilita o compartilhamento de arquivos em rede de forma transparente, permitindo que diretórios e arquivos localizados em um servidor sejam acessados por clientes como se estivessem em seus próprios sistemas locais.

No contexto da **Cooperativa de Crédito**, foi configurada uma arquitetura em que a **Matriz** atua como **Servidor NFS (NFS Server)** e as **Filiais** operam como **Clientes NFS (NFS Clients)**.

Com essa configuração, todos os arquivos gerados ou modificados nas Filiais são armazenados centralmente na Matriz, garantindo **padronização, sincronização e transparência de acesso**.

O uso do NFS reduz a duplicação de dados, centraliza o armazenamento e facilita o controle de versões e rotinas de backup corporativo.

---

### 2.2.5.2 Topologia da Arquitetura

**Tipo:** Centralizada  
**Rede VPC:** 172.31.0.0/16  
**Acesso permitido:** 0.0.0.0/0 *(apenas para Proof of Concept - POC/testes)*  

| Função   | Nome da Instância | IPv4 Privado    | Papel        |
|----------|-----------------|----------------|-------------|
| Matriz   | NFS-Server      | 172.31.31.204  | Servidor NFS |
| Filial 1 | NFS-Filial-1    | 172.31.23.111  | Cliente NFS |
| Filial 2 | NFS-Filial-2    | 172.31.28.50   | Cliente NFS |
| Filial 3 | NFS-Filial-3    | 172.31.22.140  | Cliente NFS |
| Filial 4 | NFS-Filial-4    | 172.31.19.147  | Cliente NFS |
| Filial 5 | NFS-Filial-5    | 172.31.25.100  | Cliente NFS |

> **Observação:** Ambiente configurado em instâncias **AWS EC2** com **Ubuntu Server 22.04 LTS (t3.micro)**.

---

### 2.2.5.3 Máquinas Virtuais na Nuvem

Foram criadas seis máquinas virtuais, denominadas como instâncias do tipo EC2 utilizando o serviço de computação em nuvem da AWS (Amazon Web Services), sendo uma como Servidor da Matriz e as demais como Filiais (Clientes).

<img width="1738" height="830" alt="Screen Shot 2025-10-10 at 18 32 17" src="https://github.com/user-attachments/assets/52f47823-b9de-4e52-9a8c-1fff046cafad" />

### 2.2.5.4 Configuração do Servidor NFS (Matriz)

#### a) Instalação do serviço

```bash
sudo apt update
sudo apt install nfs-kernel-server -y
```

#### b) Criação do diretório compartilhado
```bash
sudo mkdir -p /mnt/nfs_share
sudo chown nobody:nogroup /mnt/nfs_share
sudo chmod 777 /mnt/nfs_share
```
O uso de chmod 777 é recomendado apenas em ambiente de teste (POC), permitindo acesso irrestrito às Filiais.

#### c) Configuração do arquivo /etc/exports
```bash
sudo nano /etc/exports
```
Conteúdo adicionado:
```bash
/mnt/nfs_share 172.31.0.0/16(rw,sync,no_subtree_check)
```
Significado das opções:

172.31.0.0/16: faixa de IPs permitida

rw: leitura e escrita habilitadas

sync: grava dados imediatamente no disco

no_subtree_check: melhora desempenho e evita checagens desnecessárias de subdiretórios

#### d) Aplicação das exportações
```bash
sudo exportfs -ra
sudo exportfs -v
```
#### e) Configuração de segurança (AWS Security Groups)
Para efeito de POC, foram liberadas as seguintes portas:

|Protocolo | Porta |	Serviço |
|----------|-------|---------|
|TCP/UDP |	2049 |	NFS |
|TCP/UDP |	111 |	RPCBind |
|TCP |	22 |	SSH |
|ICMP	| - |	Echo Request/Reply |

Em ambiente de produção, recomenda-se restringir o acesso à faixa da VPC e implementar autenticação por host.

---

### 2.2.5.5 Configuração do Cliente NFS (Filial 1)
Por limitação de tempo e escopo do projeto, a configuração foi demonstrada apenas na Filial 1. As demais filiais podem replicar a configuração.

#### a) Instalação do cliente NFS
```bash
sudo apt update
sudo apt install nfs-common -y
```
#### b) Criação dos diretórios locais
```bash
sudo mkdir -p /mnt/nfs_share /mnt/nfs_client
```
#### c) Montagem do compartilhamento
```bash
sudo mount -t nfs 172.31.31.204:/mnt/nfs_share /mnt/nfs_client
```
#### d) Verificação da montagem
```bash
df -h | grep nfs
```
Exemplo de saída:
```bash
172.31.31.204:/mnt/nfs_share  6.8G  2.0G  4.8G  30% /mnt/nfs_client
```
---

### 2.2.5.6 Testes de Leitura e Escrita
#### a) Criação de arquivo na Matriz (Servidor)
```bash
echo -e "Manual de uso do NFS da Cred Vale Doce\n\nDefinições\nInstruções de uso\nBenefícios" | sudo tee /mnt/nfs_share/manual_nfs.txt
```
<img width="621" height="286" alt="Screen Shot 2025-10-10 at 17 53 36" src="https://github.com/user-attachments/assets/d3b0ad87-340d-4990-8807-136ade27a844" />

#### b) Leitura do arquivo na Filial 1 (Cliente)
```bash
sudo mkdir -p /mnt/nfs_share /mnt/nfs_client
sudo mount -t nfs 172.31.31.204:/mnt/nfs_share /mnt/nfs_client
df -h | grep nfs
cat /mnt/nfs_client/manual_nfs.txt
```
<img width="621" height="286" alt="Screen Shot 2025-10-10 at 17 58 50" src="https://github.com/user-attachments/assets/9b6017bb-9c8c-48f8-8b4b-b75a6e174c73" />

#### c) Criação de arquivo a partir da Filial 1
```bash
echo "Teste NFS da FILIAL-01" | sudo tee /mnt/nfs_client/arquivo_teste_filial-1.txt
```
<img width="621" height="286" alt="Screen Shot 2025-10-10 at 18 01 07" src="https://github.com/user-attachments/assets/3d4a03f8-a139-47e7-8f64-ce006d3f59f8" />

#### d) Leitura do mesmo arquivo na Matriz
```bash
cat /mnt/nfs_share/arquivo_teste_filial-1.txt
```
<img width="620" height="289" alt="Screen Shot 2025-10-10 at 18 02 11" src="https://github.com/user-attachments/assets/3356c412-337a-4e9c-8a7e-3098355eff17" />

#### e) Listagem geral dos arquivos compartilhados
```bash
ls /mnt/nfs_share/*.txt
```
<img width="621" height="285" alt="Screen Shot 2025-10-10 at 18 03 02" src="https://github.com/user-attachments/assets/68d0f50b-b529-4f36-9d24-56df9b962284" />

---

### 2.2.5.7 Transparência do Network File System
A transparência do NFS é demonstrada pelo fato de que o diretório remoto montado é acessado pelo cliente como se fosse local.
As operações de leitura, gravação e modificação realizadas nas Filiais ocorrem diretamente no servidor, sem necessidade de sincronizações manuais.

Dessa forma:

- O cliente não precisa saber onde os dados estão fisicamente armazenados

- Todas as Filiais visualizam o mesmo conjunto de arquivos centralizados

- Há consistência e simplicidade na administração do sistema

Assim, o NFS implementa o conceito de sistema de arquivos distribuído, assegurando consistência, integridade e facilidade operacional.
