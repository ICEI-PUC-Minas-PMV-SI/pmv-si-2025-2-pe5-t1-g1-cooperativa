# 3 GERÊNCIA E MONITORAÇÃO DE AMBIENTES DE REDE

# 3.1 Monitoramento em Máquinas Virtuais Locais 

As máquinas virtuais locais foram utilizadas para criar um ambiente controlado, ideal para testes e simulações de rede. Nelas, o Zabbix teve um papel essencial, sendo responsável por monitorar o desempenho e o consumo de recursos de cada máquina. Por meio dessa ferramenta, foi possível observar o funcionamento dos serviços em tempo real, detectar possíveis falhas e manter a estabilidade do sistema. O uso do Zabbix é importante porque garante maior eficiência, confiabilidade e controle sobre os ambientes virtuais, tornando o processo de gerenciamento e análise muito mais preciso.

## 3.1.1 Monitoramento Servidor DHCP (Dynamic Host Configuration Protocol) 

O Zabbix foi utilizado para monitorar o funcionamento do DHCP (Dynamic Host Configuration Protocol), um protocolo que automatiza a atribuição de endereços IP e outras configurações de rede aos dispositivos conectados. Essa automação evita conflitos de endereçamento e facilita o gerenciamento da infraestrutura. No projeto, o Zabbix Appliance foi implementado junto a uma máquina Linux Ubuntu Server configurada como servidor DHCP, possibilitando acompanhar em tempo real o desempenho do serviço e garantir uma distribuição eficiente e estável dos endereços na rede.

## 3.1.2 Monitoramento Servidor AD (Active Directory)

O monitoramento e a gerência de ambientes de rede são componentes fundamentais para garantir o desempenho, a disponibilidade e a segurança de sistemas de rede, por isso foram feitos os testes para o serviço AD (Active Directory) da CREDIVALE DOCE. Esse serviço está localizado em um ambiente virtual local, possibilitando integrar ferramentas de monitoramento, como foi utilizado no caso o Zabbix Appliance, com o serviço de diretório, AD, para obter uma visão centralizada e eficiente da infraestrutura do serviço.
O ambiente é composto por duas máquinas virtuais principais, o Zabbix Appliance, responsável pelo monitoramento e coleta de métricas dos dispositivos, servidores e serviços da rede. Ele é uma solução pronta para uso que já vem com o sistema operacional e o Zabbix Server pré-instalados hospedado no VirtualBox. E o Servidor AD (Active Directory) no Windows Server, responsável pelo gerenciamento de usuários, autenticação, políticas de grupo e demais funções de diretório hospedado no VirtualBox.

### 3.1.2.1 Monitoramento da Infraestrutura

O Zabbix utiliza um agente instalado no host Windows para coletar dados detalhados, como disponibilidade de serviços, utilização de recursos e status de processos do sistema. Alertas e triggers são configurados para notificar administradores em caso de falhas ou degradação de desempenho.
Dessa forma, os itens de monitoramento mais importantes para serem considerados quanto ao AD Server são o uso de memória RAM, o espaço de armazenamento e o consumo de CPU.
No gráfico de utilização de memória é possível perceber que a utilização da mesma não chegou em pontos críticos e se manteve estável, mostrando a estabilidade no serviço. Já no gráfico de utilização de CPU houveram picos e quedas se mantendo mais estável para o final do gráfico, esses picos podem sinalizar uma sobrecarga devido a inicialização do Windows que depois se estabiliza à medida que o tempo passa.

<img width="1167" height="337" alt="Captura de tela 2025-11-08 175439" src="https://github.com/user-attachments/assets/7be53f34-9d07-4c96-a17d-4823336ae255" />
<img width="1181" height="343" alt="Captura de tela 2025-11-08 175428" src="https://github.com/user-attachments/assets/1e6680db-4859-48b0-962b-c47c0ff6d889" />


O gráfico de tráfego de rede mostrou que não houveram perdas de pacotes ou retransmissões anormais o que demonstra que a comunicação está funcionando corretamente, o tráfego está normal para um AD Server e o pico que houve no gráfico pode demonstrar um momento de maior demanda da rede, o que acompanha o uso normal de um server, um pico controlado e uma queda progressiva.

<img width="1151" height="380" alt="Captura de tela 2025-11-08 175355" src="https://github.com/user-attachments/assets/4473d7c1-3d17-47e6-82b9-f2484c62c46c" />


Os gráficos de uso de espaço apesar de demonstrar que o uso está no máximo, foi acrescentado uma memória extra para o melhor funcionamento da aplicação.

<img width="407" height="310" alt="511869112-6fa55489-b51c-4669-840e-a4ad100b22f2" src="https://github.com/user-attachments/assets/fc2e1023-4dd8-4906-bd56-abe0bc1f188b" />

<img width="418" height="305" alt="511869126-d38cfcef-bb2d-4a3b-8e90-b67f00beeaf8" src="https://github.com/user-attachments/assets/4f721579-8cb1-4dc9-85fa-33cdff8e81c4" />

### 3.1.2.1 Considerações Finais
A combinação do Zabbix Appliance com um servidor AD em um ambiente virtual local cria uma solução robusta de monitoramento e administração de rede. Essa arquitetura permite que os administradores mantenham total controle sobre os recursos, sem depender de serviços externos, e ainda aproveitem a flexibilidade de um ambiente virtualizado.
Ao monitorar continuamente o Active Directory e os demais componentes da infraestrutura, a equipe de TI pode agir proativamente, prevenindo falhas, otimizando o desempenho e garantindo a disponibilidade dos serviços essenciais da rede corporativa.


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


## 3.2.4 Monitoramento Serviço WEB

<img width="334" height="281" alt="WebG1" src="https://github.com/user-attachments/assets/60dcf745-ed97-4081-b8d8-885226626672" />

<img width="692" height="282" alt="WebG2" src="https://github.com/user-attachments/assets/76a8924c-5dfb-4e8e-8953-505e11f05f04" />

<img width="692" height="278" alt="WebG3" src="https://github.com/user-attachments/assets/a19e898b-5797-4679-bcc8-dcfa86fea765" />

A Figura XX apresenta o monitoramento do Serviço Web, responsável por hospedar e disponibilizar aplicações corporativas por meio de um servidor dedicado. Esse serviço tem como principal função garantir o acesso estável, rápido e seguro aos sistemas web da organização, sendo essencial para o funcionamento contínuo das aplicações. O monitoramento foi realizado utilizando o Zabbix Agent, com base em três indicadores principais: Disk Space Used, Response Time e Falhas, que permitem acompanhar, respectivamente, o uso de armazenamento, o tempo médio de resposta da aplicação e a ocorrência de erros no serviço.

O primeiro gráfico da Figura XX (Web Server – Disk Space Used) representa o indicador de uso de espaço em disco do servidor web. Observa-se a mensagem “No data”, indicando que não houve consumo significativo de armazenamento durante o período de monitoramento, ou que o valor permaneceu dentro de níveis estáveis e irrelevantes para exibição gráfica. Esse resultado sugere que o servidor apresenta baixa demanda de escrita e armazenamento, o que é comum em ambientes voltados apenas à entrega de páginas e serviços web, onde o processamento é predominantemente de leitura e resposta a requisições.
Mesmo assim, o acompanhamento contínuo desse parâmetro é fundamental, pois o espaço em disco é um recurso crítico: sua saturação pode comprometer o funcionamento do sistema, a gravação de logs e, em casos mais extremos, causar interrupções nos serviços hospedados.

O segundo gráfico (Servidor Web – Response time for step "HomePage" of scenario "CredValeDoce") apresenta o tempo de resposta da aplicação monitorada. Esse parâmetro mede o desempenho da página inicial (“HomePage”) pertencente ao cenário de teste “CredValeDoce”. Os valores observados variam entre 1,3 ms e 2,83 ms, com média de 2,01 ms ao longo do período analisado (entre 18h30 e 19h20). Esses resultados demonstram excelente desempenho e estabilidade, indicando que o servidor está processando as requisições de forma eficiente, sem lentidão ou picos de resposta anormais. A constância da linha verde no gráfico reforça a eficiência e a regularidade do serviço web durante o monitoramento.

Por fim, o terceiro gráfico (Servidor Web – Falhas) mostra o número de erros ou falhas detectadas nas requisições realizadas pelo mesmo cenário de teste. O gráfico mantém-se constantemente na linha zero, indicando que nenhuma falha foi registrada durante o intervalo de observação. Isso evidencia alta disponibilidade e confiabilidade do serviço, sem ocorrências de indisponibilidade, erros HTTP ou falhas de comunicação.

Com base na análise dos três indicadores apresentados na Figura XX, conclui-se que o Serviço Web encontra-se em excelente estado operacional, apresentando:

- Desempenho estável e eficiente, com tempo médio de resposta de aproximadamente 2 ms;

- Ausência total de falhas, demonstrando confiabilidade e disponibilidade do ambiente;

- Necessidade de ajuste na coleta de dados de disco, para garantir o acompanhamento completo dos recursos do servidor.

Em síntese, o ambiente web monitorado mostra-se saudável e com ampla margem de desempenho, sendo recomendado apenas o restabelecimento do monitoramento do espaço em disco para assegurar a observabilidade integral dos recursos críticos do sistema.

##### DNS

### 3.2.5 Monitoramento Serviço DNS  

Nesta etapa foi realizado o monitoramento do "serviço DNS (Domain Name System)" hospedado na instância AWS EC2**, utilizando o Zabbix Agent - para coleta de métricas de desempenho e disponibilidade.  
Como o DNS tem papel essencial na rede, sendo responsável por basicamente traduzir nomes de domínio em endereços IP, logo, os usuários que consultar os serviços sem a necessidade de utilizar e "decorar" endereços numéricos.  

<img width="1716" height="280" alt="image" src="https://github.com/user-attachments/assets/cff34d1a-3be3-46a8-bdb6-5c28d2025a63" />

O gráfico XX "Query Time" expõe o "tempo médio de resposta das consultas DNS" durante o período monitorado. Desse modo, observa-se que os valores permaneceram próximos de 0 ms, com variação mínima, indicando excelente desempenho do servidor.  

Logo, esse resultado evidencia que o serviço DNS está resolvendo os nomes de domínio de forma "rápida e estável", sem atrasos perceptíveis ou falhas de comunicação.  

#### 3.2.6 DNS Server – Network Inbound e Outbound  

Os gráficos de "Network Inbound e Network Outbound" indicam o fluxo de dados recebidos e enviados pela interface de rede da instância DNS. Verifica-se uma atividade de rede constante, e como observado com picos variando entre "5 Kbps e 25 Kbps", o que demonstra que o servidor está sendo acessado regularmente e processando consultas em diferentes momentos. Desse modo, a alternância entre os valores de entrada e saída é esperada e representa o ciclo natural de recebimento de consultas (Inbound) e envio de respostas (Outbound).  

Portanto, o monitoramento do servidor DNS apresentou excelente estabilidade e desempenho, com tempo médio de resposta próximo de zero e tráfego de rede coerente com o volume de consultas. Esses resultados confirmam que o serviço está corretamente configurado, operando dentro dos padrões esperados e garantindo alta disponibilidade para os demais sistemas dependentes da resolução de nomes.  

Dessa forma, o "Zabbix" se mostrou uma ferramenta eficaz para acompanhar a performance do DNS, permitindo detectar possíveis falhas de rede ou lentidão antes que impactem o ambiente. O comportamento observado reforça a confiabilidade da configuração e a eficiência da infraestrutura implementada na AWS.
