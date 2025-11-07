# 3 GERêNCIA E MONITORAÇÃO DE AMBIENTES DE REDE

# 3.1 Monitoramento em Máquinas Virtuais Locais 

## 3.1.1 Monitoramento Servidor DHCP (Dynamic Host Configuration Protocol) 


## 3.1.2 Monitoramento Servidor AD (Active Directory) 


#### Imagens 

##### Geral
<img width="1920" height="2475" alt="image" src="https://github.com/user-attachments/assets/1fcb8411-c39f-4e0a-9810-474cc31cd347" />
> Será atualizada

##### Status de todas as máquinas 
<img width="1716" height="284" alt="image" src="https://github.com/user-attachments/assets/5ba9cdf1-d7de-4ac6-a1db-5060bacdaa7e" />
> Será atualizada

##### Monitoramento de RAM e CPU Geral
<img width="1722" height="283" alt="image" src="https://github.com/user-attachments/assets/cc2fb645-b395-44ca-b177-df389684ad56" />

##### FTP
<img width="1723" height="280" alt="image" src="https://github.com/user-attachments/assets/a2171516-2622-477f-b080-678113a18441" />

##### NFS 
<img width="1719" height="282" alt="image" src="https://github.com/user-attachments/assets/918433f7-7e3f-40aa-86c0-06100a7afe4f" />

## 3.2.X Monitoramento Serviço NFS

Os gráficos apresentados nas Figuras XX, XX e XX referem-se ao monitoramento do serviço NFS (Network File System) configurado na instância do EC2 da AWS, responsável por prover o compartilhamento de arquivos entre os ambientes da matriz e da nuvem. O monitoramento foi realizado por meio do Zabbix Agent, com base nos indicadores Disk Space Used, Disk Read Rate (r/s) e Disk Write Rate (w/s), que permitem avaliar respectivamente a ocupação do volume, as operações de leitura e as operações de escrita por segundo no disco utilizado pelo NFS.

No gráfico da Figura XX (NFS-Matriz – Disk Space Used), o percentual de utilização do volume em disco encontra-se em 38,86%, valor considerado dentro dos limites seguros de operação. Essa taxa indica que o ambiente ainda dispõe de ampla capacidade livre para armazenamento e expansão, sem risco imediato de esgotamento do espaço disponível. O indicador demonstra estabilidade e ausência de crescimento abrupto no consumo de espaço, evidenciando o uso controlado e consistente do armazenamento associado ao serviço NFS.

Na sequência, o gráfico da Figura XX (NFS-Matriz – Disk Read Rate) apresenta a taxa média de leitura durante o período de monitoramento em torno de 0,2 r/s, com picos de 5 r/s registrados durante períodos de maior demanda. As variações observadas refletem o acesso de múltiplos clientes à estrutura de diretórios compartilhados, mantendo-se, contudo, dentro dos parâmetros operacionais esperados. Não foram identificadas interrupções nem períodos prolongados de inatividade, indicando estabilidade nas operações de leitura.

Por fim, o gráfico da Figura XX (NFS-Matriz – Disk Write Rate) demonstra comportamento semelhante, com média de 0,3 w/s e picos de 2,5 w/s correspondentes a momentos de escrita simultânea. O padrão de oscilação é característico do NFS em ambiente multiusuário, refletindo operações regulares de atualização de arquivos. O desempenho de escrita manteve-se estável durante todo o monitoramento.

Em síntese, o serviço NFS operando em uma instância AWS apresenta desempenho estável, com utilização de disco de 38,86% e taxas de leitura e escrita coerentes com a carga de trabalho aplicada. Não foram observados gargalos, saturações ou anomalias de uso, confirmando a eficiência e a confiabilidade do serviço no ambiente de nuvem.

##### Banco
<img width="1720" height="281" alt="image" src="https://github.com/user-attachments/assets/c0fc5998-2d97-40f6-93ad-ab110f45b570" />
> Será atualizada

##### WEB
<img width="1719" height="282" alt="image" src="https://github.com/user-attachments/assets/610795aa-5b3f-45f9-9d9b-d1b4d7c816b1" />

##### DNS
<img width="1718" height="279" alt="image" src="https://github.com/user-attachments/assets/4e856d10-1529-4cf4-a196-b5e50964aae1" />
> Será atualizada
