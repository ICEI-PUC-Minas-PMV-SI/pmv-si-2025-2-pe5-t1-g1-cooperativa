# Cronograma de Atividades – 3ª Etapa

| Equipe | Carga Horária | Ações/Atividades | Data |
|--------|---------------|-----------------|------|
| Carlos Alberto Vieira de Souza; Laura de Freitas Mendes Losque; Luana Horta de Souza; Lucas Araújo Pacheco; Odair Cordeiro Marra; Victor Samuel Costa Pereira; Yan Oyama Moura. | 0:30 h | Divisão das atividades. | 27/10 |
| Carlos Alberto Vieira de Souza; Laura de Freitas Mendes Losque; Luana Horta de Souza; Lucas Araújo Pacheco; Odair Cordeiro Marra; Victor Samuel Costa Pereira; Yan Oyama Moura. | 2:00 h | Conexões e soluções de problemas. | 30/10 |
| Carlos Alberto Vieira de Souza; Laura de Freitas Mendes Losque; Luana Horta de Souza; Lucas Araújo Pacheco; Odair Cordeiro Marra; Victor Samuel Costa Pereira; Yan Oyama Moura. | 2:30 h | Unificação dos serviços no Zabbix das máquinas na nuvem. | 02/11 |
| Carlos Alberto Vieira de Souza; Laura de Freitas Mendes Losque; Luana Horta de Souza; Lucas Araújo Pacheco; Odair Cordeiro Marra; Victor Samuel Costa Pereira; Yan Oyama Moura. | 0:15 h | Alinhamento de atividades e programação de entregas da documentação. | 03/11 |
| Carlos Alberto Vieira de Souza; Laura de Freitas Mendes Losque; Luana Horta de Souza; Lucas Araújo Pacheco; Odair Cordeiro Marra; Victor Samuel Costa Pereira; Yan Oyama Moura. | 2:40 h | Reunião de discussão de dificuldades e rascunho inicial da documentação da etapa. | 06/11 |

# Atividades Individuais – 3ª Etapa

- **Carlos** → criei a máquina para o zabbix server na aws e configurei o zabbix agent na máquina ftp, após reuniões com o grupo decidimos que faríamos a unificação do monitoramento na máquina server no meu laboratório, portanto fiz a configuração dos hosts no frontend do zabbix e montei o dashboard seguindo o que foi conversado e decidido em reunião, no final apenas passei o texto e as imagens do .md no github para o artigo, por enquanto pelo overleaf.

- **Luana** → Nessa etapa, fiquei responsável pelos servers locais do projeto. Fiz a instalação do Zabbix Appliance e o monitoramento do Server o AD e ajudei no DHCP juntando-o também a minha máquina.

- **Odair** 

Nessa terceira etapa do projeto, voltada à implementação da gerência e monitoração do ambiente de redes, participei do planejamento das atividades e fiquei responsável pela configuração inicial da ferramenta Zabbix em um servidor local, com o objetivo de monitorar o serviço NFS (Network File System).

Durante o planejamento, colaborei na definição da proposta de template do dashboard de monitoramento, discutindo com o grupo quais indicadores seriam mais relevantes para acompanhamento no servidor central — como utilização de CPU, memória, espaço em disco e disponibilidade do serviço NFS. Definimos que o servidor central de monitoramento seria alocado na máquina do Carlos, onde seriam concentradas as coletas e visualizações gráficas. 

Após a verificação de que o monitoramento local estava operacional, iniciamos a integração com os serviços hospedados na AWS. Nessa fase, realizei os ajustes de configuração no diretório `/etc/zabbix/zabbix_agentd.conf` da instância NFS-Matriz, inserindo o IP público do Servidor Geral (máquina do Carlos) para estabelecer a comunicação entre o agente Zabbix e o servidor de monitoramento. Também forneci o endereço IP público da instância NFS-Matriz ao Carlos, garantindo que o servidor geral conseguisse identificar e monitorar adequadamente o serviço remoto. 

Em seguida, realizamos testes de leitura e escrita de arquivos entre as máquinas, Matriz e Filiais, validando a comunicação e confirmando o correto funcionamento do monitoramento. Por fim, fiquei encarregado de documentar o processo de configuração e monitoração do serviço NFS, incluindo descrever os resultados obtidos nos gráficos gerados pelo Zabbix após a execução dos testes de desempenho e disponibilidade.

- **Lucas** → Nesta etapa, foi configurada a máquina virtual do Serviço Web para estabelecer comunicação com o servidor Zabbix, responsável pelo monitoramento centralizado do ambiente. Foi criado um ambiente de teste local para validar os parâmetros de coleta e, em seguida, a máquina foi integrada ao servidor principal, permitindo o acompanhamento de métricas como tempo de resposta, uso de disco e estabilidade do serviço.

- **Yan** → Nesta etapa, foi configurado um servidor DNS em uma instância EC2 na AWS e integrado ao Zabbix para monitoramento. O objetivo foi acompanhar o desempenho da resolução de nomes e a comunicação de rede da instância.

O gráfico obtido mostra três métricas principais: Query Time, Network Inbound e Network Outbound. O tempo de consulta (Query Time) manteve-se baixo, indicando respostas rápidas do servidor. Já os gráficos de entrada e saída de rede mostraram variações esperadas, representando o tráfego de consultas e respostas DNS.

Com isso, foi possível verificar que o servidor DNS apresentou bom desempenho e estabilidade, respondendo adequadamente às solicitações e garantindo a conectividade e disponibilidade do serviço hospedado na AWS.

- **Victor** →  Nesta etapa, configurei a maquina virtual Postgres para que pudesse haver a comunicação com a maquina virtual Zabbix que estava realizando o processo de monitoramento de todas as maquinas virtuais da sede matrix. Para realizar um teste inicial, criei uma maquina local utilizando o Zabbix e preparei para que posteriomente pudesse ser implementado ao servidor Zabbix final. Auxiliei o Carlos com a configuração do servidor Zabbix com relação a configuração do Zabbix para realizar o monitoramento do banco de dados e documentei o processo de monitoamento do serviço postgeSQL, incluindo a descrição de todos os graicos que foram gerados pelo Zabbix após os testes de desempenho e processamento no banco de dados.
  
- **Laura** → Nesta etapa, 
