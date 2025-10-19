# Plano de Trabalho – Etapa 2 do Projeto de Rede Estruturada

## Objetivo
Configurar e documentar os principais serviços de rede (**FTP, NFS, Web/Apache, DNS, Banco de Dados, DHCP, AD + GPO**), garantindo integração entre eles, segurança e disponibilidade, conforme os critérios de avaliação.

---

## 1. Organização da Equipe
- **Carlos** → Configuração e testes do FTP e ajuda no AD.  
- **Odair** → Configuração e testes do NFS.  
- **Lucas** → Configuração do servidor Web (Apache).  
- **Yan** → Configuração do DNS.  
- **Victor** → Configuração do Banco de Dados (PostgreSQL).
- **Luana** → Configuração e testes AD e ajuda no DHCP.   
- **Laura** → Configuração e testes do DHCP.  
- **Todos** → Colaboração na documentação final, revisão e testes integrados.  

---

## 2. Fases do Trabalho

### 2.1 Fase 1 – Revisão do Planejamento
- Definir endereçamento IP (fixo e DHCP).  
- Revisão da planilha de recursos de rede (com base na topologia e equipamentos).  

**Entrega parcial:**  
- Planilha revisada de recursos de rede.

---

### 2.2 Fase 2 – Configuração Individual
Cada membro ficou responsável pela configuração de um serviço inicialmente:  

- **Carlos (FTP)** → criar usuários, testar envio/recebimento.  
- **Luana (AD)** → criar usuários e grupos, organizar OUs, aplicar políticas de segurança e restrições via GPO, testar autenticação e permissões.  
- **Odair (NFS)** → configurar diretórios exportados, testar leitura/escrita.  
- **Lucas (Apache)** → hospedar página inicial, habilitar logs.  
- **Yan (DNS)** → criar zonas direta e reversa, validar resolução de nomes.  
- **Victor (PostgreSQL)** → criar banco inicial, permissões de usuários, testar conexões.  
- **Laura (DHCP)** → configurar range de IPs, reservas, testes de atribuição dinâmica.  

**Entrega parcial:**  
- documentação de configuração de cada serviço e prints dos testes.

---

### 2.3 Fase 3 – Documentação Final
- Consolidar o relatório de configuração de serviços + evidências de testes.  
- Montar a apresentação em um vídeo de até 20 minutos com a demonstração de todos os serviços funcionando.

---

# Cronograma de Atividades – 2ª Etapa

| Equipe | Carga Horária | Ações/Atividades | Data |
|--------|---------------|-----------------|------|
| Carlos Alberto Vieira de Souza; Laura de Freitas Mendes Losque; Luana Horta de Souza; Lucas Araújo Pacheco; Odair Cordeiro Marra; Victor Samuel Costa Pereira; Yan Oyama Moura. | 1:00 h | Reunião inicial. | 15/09 |
| Carlos Alberto Vieira de Souza; Laura de Freitas Mendes Losque; Luana Horta de Souza; Lucas Araújo Pacheco; Odair Cordeiro Marra; Victor Samuel Costa Pereira; Yan Oyama Moura. | 2:20 h | Reunião para divisão de tarefas. | 24/09 |
| Carlos Alberto Vieira de Souza; Laura de Freitas Mendes Losque; Luana Horta de Souza; Lucas Araújo Pacheco; Odair Cordeiro Marra; Victor Samuel Costa Pereira; Yan Oyama Moura. | 5:00 h | Reunião para ajudar quem ainda não havia baixado as máquinas virtuais. | 25/09 |
| Carlos Alberto Vieira de Souza; Laura de Freitas Mendes Losque; Luana Horta de Souza; Lucas Araújo Pacheco; Odair Cordeiro Marra; Victor Samuel Costa Pereira; Yan Oyama Moura. | 2:30 h | Reunião para entrar em no github e ver progresso. | 06/10 |
| Carlos Alberto Vieira de Souza; Laura de Freitas Mendes Losque; Luana Horta de Souza; Lucas Araújo Pacheco; Odair Cordeiro Marra; Victor Samuel Costa Pereira; Yan Oyama Moura. | 3:00 h | Reunião para definir o padrão do trabalho e dos vídeos. | 08/10 |
| Carlos Alberto Vieira de Souza; Laura de Freitas Mendes Losque; Luana Horta de Souza; Lucas Araújo Pacheco; Odair Cordeiro Marra; Victor Samuel Costa Pereira; Yan Oyama Moura. | 1:30 h | Reunião para atualizações. | 13/10 |


# Atividades Individuais – 2ª Etapa

- **Carlos** →  
- **Luana** → fiz o servidor e cliente AD e a documentação do mesmo, ajudei a Laura no servidor DHCP e editei o video da entrega.
- **Odair** →   
- **Lucas** →  
- **Yan** →   
- **Victor** →  
- **Laura** → fiz o servidor e o cliente DHCP  
