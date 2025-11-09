# 3 GERÊNCIA E MONITORAÇÃO DE AMBIENTES DE REDE

# 3.1 Monitoramento em Máquinas Virtuais Locais 

## 3.1.1 Monitoramento Servidor DHCP (Dynamic Host Configuration Protocol) 

## 3.1.2 Monitoramento Servidor AD (Active Directory)

# 3.2 Monitoramento em Máquinas na AWS ( Amazon Web Services ) 

<img width="1716" height="284" alt="511047702-5ba9cdf1-d7de-4ac6-a1db-5060bacdaa7e" src="https://github.com/user-attachments/assets/11d2df1c-2895-4e25-ae6b-6ea5327bcc4d" />

<img width="857" height="283" alt="RAM" src="https://github.com/user-attachments/assets/f836aba9-08d4-4e1f-99dd-f415f5a0a105" />

<img width="863" height="283" alt="CPU" src="https://github.com/user-attachments/assets/d2e0e55a-6d85-4fc0-8ff1-1f7ce685d694" />

Para o ambiente em nuvem da AWS foi criada uma nova instância na EC2 para instalar e hospedar o servidor Zabbix que monitora todas as outras máquinas dos outros serviços. No frontend foi configurado um dashboard para unificar todos os gráficos em um só local, foi definido que os dados relevantes para todos os serviços seriam colocados cada um em um gráfico apenas, sendo eles a disponibilidade do agente, o uso de memória RAM e o uso de CPU.

Na Figura XX é possível ver a disponibilidade do agente em cada máquina, o valor retornado para o monitor Zabbix é do tipo 0 ou 1, sendo 0 o agente não está respondendo e 1 significando que o cliente na máquina monitorada está funcional. Com isso foi configurado para que ao receber o valor 0 faça com que a cor de fundo fique vermelha e com o valor 1 fique verde, fazendo assim que fique intuitivo e de rápida assimilação a informação sobre a disponibilidade do monitoramento.

Para o uso da memória RAM e CPU foi escolhido mostrar os dados em um gráfico de linha em que o uso em porcentagem é representado no eixo y, e o eixo x representa o tempo. Podemos visualizar nas Figuras XX e XX que para todas as máquinas o uso de RAM e CPU foram suficientemente constantes no período monitorado, indicando que a carga sobre as máquinas não estavam sendo preocupantes. Também é possível visualizar no gráfico uma linha superior de gatilho para valores superiores a 90%, com ele é possível configurar alarmes de diversas maneiras para que ao atingir um valor tão alto o responsável tenha conhecimento do ocorrido e possa buscar outros dados para interpretar a fim de diagnosticar o problema e tomar ações para solucioná-lo. 

## 3.2.1 Monitoramento Serviço FTP 

<img width="333" height="277" alt="FTPG1" src="https://github.com/user-attachments/assets/b516fc26-bbe3-4d43-b65c-bbe6f25d10c4" />

<img width="693" height="277" alt="FTPG2" src="https://github.com/user-attachments/assets/bc9dee68-a4eb-4778-96b0-3c9bf7f3e4a3" />

<img width="691" height="278" alt="FTPG3" src="https://github.com/user-attachments/assets/4f35c923-4233-457b-90d5-50f910910b9e" />

Pelo servidor de FTP ser responsável por transferir e armazenar os arquivos foram selecionados o espaço utilizado do disco e o tráfego de rede para serem monitorados por julgar como os dados mais relevantes para o serviço.

No gráfico mostrado pela Figura XX podemos ver que o armazenamento está apenas 38,84% utilizado, esse valor é aceitável pois ainda está longe de atingir o limite do disco. Este gráfico é importante para conseguir identificar rapidamente a necessidade de rever políticas de armazenamento, ou mais comumente, a necessidade de expansão na capacidade do disco da máquina.

Já na Figura XX podemos visualizar o tráfego de rede de entrada e na Figura XX o tráfego de saída da máquina, eles indicam principalmente quando estão acontecendo transferências de arquivos, por meio desses dados pode-se tirar informações como horário em que a máquina é mais utilizada, valor que ela necessidade de banda para funcionar sem ter problemas, até também momentos de anormalidades que podem ser referentes a mau uso, ou algum ataque, por exemplo. No gráfico de entrada, Figura XX, o único pico, que chega a um uso de 8 Mpbs, representa um momento em que foi enviado um arquivo maior para a máquina que está hospedando o serviço, já no gráfico de saída, Figura XX, os picos apresentados podem significar os momentos em que arquivos foram transferidos para uma ou mais máquinas clientes.

## 3.2.2 Monitoramento Serviço NFS

<img width="328" height="274" alt="NFSG1" src="https://github.com/user-attachments/assets/e93e71f3-a7ce-46a4-9a71-685505e1a9f6" />

<img width="687" height="275" alt="NFSG2" src="https://github.com/user-attachments/assets/23cc4b60-1c4e-4c20-a7c3-852527eb369b" />

<img width="688" height="276" alt="NFSG3" src="https://github.com/user-attachments/assets/9fd3dfee-748e-4a9e-a805-662b0a00ec46" />

Os gráficos apresentados nas Figuras XX, XX e XX referem-se ao monitoramento do serviço NFS (Network File System) configurado na instância do EC2 da AWS, responsável por prover o compartilhamento de arquivos entre os ambientes da matriz e da nuvem. O monitoramento foi realizado por meio do Zabbix Agent, com base nos indicadores Disk Space Used, Disk Read Rate (r/s) e Disk Write Rate (w/s), que permitem avaliar respectivamente a ocupação do volume, as operações de leitura e as operações de escrita por segundo no disco utilizado pelo NFS.

No gráfico da Figura XX (NFS-Matriz – Disk Space Used), o percentual de utilização do volume em disco encontra-se em 38,86%, valor considerado dentro dos limites seguros de operação. Essa taxa indica que o ambiente ainda dispõe de ampla capacidade livre para armazenamento e expansão, sem risco imediato de esgotamento do espaço disponível. O indicador demonstra estabilidade e ausência de crescimento abrupto no consumo de espaço, evidenciando o uso controlado e consistente do armazenamento associado ao serviço NFS.

Na sequência, o gráfico da Figura XX (NFS-Matriz – Disk Read Rate) apresenta a taxa média de leitura durante o período de monitoramento em torno de 0,2 r/s, com picos de 5 r/s registrados durante períodos de maior demanda. As variações observadas refletem o acesso de múltiplos clientes à estrutura de diretórios compartilhados, mantendo-se, contudo, dentro dos parâmetros operacionais esperados. Não foram identificadas interrupções nem períodos prolongados de inatividade, indicando estabilidade nas operações de leitura.

Por fim, o gráfico da Figura XX (NFS-Matriz – Disk Write Rate) demonstra comportamento semelhante, com média de 0,3 w/s e picos de 2,5 w/s correspondentes a momentos de escrita simultânea. O padrão de oscilação é característico do NFS em ambiente multiusuário, refletindo operações regulares de atualização de arquivos. O desempenho de escrita manteve-se estável durante todo o monitoramento.

Em síntese, o serviço NFS operando em uma instância AWS apresenta desempenho estável, com utilização de disco de 38,86% e taxas de leitura e escrita coerentes com a carga de trabalho aplicada. Não foram observados gargalos, saturações ou anomalias de uso, confirmando a eficiência e a confiabilidade do serviço no ambiente de nuvem.

## 3.2.3 Monitoramento Serviço PostgreSQL

<img width="329" height="274" alt="PSQLG1" src="https://github.com/user-attachments/assets/8431fbea-50ea-4345-803a-2939125bd10a" />

<img width="688" height="277" alt="PSQLG2" src="https://github.com/user-attachments/assets/f4c550ac-af6f-4a38-9e3c-43ad1674edc1" />

<img width="689" height="275" alt="PSQLG3" src="https://github.com/user-attachments/assets/c07a7200-249c-49f8-b6d5-5702f93cae8c" />

Os gráficos apresentados nas Figuras XX, XX e XX referem-se ao monitoramento do serviço PostgreSQL, que é um gerenciador de banco de dados relacional com o foco na segurança e escalabilidade para a empresa. Foi configurado utilizando uma instância do EC2 da AWS, é um sistema responsável por armazenar os dados da matriz em nuvem. O monitoramento foi realizado por meio do Zabbix Agent, com base nos indicadores Disk Space Used, Disk Utilization e Disk Network (Kbps), que permitem avaliar respectivamente a ocupação do volume, a utilização do espaço de armazenamento pelo PostgreSQL e a quantidade de dados trafegados durante um periodo de tempo.

No gráfico da Figura XX (Postgres-Matriz – Disk Space Used), mostra a proporção do espaço total em disco que está atualmente sendo utilizado pelo servidor. O valor destacado é de 46,30%. O espaço em disco é um recurso crítico para qualquer servidor de banco de dados. Se o disco encher, o PostgreSQL pode parar de funcionar, resultando em indisponibilidade do serviço, falhas em transações e possivelmente corrupção de dados. Um uso de 46,30% indica que pouco menos da metade da capacidade total do disco está sendo utilizada. Isso é geralmente considerado uma situação saudável e segura, pois há espaço suficiente disponível para crescimento futuro, operações de manutenção (como backups, vacuums, etc.) e picos não planejados no uso.

Na sequência, o gráfico da Figura XX (Postgres-Matriz – Disk Utilization) é um gráfico que demostra mostra a taxa de utilização do disco (I/O – operações de leitura e escrita) ao longo do tempo. Os valores são muito baixos, variando entre 0.01% e 0.08%. A utilização do disco (I/O) mede o quão ativo e sobrecarregado o subsistema de armazenamento está. Mesmo com espaço livre, um disco com I/O muito alto (100% de utilização) pode se tornar um gargalo, tornando o sistema lento, pois as operações ficam na fila aguardando para serem lidas ou escritas. Os valores extremamente baixos (menos de 0,1%) indicam que o servidor não está sob pressão de I/O. O disco está respondendo rapidamente às solicitações, sem formar filas. Isso é ideal para o desempenho do banco de dados, especialmente para o PostgreSQL, que é intensivo em operações de disco.

Por fim, o gráfico da Figura XX (NFS-Matriz – Disk Network) que monitora o tráfego de rede do servidor, especificamente a taxa de transferência de dados nas interfaces de rede ens6 (dados recebidos) e ens5 (dados enviados). A unidade de medida é Kbps (Kilobits por segundo), e o pico mostrado é de aproximadamente 8 Kbps. A rede é o canal de comunicação do servidor de banco de dados com suas aplicações clientes e outros serviços. É crucial monitorar para identificar gargalos de comunicação, picos de tráfego anormais (que podem indicar um ataque ou problema na aplicação) ou para planejamento de capacidade. Um tráfego na casa de poucos Kbps é considerado muito baixo. Isso sugere que, no momento do monitoramento, o servidor estava lidando com uma carga de trabalho leve ou praticamente ociosa em termos de comunicação de rede. Não há congestionamento ou gargalo de rede. Para um servidor de banco de dados em produção sob carga normal, esperariam-se valores significativamente mais altos (Mbps ou até Gbps).

Com base nos dados monitorados, o servidor Postgres-Matriz está em um estado extremamente saudável e sem pressão em todos os recursos críticos analisados:

- Disco: Tem espaço mais que suficiente (46,30% usado) e não sofre com lentidão de I/O (utilização abaixo de 0,1%).
- Rede: O tráfego é mínimo, indicando que não há uma carga pesada de consultas ou transferência de dados no momento.

Esta é uma situação ideal, indicando que há uma grande margem para crescimento na carga de trabalho sem que o servidor enfrente problemas de desempenho imediatos. A monitorização contínua é essencial para detectar quando esses números começarem a aumentar para níveis que exijam atenção.


##### WEB
<img width="1719" height="282" alt="image" src="https://github.com/user-attachments/assets/610795aa-5b3f-45f9-9d9b-d1b4d7c816b1" />

##### DNS
<img width="1716" height="280" alt="image" src="https://github.com/user-attachments/assets/cff34d1a-3be3-46a8-bdb6-5c28d2025a63" />

> Será atualizada
