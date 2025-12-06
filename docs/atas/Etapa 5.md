# Cronograma de Atividades – 5ª Etapa

| Equipe | Carga Horária | Ações/Atividades | Data |
|--------|---------------|-----------------|------|
| Carlos Alberto Vieira de Souza; Laura de Freitas Mendes Losque; Luana Horta de Souza; Lucas Araújo Pacheco; Odair Cordeiro Marra; Victor Samuel Costa Pereira; Yan Oyama Moura. | 1:30 h | Divisão das tarefas da 5ª etapa. | 01/12 |
| Carlos Alberto Vieira de Souza; Laura de Freitas Mendes Losque; Luana Horta de Souza; Lucas Araújo Pacheco; Odair Cordeiro Marra; Victor Samuel Costa Pereira; Yan Oyama Moura. | 1:40 h | Discussão sobre o roteiro e organização da lógica dos slides. | 02/12 |
| Carlos Alberto Vieira de Souza; Laura de Freitas Mendes Losque; Luana Horta de Souza; Lucas Araújo Pacheco; Odair Cordeiro Marra; Victor Samuel Costa Pereira; Yan Oyama Moura. | 2:30 h | Ensaio e cronometragem do tempo individual da apresentação, alterações no roteiro e revisão dos slides. | 03/12 |
| Carlos Alberto Vieira de Souza; Laura de Freitas Mendes Losque; Luana Horta de Souza; Lucas Araújo Pacheco; Odair Cordeiro Marra; Victor Samuel Costa Pereira; Yan Oyama Moura. | 2:45 h | Ensaio final e cronometragem do tempo geral com todos da apresentação e revisão final dos slides. | 04/12 |


# Atividades Individuais – Resumo Geral do trabalho

- **Carlos** → Na primeira etapa participei da realização do protótipo no packet trace, no preenchimento inicial das planilhas de equipamento, no preenchimento da planilha de ip e cálculo de links. Na segunda etapa configurei o ftp na AWS e ajudei a Luana pontualmente no AD. Na terceira etapa fiquei responsável pela máquina monitora do zabbix, por conectar ela com as outras instâncias da AWS e ajustar o dashboard de monitoramento. Na quarta etapa participei no início de alguns textos e participei no de vulnerabilidades. Na quinta etapa participei na elaboração do roteiro e pontualmente em ajustes dos slides que apresentei, e fiquei com a apresentação das instalações e monitoramento. A partir da etapa dois fiquei responsável por transferir o que era produzido de documentação pelo grupo para o formato de artigo utilizando LaTeX, inicialmente pela plataforma Overleaf e depois utilizando a ferramenta TexStudio e MiKTeX.

- **Luana** → 

- **Odair** → 
Na primeira etapa, participei das discussões iniciais de planejamento, contribuindo para a definição da persona, da história, da missão, visão e valores da Cred Vale Doce, bem como de sua estrutura organizacional. Colaborei na especificação dos requisitos de negócio e das restrições do projeto, no desenho do organograma e no preenchimento e validação da planilha de ativos da infraestrutura. Também atuei no desenvolvimento da simulação da rede no Cisco Packet Tracer e auxiliei na descrição dessa fase na documentação final.

Na segunda etapa, participei do planejamento geral da fase e de todas as reuniões de alinhamento e validação. Como atividade técnica principal, configurei integralmente o serviço NFS (Network File System) na AWS. Isso incluiu a criação e configuração do servidor NFS, com a exportação dos diretórios compartilhados e a definição das políticas de segurança no security group. Paralelamente, configurei as instâncias cliente, realizando o mapeamento dos diretórios remotos e executando testes de acesso. Documentei todo o processo e validei o funcionamento do serviço por meio de testes práticos de leitura e escrita entre as instâncias, garantindo a transparência e a consistência do compartilhamento de arquivos.

Na terceira etapa, participei do planejamento das atividades de monitoramento e fiquei responsável pela configuração inicial do Zabbix em um servidor local. Meu objetivo foi monitorar especificamente o serviço NFS configurado anteriormente. Instalei e configurei o agente Zabbix, integrando-o ao servidor de monitoramento central configurado por outro membro da equipe. Documentei os resultados obtidos, criando dashboards e gráficos para acompanhar métricas como utilização de disco e tráfego de rede do NFS.

Na quarta etapa, participei do planejamento das ações de segurança e contribuí diretamente para a elaboração da Política de Segurança da Informação (PSI) da Cred Vale Doce. Também formulei sugestões e conteúdos para a Cartilha de Acesso Seguro, material destinado à conscientização de colaboradores e cooperados.

Por fim, na quinta etapa, participei da elaboração do roteiro e dos slides da apresentação final e fiquei responsável por apresentar a seção de Conclusões durante o seminário, sintetizando os objetivos alcançados, os aprendizados e o valor entregue pelo projeto.

- **Lucas** → Na primeira etapa, participei das discussões de estruturação da solução, contribuindo para a definição do esquema de endereçamento IP e para o levantamento dos equipamentos necessários tanto para a Matriz quanto para as Filiais. Também auxiliei na elaboração da tabela de cálculo de links, consolidando informações essenciais para dimensionamento e planejamento da rede.

Na segunda etapa, fui responsável pela configuração do servidor web em uma instância EC2 na AWS. Após realizar os ajustes necessários no ambiente, efetuei testes de validação por meio da criação de um arquivo HTML dedicado, garantindo o correto funcionamento do serviço e a disponibilidade do ambiente web.

Na terceira etapa, realizei a configuração da máquina virtual do Serviço Web para integração com o servidor Zabbix, responsável pelo monitoramento centralizado da infraestrutura. Para validar o funcionamento, desenvolvi um ambiente de testes local, onde verifiquei parâmetros de coleta e comunicação. Em seguida, finalizei a integração com o servidor principal, permitindo o acompanhamento contínuo de métricas como tempo de resposta, utilização de disco e estabilidade do serviço.

Na quarta etapa, desenvolvi a modelagem do banco de dados e implementei o CRUD de forma completa, tanto no front-end quanto no back-end, garantindo a consistência das operações e a comunicação adequada entre as camadas da aplicação.

Por fim, nesta etapa final, contribuí para a elaboração do roteiro e dos slides da apresentação e assumi a responsabilidade pela demonstração da aplicação CRUD durante a apresentação, destacando as funcionalidades implementadas e os resultados obtidos ao longo do projeto.

- **Yan** →

- **Victor** →  Na primeira etapa, participei das discussões de estruturação da solução, contribui para a definição do esquema de endereçamento IP e o levantamento dos equipamentos necessários tanto para a Matriz quanto para as Filiais.

Na segunda etapa, fui responsável pela configuração do bqnco de dados PostgreSQL em uma instância EC2 na AWS. E com a configuração do banco realizada, fiz os ajustes necessários no ambiente para que o banco de dados pudesse ser acessado por outras maquinas que fossem autorizadas e pudessem trocar dados com as mesmas. No final, validei o banco de dados ao inserir dados e os mesmos foram acessados por um outro computador que estava com permissão de acesso ao banco de dados.

Na terceira etapa, realizei a configurações na máquina virtual do banco de dados para integração com o servidor Zabbix, responsável pelo monitoramento centralizado da infraestrutura. Para validar o funcionamento, realizei a configuração dos parâmetros nescessarios para a comunicação e formceci acesso de nivel admim ao servidor zabbix para com o banco de dados, onde o mesmo conseguiria coletar todos os dados referentes ap funcionamento do banco de dados 

Na quarta etapa, auxiliei o Lucas com a modelagem do banco de dados e implementação do CRUD de forma completa, tanto no front-end quanto no back-end.

Por fim, nesta etapa final, contribuí para a elaboração do roteiro e dos slides da apresentação e assumi a responsabilidade pela apresrntação do grupo e introdução ao desenvolvimento durante a apresentação.

  
- **Laura** → Na primeira etapa, participei das reuniões iniciais de definição estrutural da cooperativa, mas minha principal entrega foi a criação completa da logo, junto com a paleta de cores e a fonte oficial, consolidando a identidade visual. Também apoiei na reunião de requisitos, restrições, organograma e definição geográfica.

Na segunda etapa, fui responsável pela configuração completa do servidor e do cliente DHCP, garantindo o funcionamento correto do serviço na rede. Além disso, elaborei toda a documentação técnica referente ao processo, detalhando configurações, procedimentos e validações realizadas.

Na terceira etapa, realizei o monitoramento do serviço DHCP por meio do Zabbix, acompanhando desempenho e disponibilidade. Também implementei o Zabbix Agent em uma máquina Linux Ubuntu Server configurada como servidor DHCP, garantindo a coleta adequada de métricas e a supervisão contínua do ambiente.

Na quarta etapa, fiquei principalmente responsável pelo design da Cartilha de Segurança, montando toda a parte visual, organização e estilo do material. Também dei apoio na criação e revisão dos textos.

Por fim, na quinta etapa, participei da elaboração do roteiro e dos slides da apresentação final, ficando responsável pelo design dos slides e pela apresentação das Análises de Vulnerabilidades.
