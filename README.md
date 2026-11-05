# Gabriel de Almeida Cerqueira

Engenharia de Software e Inteligência Artificial Aplicada.  
Estudante de Engenharia da Computação no UniSALESIANO (formação prevista para Dezembro de 2026) e Estagiário de Desenvolvimento de Software na GIMB.

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=flat&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/gabrielde-almeida-cerqueira479390256)
[![GitHub](https://img.shields.io/badge/GitHub-Gabriel--Cerqueira-181717?style=flat&logo=github&logoColor=white)](https://github.com/Gabriel-Cerqueira)
[![Email](https://img.shields.io/badge/Email-gabrieldealmeidacerqueira%40hotmail.com-181717?style=flat&logo=microsoftoutlook&logoColor=white)](mailto:gabrieldealmeidacerqueira@hotmail.com)
[![Localização](https://img.shields.io/badge/Localiza%C3%A7%C3%A3o-Ara%C3%A7atuba%2C%20SP-24292e?style=flat&logo=googlemaps&logoColor=white)](https://maps.google.com/?q=Aracatuba,+SP)

---

## Perfil Técnico

Atuação orientada à construção de software resiliente, combinando fundamentos de engenharia de software com inteligência artificial aplicada à automação de fluxos reais:

1. **Engenharia de Software Corporativa:** Desenvolvimento de serviços backend e interfaces web com foco em manutenibilidade, contratos estritos e resiliência transacional. Experiência de mercado na sustentação e evolução de sistemas corporativos utilizados por grandes players industriais (Solinftec, Raízen e Atvos).
2. **Engenharia de IA & Sistemas Inteligentes (AI Engineering):** Aplicação prática e arquitetura de modelos de linguagem (LLMs) integrados a sistemas de produção. Construção de soluções baseadas em chamadas determinísticas de ferramentas (*Function Calling*), pipelines assíncronos, saídas estritamente estruturadas em JSON Mode, avaliação sistemática de acurácia de prompts e integração com interfaces físicas e web.
3. **Engenharia de Baixo Nível e Sistemas:** Bagagem prática em laboratório de eletrônica e formação em Engenharia da Computação aplicada a hardware (Raspberry Pi), automação nativa, consumo de APIs do sistema operacional (Windows API) e desenvolvimento em Rust e Java moderno.

---

## Projetos de Código Aberto em Destaque

### Nexus — Interface Física Reconfigurável por LLM (TCC)
*Console físico de automação contextual com Raspberry Pi e orquestração determinística via IA.*

- **Contexto:** Painéis convencionais de automação de mesa (como Stream Decks) possuem leiautes estáticos e macros fixas. O Nexus permite que o operador configure o console físico dinamicamente através de instruções em linguagem natural.
- **Implementação de IA:** Agente orquestrador com suporte a Gemini API e DeepSeek via *Function Calling*. O modelo decide ferramentas e parâmetros validados deterministicamente pelo backend antes de refletir no display touch (800x480).
- **Rigor de Engenharia:** Versionamento formal de diretrizes de sistema (`PROMPT_VERSION`), script dedicado de avaliação de acurácia de intenções (`eval_prompt.py`), isolamento de privilégios (`PluginSpec`) e barramento bidirecional com FastAPI e Socket.IO.
- **Contribuições Específicas de Gabriel:**
  - Desenvolvimento do subsistema de notificações multiplataforma (`plugins/notification.py`), sincronizando alertas no display touch do Raspberry Pi e na API nativa do sistema operacional host.
  - Implementação inicial do serviço de chat (`chat_service.py`), rotas de API e telemetria de métricas operacionais.
  - Algoritmo geométrico de prevenção de colisões visuais no grid (`layout_ops.py`), assegurando posicionamento sem sobreposição de widgets.
- **Stack:** Python, FastAPI, Socket.IO, React, TypeScript, Raspberry Pi.
- **Repositório:** [Gabriel-Cerqueira/nexus](https://github.com/Gabriel-Cerqueira/nexus)

---

### OurBills API — Núcleo Financeiro com DDD & Concorrência
*Backend REST para gestão financeira pessoal com consistência contábil estrita e previsão de caixa.*

- **Contexto & Motivação:** Iniciado para solucionar uma dor real de gestão financeira e previsibilidade de caixa de uma pessoa próxima. Aproveitei o problema prático como laboratório deliberado para aprofundar e aplicar conceitos avançados de **System Design**, **testes automatizados** e **escalabilidade**. O projeto é um MVP em desenvolvimento ativo (não finalizado).
- **Padrões de Engenharia:**
  - Arquitetura de Monólito Modular modelada com agregados e invariantes de **Domain-Driven Design (DDD)**.
  - Segregação multi-tenant lógica por espaços financeiros (*Workspaces*).
  - Bloqueio otimista de concorrência (`@Version`) para transações financeiras simultâneas e recálculo atômico de saldos.
  - Trilha de auditoria *append-only* imutável para rastreabilidade de eventos contábeis.
  - 15 migrações versionadas com Flyway e suíte de testes de integração com Testcontainers.
- **Stack:** Java 21 LTS, Spring Boot 4, PostgreSQL 17, Flyway, Hibernate, Docker.
- **Repositório:** [Gabriel-Cerqueira/ourbills-api](https://github.com/Gabriel-Cerqueira/ourbills-api)

---

### AvaCatcher — Cliente Desktop Nativo em Rust e Tauri v2
*Aplicativo desktop multiplataforma para sincronização acadêmica e visualização offline.*

- **Contexto & Motivação:** Criado a partir de uma necessidade pessoal direta: precisava de uma solução moderna e rápida para acompanhar a data de atividades, provas e trabalhos marcados, eliminando a lentidão, fragmentação e dependência de conexão dos portais web acadêmicos convencionais.
- **Engenharia e Desempenho:**
  - Binário compilado nativo com consumo de memória de trabalho reduzido (~35 MB de RAM).
  - Rotina automatizada de autenticação (handshake SSO) com resolução de redirecionamentos via `reqwest` com TLS spoofing.
  - Parser HTML resiliente (`scraper`) para extração estruturada de notas e prazos.
  - Persistência e cache offline local utilizando SQLite embarcado via `rusqlite`.
- **Stack:** Rust, Tauri v2, SQLite, React 19, TypeScript, Tailwind CSS.
- **Repositório:** [Gabriel-Cerqueira/avacatcher](https://github.com/Gabriel-Cerqueira/avacatcher)

---

### Utilitários de Sistemas em Rust (PortGuard & DevSweep)
*Ferramentas de linha de comando (CLI) e interfaces de terminal (TUI) de alta eficiência.*

| Projeto | Propósito | Destaques Técnicos |
| :--- | :--- | :--- |
| **[PortGuard](https://github.com/Gabriel-Cerqueira/portguard)** | Inspeção e gerenciamento de portas de rede ativas no Windows. | Consulta direta às Windows IP Helper APIs (`GetExtendedTcpTable` e `GetExtendedUdpTable`). Mapeamento de consumo de RAM por processo, encerramento via `TerminateProcess`, modo interativo com `ratatui` e comandos diretos para scripts. |
| **[DevSweep](https://github.com/Gabriel-Cerqueira/devsweep)** | Varredura e expurgo seguro de caches de compilação descartáveis. | Travessia paralela de diretórios com `rayon` e `jwalk`. Detecção multiecossistema (`target/`, `node_modules/`, `.venv/`, `.gradle/`). Validação estrita contra deleções fora da raiz e integração com a Lixeira do Windows via Shell APIs (`IFileOperation`). |

---

## Experiência Profissional

### GIMB — Estagiário em Desenvolvimento de Software
*Março de 2025 — Presente | Araçatuba, SP*

- Desenvolvimento e manutenção de sistemas corporativos utilizados por clientes como Solinftec, Raízen e Atvos.
- Implementação de interfaces web com Angular 19 e TypeScript, e integração com APIs REST em Java.
- Manutenção de bancos de dados relacionais MySQL, modelagem de tabelas e otimização de consultas.
- Execução de testes de carga e diagnóstico de gargalos de desempenho em endpoints HTTP utilizando Apache JMeter.
- Atuação direta em suporte de segundo nível, depuração de erros em produção e garantia de qualidade de novas entregas.

### Multartec — Estagiário em Laboratório de Eletrônica
*Setembro de 2024 — Março de 2025 | Araçatuba, SP*

- Manutenção preventiva e corretiva de computadores de bordo e módulos eletrônicos automotivos e industriais.
- Diagnóstico de circuitos em bancada com osciloscópio e multímetro digital; substituição de componentes eletrônicos SMD e THT.
- Execução de testes funcionais padronizados para homologação pós-reparo e liberação de equipamentos em garantia.

---

## Formação Acadêmica e Certificações

- **Bacharelado em Engenharia da Computação**  
  UniSALESIANO — *Previsão de conclusão: Dezembro de 2026*
- **Microsoft Certified: Azure Fundamentals (AZ-900)** — SENAI / Microsoft (2023)
- **Fundamentos de Linguagem Python para Análise de Dados e Data Science (72h)** — Data Science Academy (2024)
- **Microsoft Power BI — Fundamentos (30h)** — SENAI (2023)
- **Inglês Avançado** — Formação Yázigi (2016 — 2021)

---

## Habilidades Técnicas

| Categoria | Tecnologias e Metodologias |
| :--- | :--- |
| **Linguagens** | Java 21, Rust, TypeScript, Python, JavaScript, SQL |
| **Backend & Arquitetura** | Spring Boot, FastAPI, RESTful APIs, Domain-Driven Design (DDD), Concorrência Transacional, Flyway, JWT |
| **Frontend & Desktop** | React 19, Angular 19, Tauri v2, Tailwind CSS, Vite |
| **IA & Automação** | Function Calling, Avaliação Sistemática de Prompts, Saídas Estruturadas (JSON Mode), Automação de Interfaces |
| **Dados & Infraestrutura** | PostgreSQL, MySQL, SQLite, Docker, Apache JMeter, Git, GitHub Actions, Microsoft Azure |
| **Sistemas & Hardware** | Windows API (IP Helper, Shell APIs), Raspberry Pi, Linux, Eletrônica de Bancada |

---

## Contato

- **LinkedIn:** [linkedin.com/in/gabrielde-almeida-cerqueira479390256](https://www.linkedin.com/in/gabrielde-almeida-cerqueira479390256)
- **GitHub:** [github.com/Gabriel-Cerqueira](https://github.com/Gabriel-Cerqueira)
- **E-mail:** [gabrieldealmeidacerqueira@hotmail.com](mailto:gabrieldealmeidacerqueira@hotmail.com)
