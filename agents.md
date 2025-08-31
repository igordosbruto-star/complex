# AGENTS.md — Arquitetura de Agentes

Este documento descreve a arquitetura de **agentes** do projeto **Robô Universal de Vendas para WhatsApp (CodeX)** e orienta como cada componente será implementado em **Python**. Os agentes são serviços autônomos que interagem entre si para cumprir funções específicas da plataforma, sempre **alinhados ao ROADMAP.md e CHANGELOG.md**, garantindo consistência e rastreabilidade no desenvolvimento.

---

## 1. Visão Geral da Arquitetura

A solução é composta por múltiplos **agentes Python**, cada um responsável por uma camada do funil de vendas:

- **Agente Gateway WhatsApp**: faz a ponte com a API oficial (ou provedores compatíveis).  
- **Agente de Conversa**: utiliza IA (ex.: GPT) e regras configuráveis para interpretar e responder mensagens.  
- **Agente de Catálogo**: gerencia produtos/serviços e prepara listas ou carrosséis para envio.  
- **Agente de Qualificação**: conduz o lead pelo funil, coletando nome, interesse, orçamento e outras informações.  
- **Agente de Checkout**: cria links ou QR Codes para pagamento (Pix, cartão) e confirma status.  
- **Agente de Integrações**: conecta CRM/ERP/e-commerce e propaga eventos via webhooks.  
- **Agente de Orquestração**: coordena o fluxo entre os demais agentes, aplica regras de negócio e encaminha transferências para atendentes humanos quando necessário.  
- **Agente de Logs/Analytics**: centraliza métricas (SLA, conversão, tickets) e exporta relatórios para dashboards.

---

## 2. Responsabilidades e Interfaces

### 2.1 Agente Gateway WhatsApp
- **Função:** enviar/receber mensagens, arquivos, botões e listas pelo WhatsApp Business API.  
- **Interface:** expõe endpoints HTTP (FastAPI) para receber eventos e utiliza webhooks para novos textos ou mídias.  
- **Exemplo de estrutura:**
  ```python
  from fastapi import FastAPI
  app = FastAPI()

  @app.post("/whatsapp/webhook")
  async def inbound_webhook(event: dict):
      # parseia o evento e encaminha ao Orquestrador
      pass
  ```

### 2.2 Agente de Conversa
- **Função:** interpretar mensagens livres via modelo de linguagem (ex.: GPT) e aplicar regras da DSL de fluxo.  
- **Interface:** recebe intent + contexto e devolve resposta + próximo estado.  
- **Detalhes:** usa `httpx`/`aiohttp` para consumir serviços de IA; mantém memória de sessão.  

### 2.3 Agente de Catálogo
- **Função:** CRUD de produtos/serviços, preços, descrições e imagens.  
- **Interface:** APIs REST para consulta e atualização de catálogo; resposta pronta para o Orquestrador.  

### 2.4 Agente de Qualificação
- **Função:** aplicar questionários para qualificar leads.  
- **Interface:** fluxo automatizado que interage com o Agente de Conversa e registra dados no banco.  

### 2.5 Agente de Checkout
- **Função:** integração com gateways de pagamento (Pix, cartão, boleto).  
- **Interface:** gera link/QR Code, consulta status e retorna confirmação.  

### 2.6 Agente de Integrações
- **Função:** sincronizar dados com ERP, CRM e e-commerce.  
- **Interface:** expõe webhooks e API REST para consumo por terceiros.  

### 2.7 Agente de Orquestração
- **Função:** coordenar a comunicação entre os agentes conforme regras do funil.  
- **Interface:** recebe eventos do Gateway, decide o próximo passo no fluxo (via DSL) e gerencia fallback humano.  

### 2.8 Agente de Logs/Analytics
- **Função:** coletar métricas de conversas, vendas e performance.  
- **Interface:** exporta dados para Prometheus/Grafana; gera relatórios acessíveis no painel administrativo.  

---

## 3. Comunicação entre Agentes
- **Transporte:** HTTP/REST no MVP; evoluir para mensageria assíncrona (RabbitMQ/Kafka) em fases futuras.  
- **Formato:** JSON validado via **Pydantic**.  
- **Rastreabilidade:** cada evento deve carregar `session_id` e `trace_id` para auditoria e análise.  

---

## 4. Padrões de Desenvolvimento em Python
- **Versão:** Python 3.9+ (com suporte a async/await).  
- **Frameworks:** FastAPI, Pydantic, SQLAlchemy (ou equivalente) para persistência.  
- **Estilo:** seguir PEP 8; usar `black`, `isort` e `flake8`.  
- **Logs:** `logging` + função utilitária `wr:p` para mensagens `info`, `warn`, `error`.  
- **Testes:** `pytest` e `pytest-asyncio`, com cobertura mínima de 80 %.  

---

## 5. Alinhamento com ROADMAP.md e CHANGELOG.md
- Cada agente deve ser planejado e priorizado de acordo com as **fases descritas no ROADMAP.md**.  
- Toda mudança ou novo agente precisa ser registrada no **CHANGELOG.md** na seção adequada (Unreleased ou versão correspondente).  
- O **CodeX** auxilia na criação de issues, PRs e commits para manter a rastreabilidade.  

---

## 6. Extensibilidade
- **Novo agente:** implementar a classe base `BaseAgent` em Python com métodos `async def handle_event(self, event): ...`.  
- **Novos canais:** criar agentes Gateway adicionais seguindo a mesma interface do WhatsApp.  
- **Plug-ins externos:** roadmap prevê marketplace (Fase 6) para que terceiros desenvolvam agentes customizados.  

---

## 7. Monitoramento e Observabilidade
- Cada agente deve expor *healthcheck* e métricas.  
- Acompanhar performance, SLA e erros conforme métricas definidas no **VISION.md**.  
- Relatórios de evolução devem ser vinculados ao **CHANGELOG.md**.  

---

✨ Com este guia, asseguramos que todos os agentes do projeto sejam consistentes com a visão (VISION.md), o planejamento (ROADMAP.md) e as diretrizes de contribuição (CONTRIBUTING.md).

