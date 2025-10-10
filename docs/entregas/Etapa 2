














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

| Função | Nome da Instância | IPv4 Privado | Papel |
|:--|:--|:--|:--|
| Matriz | NFS-Server | 172.31.31.204 | Servidor NFS |
| Filial 1 | NFS-Filial-1 | 172.31.23.111 | Cliente NFS |
| Filial 2 | NFS-Filial-2 | 172.31.28.50 | Cliente NFS |
| Filial 3 | NFS-Filial-3 | 172.31.22.140 | Cliente NFS |
| Filial 4 | NFS-Filial-4 | 172.31.19.147 | Cliente NFS |
| Filial 5 | NFS-Filial-5 | 172.31.25.100 | Cliente NFS |

> **Observação:** Ambiente configurado em instâncias **AWS EC2** com **Ubuntu Server 22.04 LTS (t3.micro)**.

---

### 2.2.5.3 Configuração do Servidor NFS (Matriz)

#### a) Instalação do serviço
```bash
sudo apt update
sudo apt install nfs-kernel-server -y
b) Criação do diretório compartilhado
bash
Copy code
sudo mkdir -p /mnt/nfs_share
sudo chown nobody:nogroup /mnt/nfs_share
sudo chmod 777 /mnt/nfs_share
O uso de chmod 777 é justificado apenas para o ambiente de testes (POC), permitindo acesso irrestrito às Filiais.

c) Configuração do arquivo /etc/exports
bash
Copy code
sudo nano /etc/exports
Conteúdo adicionado:

bash
Copy code
/mnt/nfs_share 172.31.0.0/16(rw,sync,no_subtree_check)
Significado das opções:

172.31.0.0/16: faixa de IPs permitida;

rw: leitura e escrita habilitadas;

sync: grava dados imediatamente no disco (maior segurança);

no_subtree_check: melhora o desempenho e evita verificações desnecessárias de subdiretórios.

d) Aplicação das exportações
bash
Copy code
sudo exportfs -ra
sudo exportfs -v
e) Configuração de segurança (AWS Security Groups)
Para efeito de POC, foram liberadas as seguintes portas:

Protocolo	Porta	Serviço
TCP/UDP	2049	NFS
TCP/UDP	111	RPCBind
TCP	22	SSH
ICMP	-	Echo Request/Reply (teste de conectividade)

Em ambiente de produção, recomenda-se restringir o acesso à faixa da VPC e implementar autenticação por host.

2.2.5.4 Configuração do Cliente NFS (Filial 1)
Por limitação de tempo e escopo do projeto, a configuração foi demonstrada apenas na Filial 1, sendo as demais filiais replicáveis de forma idêntica.

a) Instalação do cliente NFS
bash
Copy code
sudo apt update
sudo apt install nfs-common -y
b) Criação dos diretórios locais
bash
Copy code
sudo mkdir -p /mnt/nfs_share /mnt/nfs_client
c) Montagem do compartilhamento
bash
Copy code
sudo mount -t nfs 172.31.31.204:/mnt/nfs_share /mnt/nfs_client
d) Verificação da montagem
bash
Copy code
df -h | grep nfs
Exemplo de saída:

ruby
Copy code
172.31.31.204:/mnt/nfs_share  6.8G  2.0G  4.8G  30% /mnt/nfs_client
2.2.5.5 Testes de Leitura e Escrita
a) Criação de arquivo na Matriz (Servidor)
bash
Copy code
echo -e "Manual de uso do NFS da Cred Vale Doce\n\nDefinições\nInstruções de uso\nBenefícios" | sudo tee /mnt/nfs_share/manual_nfs.txt
[Evidência: captura de tela do terminal da Matriz com a criação do arquivo.]

b) Leitura do arquivo na Filial 1 (Cliente)
bash
Copy code
cat /mnt/nfs_client/manual_nfs.txt
[Evidência: saída exibindo o conteúdo idêntico ao arquivo da Matriz.]

c) Criação de arquivo a partir da Filial 1
bash
Copy code
echo "Teste NFS da FILIAL-01" | sudo tee /mnt/nfs_client/arquivo_teste_filial-1.txt
[Evidência: o conteúdo criado na Filial.]

d) Leitura do mesmo arquivo na Matriz
bash
Copy code
cat /mnt/nfs_share/arquivo_teste_filial-1.txt
[Evidência: o conteúdo criado na Filial aparece instantaneamente na Matriz.]

e) Listagem geral dos arquivos compartilhados
bash
Copy code
ls /mnt/nfs_share/*.txt
[Evidência: Listagem de todos os arquivos na Matriz.]

2.2.5.6 Transparência do Network File System
A transparência do NFS é demonstrada pelo fato de que o diretório remoto montado é acessado pelo cliente como se fosse local.
As operações de leitura, gravação e modificação realizadas nas filiais ocorrem diretamente no servidor, sem necessidade de sincronizações manuais.

Dessa forma:
O cliente não precisa saber onde os dados estão fisicamente armazenados;
Todas as filiais visualizam o mesmo conjunto de arquivos centralizados;
Há consistência e simplicidade na administração do sistema.

Assim, o NFS implementa o conceito de sistema de arquivos distribuído, assegurando consistência, integridade e facilidade operacional.
