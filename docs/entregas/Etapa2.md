# 2 PREPARAÇÃO DO AMBIENTE EM NUVEM E VIRTUALIZAÇÃO LOCAL


# 2.1 Serviços em Máquinas Virtuais Locais pelo VirtualBox




# 2.2 Serviços em Máquinas Virtuais na Nuvem pela AWS




## 2.X.X Servidor DHCP (Dynamic Host Configuration Protocol)



## 2.X.X Servidor WEB



## 2.X.X Serviço DNS (Domain Name System)



## 2.X.X Serviço de Banco de Dados (PostgreSQL)



## 2.X.X Serviço de AD (Active Directory)



## 2.2.4 Serviço FTP (File Transfer Protocol)



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
