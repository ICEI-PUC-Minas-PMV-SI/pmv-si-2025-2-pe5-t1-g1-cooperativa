# PROJETO EIXO 5 - DISCIPLINA DE PROJETO  
### Sistemas de Informação – EAD  

---

## CRED VALE DOCE  
**Cooperativa bancária em uma cidade polo do interior do estado com cinco filiais em cidades próximas**

---

## 1. Introdução

No mundo contemporâneo, a integração e a eficiência dos processos organizacionais das instituições dependem amplamente da infraestrutura de rede que foi adotada pelas mesmas. Cooperativas de crédito não são uma exceção à regra, já que possuem características próprias de gestão e foco na coletividade.  

No caso de uma cooperativa de crédito que possui uma matriz e cinco filiais, como neste projeto, essa lógica se torna ainda mais forte, porque a conectividade é um fator determinante para assegurar que haverá fluidez na comunicação, confiabilidade dos dados e continuidade das operações.  

Fazer a escolha de uma estrutura de rede adequada se faz necessária para uma integração eficiente entre os diferentes pontos de atendimento e a administração, permitindo que haja um compartilhamento seguro e ágil de informações, tanto para gestão quanto para o atendimento aos cooperados.  

Uma rede que não atenda às necessidades ou que seja mal estruturada pode causar problemas como falhas na comunicação, vulnerabilidade de segurança e lentidão no acesso, o que compromete tanto a qualidade dos serviços prestados quanto a confiança que os cooperados têm na empresa — afetando também a tomada de decisão dos gestores.  

A adoção de serviços alinhados aos parâmetros de segurança, funcionamento, administração e atendimento da empresa leva à otimização dos processos internos e à redução dos custos operacionais, permitindo investimentos mais estratégicos e tornando a cooperativa mais competitiva no mercado, o que possibilita sua expansão e o aumento na oferta de serviços e crédito para os cooperados.  

Diante desse cenário, a cooperativa de crédito exige um planejamento que envolva uma topologia adequada, aliada a estratégias para sua segurança e escalabilidade. Este projeto tem como objetivo analisar e propor soluções de rede que aliem a viabilidade técnica e econômica às necessidades de integração e suporte para as atividades estratégicas, operacionais e administrativas da cooperativa.  

---

## 2. Tema para Desenvolvimento do Projeto

**Rede Estruturada para uma Cooperativa Bancária em uma cidade polo do interior do estado com cinco filiais em cidades próximas.**

---

### 2.1 Descrição da Persona Jurídica

#### 2.1.1 Nome da Cooperativa  
Cred Vale Doce

#### 2.1.2 Slogan  
“Onde cada cooperado é parte da solução.”

---

#### 2.1.3 Identidade Visual e Cultural

##### História  
A **Cred Vale Doce** foi fundada em 2015, na cidade de **Guanhães**, em **Minas Gerais**, por produtores rurais, comerciantes e empreendedores locais que buscavam uma alternativa justa aos bancos tradicionais. Seu objetivo inicial era apoiar a expansão da produção de leite, promovendo a inclusão financeira e o fortalecimento da economia regional.  

Ao longo dos anos, graças à experiência acumulada e aos resultados alcançados, a cooperativa expandiu suas atividades para cidades vizinhas, sempre preservando o espírito cooperativista que inspirou sua origem.  

##### Missão  
Oferecer serviços financeiros acessíveis e transparentes, promovendo o desenvolvimento econômico e social das comunidades onde atua.

##### Visão  
Ser reconhecida como a principal cooperativa financeira do Vale do Rio Doce Mineiro até 2030, destacando-se pela inovação tecnológica e proximidade com os cooperados.

##### Valores  
- Transparência e ética  
- Valorização da comunidade  
- Inclusão financeira  
- Inovação com responsabilidade  

##### Logo   

#### Figura 1. Logo e Marca CRED VALE DOCE
<img width="532" height="128" alt="Screen Shot 2025-10-13 at 21 28 20" src="https://github.com/user-attachments/assets/12988011-7a73-40de-98b7-95b9671f00e9" />

*Fonte: elaboração própria.*

A identidade visual da **Cred Vale Doce** foi desenvolvida para refletir **confiança, cooperação e crescimento**.  

O **azul** foi escolhido como cor principal por transmitir **segurança, credibilidade e profissionalismo**, enquanto o **verde** complementa com a ideia de **prosperidade e estabilidade financeira**.  

A **tipografia sem serifa (Montserrat Bold)** utilizada no nome é moderna, limpa e de fácil leitura, reforçando **clareza e transparência na comunicação**.  

O **símbolo da logo**, formado por um círculo com uma seta ascendente, representa **união, integração e evolução**, traduzindo o propósito da cooperativa de **promover o crescimento sustentável de seus associados**.  

---

### Estrutura de Colaboradores

- **Total:** cerca de 125 colaboradores  
- **Distribuição:**  
  - **Matriz:** 50 colaboradores  
  - **Filiais:** média de 15 colaboradores cada (gerência, atendimento, suporte, TI local)

---

### Estimativa do Número de Clientes
- **Total estimado:** 59.000 cooperados

---

### Localização (MG)

**Matriz e cinco filiais** em cidades estratégicas (polo + entorno):

| Unidade | Cidade | Atividade Econômica Principal |
|:---------|:--------|:------------------------------|
| **Matriz** | Guanhães | Produção de leite (Vale do Rio Doce) |
| **Filial 1** | Conceição do Mato Dentro | Mineração de ferro |
| **Filial 2** | Serro | Produção de queijo do Serro |
| **Filial 3** | Virginópolis | Produção de jabuticaba |
| **Filial 4** | Diamantina | Produção de vinhos |
| **Filial 5** | Governador Valadares | Fruticultura e indústria de serviços |

---

### Serviços Oferecidos

#### a) Serviços Bancários
- Contas correntes, poupança e investimentos  
- Empréstimos e financiamentos (rurais e comerciais)  
- Crédito consignado  
- Cartões de débito e crédito próprios da cooperativa  
- Aplicações financeiras e fundos cooperativos  

#### b) Serviços Digitais
- Internet Banking e Mobile Banking  
- PIX e transferências instantâneas  
- Atendimento por chatbot via mensageiros instantâneos e assistente virtual  
- Central de suporte remoto às filiais  

#### c) Serviços para Empresas
- Conta PJ com linhas de crédito para empreendedores  
- Máquinas de cartão e aplicativos de pagamento mobile  
- Gestão de folha de pagamento via cooperativa  

#### d) Ações Comunitárias
- Programas de educação financeira  
- Apoio a cooperativas agrícolas e projetos sociais  
  - Laboratório de inclusão digital  
  - Pontos de acesso à internet para cooperados e visitantes  

---

## 3. Desenvolvimento do Projeto

### 3.1 Metodologia

Para o desenvolvimento do projeto de rede da **CRED VALE DOCE**, será adotada a **Metodologia Top-Down**.  

Isso significa que, **primeiramente**, serão analisadas as **necessidades do cliente**, e **somente depois** serão definidos os **equipamentos, protocolos e serviços** necessários.  

Essa abordagem garante que o projeto atenda de forma precisa às demandas da cooperativa, equilibrando desempenho, custo e escalabilidade da infraestrutura.

---

### 3.2 Modelo

O modelo adotado neste projeto será o **TCP/IP (Transmission Control Protocol/Internet Protocol)**, ele é baseado no modelo conceitual **OSI (Open Systems Internnection)**, que foi criado para padronizar a comunicação entre dispositivos em redes de computadores. O modelo OSI é dividido em **7 camadas**. As três primeiras, mais externas: **7 (Aplicação); 6 (Apresentação); 5 (Sessão)**: referem-se ao conjunto de protocolos de Internet voltados para a “aplicação”, tratando dos processos de usuário e dos detalhes das aplicações. As camadas mais internas são voltadas ao Kernel, abordando os detalhes das comunicações. A camada **4 (Transporte)** é implementada por meio dos protocolos **TCP/UDP**; a camada **3 (Rede)**, por **IPv4 e IPv6**; a camada **2 (Enlace de Dados)** e a camada **1 (Física)** abrangem os drivers de dispositivos e o hardware (OPPENHEIMER, 1999).

Apesar de sua inegável importância histórica e didática, esse modelo não é utilizado de forma direta, ele é visto como um guia conceitual para a compreensão do processo de comunicação. O modelo utilizado no dia a dia é o **TCP/IP**, que se tornou a base para a internet como conhecemos hoje. Ele é composto por **quatro camadas principais**: a **camada de acesso à rede**, que faz as funções das camadas 1 e 2 do modelo OSI, que é responsável pela comunicação física e dos protocolos de enlace; a **camada de internet**, que seria responsável pela camada 3 de rede, onde atua o protocolo IP que faz o endereçamento lógico e o roteamento dos pacotes entre redes diferentes; a **camada de transporte**, **TCP, UDP**, que faz a entrega confiável entre os processos; e a **camada de aplicação** que faria o trabalho das camadas 5, 6 e 7 que englobam os protocolos que interagem diretamente com os usuários (OPPENHEIMER, 1999).

#### Figura 2. Modelo OSI e Modelo TCP/IP.
<img width="408" height="318" alt="Screen Shot 2025-10-13 at 21 40 24" src="https://github.com/user-attachments/assets/43ccbe97-1284-43e3-b5b3-4ee582ce0524" /> 

*Fonte: adaptado da aula do professor Alexandre Teixeira.*

A aplicação do modelo TCP/IP para esse projeto de uma cooperativa de crédito com cinco filiais se torna fundamental para viabilizar a integração e comunicação de ponta a ponta. Através da camada da internet as cinco filiais podem estar conectadas através do interessamento de IP e roteamento, possibilitando dessa forma um acesso centralizado aos sistemas corporativos e às bases de dados da matriz. Já na camada de transporte o TCP assegura que as informações cheguem de forma íntegra e confiável e a camada de aplicação que os colaboradores e cooperados possam ter acesso seguro aos serviços web.

Dessa forma, ao adotar o sistema TCP/IP a **CRED VALE DOCE** estabelecerá uma estrutura de rede que assegure escalabilidade, segurança e confiabilidade, sustentando assim suas operações em múltiplas filiais e mantendo uma comunicação eficiente entre a matriz, as outras unidades e os usuários finais.

---

### 3.3 Requisitos de Negócio

Seguindo essas etapas, foram avaliados os requisitos de negócio da **CRED VALE DOCE** e os objetivos são:

* Aumentar a receita e o lucro da cooperativa;  
* Expandir a participação no mercado;  
* Ampliar as vantagens competitivas em relação aos concorrentes;  
* Reduzir custos e, principalmente, riscos de segurança;  
* Aumentar a produtividade dos colaboradores;  
* Melhorar o suporte aos clientes;  
* Evitar interrupções de serviços;  
* Tornar o Data Center mais eficiente.

---

### 3.4 Restrições do Projeto

Foram levantadas as seguintes restrições:

* **Restrição orçamentária:** o projeto possui verba definida de **R$ 1.150.000,00**;  
* **Prazo de realização:** prazo de execução de **4 meses**.

---

### 3.5 Levantamento de Informações que possam impactar a aprovação e implantação do projeto

#### 3.5.1 Organograma da CRED VALE DOCE

* **Assembleia Geral**  
Formada pelos cooperados.

* **Conselho de Administração**  
Presidente;  
Vice-Presidente;  
Conselheiros.

* **Diretoria Executiva**  
Diretor Geral (CEO/Presidente Executivo);  
Diretor Financeiro (CFO);  
Diretor de Operações (COO);  
Diretor de Tecnologia da Informação (CIO/CTO);  
Diretor de Negócios e Relacionamento;  
Diretor de Riscos & Compliance.

* **Estruturas Operacionais**  
Diretoria Financeira;  
Tesouraria;  
Controladoria;  
Contabilidade.

* **Diretoria de Operações**  
Gerência de Atendimento (agências e cooperados);  
Gerência de Produtos e Serviços Bancários;  
Gerência de Suporte Administrativo (backoffice, crédito, consignado, cartões).

* **Diretoria de Tecnologia da Informação**  
Infraestrutura e Redes (AD, links, servidores, segurança);  
Desenvolvimento e Sistemas (Internet Banking, Mobile, ERP);  
Suporte Técnico (helpdesk interno, filiais);  
Segurança da Informação (LGPD, gestão de acessos).

* **Diretoria de Negócios e Relacionamento**  
Gerência Comercial (captação de novos cooperados, crédito PJ);  
Marketing e Comunicação (identidade visual, campanhas, educação financeira);  
Projetos Comunitários (laboratório de inclusão digital, apoio a produtores).

* **Diretoria de Riscos & Compliance**  
Auditoria Interna;  
Gestão de Riscos (operacional, de crédito, de mercado);  
Jurídico & Regulatório (BACEN, LGPD, legislação cooperativista).

* **Estrutura Regional (Matriz + Filiais)**  
Gerente da Matriz (Guanhães);  
Gerente de cada Filial (5 no total) — reportam à Diretoria de Operações;  
Equipe de Atendimento ao Cooperado;  
Suporte Local (TI básico, administrativo).

---

#### Figura 3.Organograma Matriz CRED VALE DOCE.
<img width="640" height="337" alt="Screen Shot 2025-10-13 at 21 50 33" src="https://github.com/user-attachments/assets/f0938eac-6249-4e1a-a480-1284a82c12fa" />

*Fonte: elaboração própria.*

---

#### Figura 4.Organograma Filial CRED VALE DOCE. 
<img width="621" height="355" alt="Screen Shot 2025-10-13 at 21 53 52" src="https://github.com/user-attachments/assets/a876159e-0043-4c23-a2af-8c40421f80b7" />

*Fonte: elaboração própria.*

---

#### 3.5.2 Localização Geográfica

Embora a distância entre a matriz e as suas filiais seja considerável, isso não representa um problema para a conectividade e integração entre esses locais. Isso porque a comunicação e o tráfego de dados não dependem mais de conexões físicas manuais, mas sim de tecnologias modernas e automatizadas, que garantem uma ligação eficiente, independentemente da distância geográfica.

---

#### Figura 5. Mapa Matriz e Filiais CRED VALE DOCE.  
<img width="521" height="299" alt="Screen Shot 2025-10-13 at 21 57 48" src="https://github.com/user-attachments/assets/fd445735-a623-4c1a-944c-998e2078d0a4" />

*Fonte: elaboração própria.*

---

#### Figura 6. Distância entre a Matriz e as Filiais CRED VALE DOCE.  
<img width="306" height="274" alt="Screen Shot 2025-10-13 at 21 58 49" src="https://github.com/user-attachments/assets/bbebeb37-d195-444b-9645-490342bb094f" />

*Fonte: elaboração própria.*

---

### 3.6 Divisão Lógica das Comunidades de Usuários

* **Grupo A:** Funcionários (rede corporativa interna)  
* **Grupo B:** Clientes (serviços digitais externos)  
* **Grupo C:** Visitantes (rede Wi-Fi segregada)

---

### 3.7 Estruturação Lógica do Projeto

#### 3.7.1 Endereçamento

#### Tabela 1. IP’s CRED VALE DOCE.  
<img width="624" height="347" alt="Screen Shot 2025-10-13 at 22 01 27" src="https://github.com/user-attachments/assets/bb3f3c38-ef2b-4c10-aabc-bd0931c3fcdf" />

*Fonte: elaboração própria.*

---

### 3.7.2 Serviços de Rede

* Servidor **DNS**, **DHCP**, **Web**, **Impressão** e **E-mail**;  
* **Autenticação centralizada (AD)**;  
* **Link dedicado**, **VPN site-to-site** entre matriz e filiais;  
* **FTP**;  
* **Wi-Fi Corporativo** e outro **Público**;  
* **Banco de Dados**.

---

### 3.7.3 Protótipo

O protótipo foi desenvolvido utilizando o **Cisco Packet Tracer** e servirá de base para o levantamento preliminar de equipamentos.

---

#### Figura 7. Protótipo de rede CRED VALE DOCE.  
<img width="703" height="315" alt="Screen Shot 2025-10-13 at 22 02 29" src="https://github.com/user-attachments/assets/57645acf-aabc-4c50-9a73-0a36e6d33c80" />

*Fonte: elaboração própria.*

---

Nele foi utilizado uma WAN em formato de anel que é o mais apropriado levando em consideração as características do projeto. A cooperativa com uma matriz e cinco filiais terá um maior equilíbrio entre o desempenho, o custo e confiabilidade se o projeto seguir essa topologia porque cada filial é interligada a próxima o que forma um circuito fechado, permitindo que os dados possam trafegar em ambas as direções, o que mantém a comunicação ativa mesmo que aconteça uma falha em um dos pontos porque existe um caminho alternativo, dando uma maior possibilidade de disponibilidade na rede. Além disso, o formato anel também facilita o gerenciamento do fluxo de informações entre a matriz e as filiais, o que reduz a possibilidade de congestionamento e otimiza a velocidade da transmissão.  

Quando pensamos em cooperativa de crédito essa integração e o acesso contínuo aos sistemas são essenciais para o atendimento aos cooperados, a escolha da topologia em anel se mostra uma solução eficiente e segura e mantém os custos em infraestrutura mais acessíveis que outras mais complexas, como a malha completa. A malha completa seria uma solução inviável porque apesar de oferecer redundância, ela exige um custo de infraestrutura alto e uma complexidade desnecessária e aumentaria a possibilidade de erros, por causa da quantidade de rotas disponíveis, tornando o anel uma alternativa mais equilibrada e confiável. Outra possibilidade seria a em estrela, já que é uma rede relativamente pequena mas, por ser uma cooperativa é essencial evitar que ocorra uma falha crítica que possa derrubar toda a rede, porque a disponibilidade da rede é essencial para atender aos cooperados nas várias filiais.

A rede corporativa foi estruturada de forma a contemplar conectividade entre a Matriz e as cinco Filiais utilizando uma WAN, com enlaces redundantes e roteadores dedicados em cada unidade. Cada roteador da WAN conecta-se à sua respectiva LAN local, garantindo segmentação, desempenho e segurança. A Matriz é o ponto central de administração e gerenciamento dos serviços, conectando-se diretamente à todas as Filiais, fechando o circuito lógico. Cada filial possui roteadores configurados em faixas de endereçamento privadas distintas, conforme Tabela 1 dos IP’S definida no projeto, utilizando a Classe A - faixa (10.x.x.x), formando um anel lógico que interliga todas as unidades.

---

#### 3.7.3.1 Protótipo Matriz

---

#### Figura 8. Protótipo de rede Matriz CRED VALE DOCE.
<img width="567" height="408" alt="Screen Shot 2025-10-13 at 22 07 44" src="https://github.com/user-attachments/assets/d8a3a75e-b95c-4471-93ca-c09943c555c0" />

*Fonte: elaboração própria.*

---

Na Matriz, o roteador da WAN conecta-se à infraestrutura LAN, que foi organizada para suportar os seguintes setores e serviços:

- **Departamentos Operacionais:** Diretoria, Tesouraria, T.I. e Atendimento, projetados para 50 equipamentos.  
- **Rede Pública Wi-Fi:** disponível para visitantes e usuários externos.  
- **Laboratório de Informática:** voltado à comunidade, com capacidade para 10 equipamentos.  
- **CPD**, contemplando os seguintes serviços:  
  - Servidor 1: Active Directory (AD), HTTP, DNS e E-mail (suportando Matriz e Filiais).  
  - Servidor 2: DHCP e FTP (dedicado à Matriz).  

A camada de rede foi planejada com **1 switch L3 na camada de Acesso** e **3 switches de 24 portas na camada de Distribuição**, permitindo expansão futura.

---

### Estrutura de Endereçamento IP

A rede LAN foi organizada em sub-redes distintas para garantir **isolamento** e **controle de tráfego** da rede:

- **LAN Operacional – Departamentos internos (Classe B)**  
  IP Address: 172.16.100.0  
  Subnet Mask: 255.255.255.0 (/24)  
  Gateway: 172.16.100.1  
  Faixa de IPs: 172.16.100.1 – 172.16.100.100  
  DHCP Pool: 172.16.100.11 – 172.16.100.100  

- **LAN Pública / Laboratório (Classe C)**  
  IP Address: 192.168.100.0  
  Subnet Mask: 255.255.255.0 (/24)  
  Gateway: 192.168.100.1  
  Faixa de IPs: 192.168.100.1 – 192.168.100.254  
  DHCP Pool: 192.168.100.2 – 192.168.100.254  

Adicionalmente, foram configuradas redes Wi-Fi independentes para os seguintes contextos:  

- Operacional (uso interno e seguro).  
- Público / Laboratório (uso externo e visitantes).  

---

### 3.7.3.2 Protótipo Filial

#### Figura 9. Protótipo de rede Filial CRED VALE DOCE.  
<img width="589" height="436" alt="Screen Shot 2025-10-13 at 22 12 21" src="https://github.com/user-attachments/assets/63544204-e440-4ad0-8ec4-bab20bbd55de" />

*Fonte: elaboração própria.*

Cada filial foi projetada com uma LAN estruturada, interligada ao respectivo roteador da WAN, garantindo **independência lógica** e **conectividade com a Matriz e demais unidades**. A configuração foi padronizada para todas as cinco filiais, assegurando **uniformidade administrativa**, **facilidade de manutenção** e **expansão futura**.

---

### Estrutura da Rede LAN das Filiais

- 15 equipamentos operacionais, distribuídos entre os departamentos de **TI, Gerência, Administrativo e Atendimento**.  
- Laboratório de informática, com 5 equipamentos destinados à comunidade ou treinamentos internos.  
- Rede Pública Wi-Fi, dedicada a visitantes e usuários externos.  
- Pontos de Acesso Wi-Fi (APs) segmentados:  
  - 1 AP para a rede Operacional (uso interno)  
  - 1 AP para a rede Pública (uso de visitantes)  
  - 1 AP para o Laboratório (uso comunitário)  

---

### CPD  

- 1 Servidor dedicado, configurado para prover os serviços de **DHCP e FTP** em cada filial.  
- 1 Switch de Distribuição, responsável pela conexão dos equipamentos locais e integração com o roteador WAN.  

---

### Estrutura de Endereçamento IP das Filiais

As redes foram segmentadas em **sub-redes Operacionais** e **sub-rede Públicas e Laboratório**, com escopos de DHCP próprios para cada filial, conforme detalhado na Tabela 1.

- **LAN Operacional – Filiais (Classe B)**  
  - Filial 1: IP Address 172.16.201.0  
  - Filial 2: IP Address 172.16.202.0  
  - Filial 3: IP Address 172.16.203.0  
  - Filial 4: IP Address 172.16.204.0  
  - Filial 5: IP Address 172.16.205.0  

- **LAN Pública / Laboratórios - Filiais (Classe C)**  
  - Filial 1: IP Address 192.168.201.0  
  - Filial 2: IP Address 192.168.202.0  
  - Filial 3: IP Address 192.168.203.0  
  - Filial 4: IP Address 192.168.204.0  
  - Filial 5: IP Address 192.168.205.0  

---

### 3.7.4 Planilha de Equipamentos

#### Tabela 2. Tabela de equipamentos Matriz CRED VALE DOCE.  
<img width="753" height="340" alt="Screen Shot 2025-10-13 at 22 15 23" src="https://github.com/user-attachments/assets/9f10e757-239a-4abc-86c6-a57c862a5292" />

*Fonte: elaboração própria.*

#### Tabela 3. Tabela de equipamentos Filial CRED VALE DOCE.  
<img width="751" height="288" alt="Screen Shot 2025-10-13 at 22 16 11" src="https://github.com/user-attachments/assets/66569962-7d4c-4144-bcd9-38a3363ed992" />

*Fonte: elaboração própria.*

---

### 3.7.5 Planilha de Cálculo de Links

#### Tabela 4. Tabela de Cálculo de Links de Dados de Internet CRED VALE DOCE.  
<img width="1465" height="340" alt="Screen Shot 2025-10-15 at 00 14 14" src="https://github.com/user-attachments/assets/b9548a8c-09bb-410b-88aa-bd31a88a3062" />

*Fonte: elaboração própria.*

---

### 3.7.6 Testes

#### Conexão entre máquinas

A primeira imagem representa a comunicação de máquinas na rede LAN, respectivamente, da matriz e de uma filial, nesse caso escolhida a filial 1. Já a segunda imagem representa respectivamente a comunicação entre a matriz e uma filial, foi escolhida para esse teste a filial 4, e a comunicação entre filiais, foram escolhidas as filiais 3 e 5.

---

#### Figura 10. Comunicação de máquinas matriz e filial 1.  
<img width="486" height="64" alt="Screen Shot 2025-10-13 at 22 18 34" src="https://github.com/user-attachments/assets/22612e41-2cdc-4027-b1ea-b3cc6349084e" />

*Fonte: elaboração própria.*

#### Figura 11. Comunicação de máquinas matriz e filial 4 e entre filiais 3 e 5.  
<img width="485" height="64" alt="Screen Shot 2025-10-13 at 22 19 10" src="https://github.com/user-attachments/assets/20448697-c639-4dbc-b6e7-0ba2cf8c4495" />

*Fonte: elaboração própria.*

---

#### Entrega de IP por DHCP

Na primeira imagem temos a entrega do IP por meio de DHCP para uma máquina na matriz, e na segunda para uma máquina na filial, foi escolhida a filial 2.

---

#### Figura 12. Entrega do IP para matriz.  
<img width="626" height="175" alt="Screen Shot 2025-10-13 at 22 19 53" src="https://github.com/user-attachments/assets/0dc36640-9d85-4143-a389-b776754f1681" />

*Fonte: elaboração própria.*

---

#### Figura 13. Entrega do IP para filial 2.  
<img width="627" height="183" alt="Screen Shot 2025-10-13 at 22 22 38" src="https://github.com/user-attachments/assets/372974e4-87bb-49ff-8a3a-e8b3c48673fb" />

*Fonte: elaboração própria.*

---

### Acesso WEB e funcionamento de DNS

Nestas imagens está demonstrado o acesso à uma página web que está no servidor WEB utilizando o nome configurado no servidor de DNS, ambos situados na matriz. A primeira imagem refere à uma máquina que está na matriz, já a segunda à uma máquina situada na filial 5.

#### Figura 14. Acesso a página WEB por máquina na matriz.  
<img width="625" height="365" alt="Screen Shot 2025-10-13 at 22 23 29" src="https://github.com/user-attachments/assets/37c9dac7-4c46-4665-bd5c-60e47350d17c" />

*Fonte: elaboração própria.*

#### Figura 15. Acesso a página WEB por máquina na filial 5.  
<img width="626" height="377" alt="Screen Shot 2025-10-13 at 22 24 02" src="https://github.com/user-attachments/assets/2f25f19c-feaa-4d2a-b531-4301a5166216" />

*Fonte: elaboração própria.*

---

### Servidor de FTP

Na primeira imagem foi feito o envio de um arquivo de uma máquina para o servidor de FTP da matriz, e na segunda foi realizado o mesmo de uma máquina para o servidor da filial 4.

#### Figura 16. Envio de arquivo de máquina da matriz para servidor FTP da matriz.  
<img width="626" height="426" alt="Screen Shot 2025-10-13 at 22 24 45" src="https://github.com/user-attachments/assets/1df80d77-d899-49ff-b160-d04b5fd6a546" />

*Fonte: elaboração própria.*

#### Figura 17. Envio de arquivo de máquina da filial 4 para servidor FTP da filial 4.  
<img width="626" height="394" alt="Screen Shot 2025-10-13 at 22 25 25" src="https://github.com/user-attachments/assets/bd283aca-3976-4e6f-984a-5ad2a1e4f2d4" />

*Fonte: elaboração própria.*

---

## Referência Bibliográfica

OPPENHEIMER, Priscilla. *Projeto de redes top-down: um enfoque de analise de sistemas para o projeto de redes empresariais.* Rio de Janeiro: Campus, 1999.

