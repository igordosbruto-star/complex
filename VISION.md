# Documento de Visão — Robô Universal de Vendas para WhatsApp (CodeX)

> **Projeto:** Automatização de Vendas — *assistente comercial omnichannel iniciado pelo WhatsApp*
>
> **Desenvolvimento:** CodeX (ChatGPT + GitHub) — fluxo guiado por issues, PRs e revisão assistida por IA.

---

## 1. Introdução
Este documento estabelece a visão do **Robô Universal de Vendas para WhatsApp**, um sistema orientado a conversação que automatiza o funil comercial do primeiro contato ao fechamento.

**Objetivos do documento**
- Alinhar propósito, escopo e critérios de sucesso.
- Descrever requisitos de alto nível e restrições técnicas.
- Definir o fluxo de desenvolvimento com **CodeX** (ChatGPT conectado ao GitHub).

**Público-alvo**
- Empreendedores (micro a enterprise) que vendem via WhatsApp.
- Times de produto/engenharia e integradores.
- Parceiros de implantação e suporte.

---

## 2. Descrição Geral do Software
### 2.1 Visão Geral
O sistema é um **robô de vendas** plugável ao WhatsApp capaz de:
- Responder automaticamente, 24/7, com **IA + regras**.
- Apresentar **catálogo** (carrossel, imagens, PDFs, links de pagamento).
- **Qualificar** leads (nome, interesse, orçamento, localização, prazo).
- Conduzir **orçamento → pedido → pagamento** na própria conversa.
- Integrar-se a **pagamentos**, **ERP/CRM**,
- Gerar **relatórios** e insights de conversão.

### 2.2 Problema que Resolve
- Perda de vendas por respostas lentas/despadronizadas.
- Dificuldade em escalar atendimento simultâneo.
- Falta de rastreabilidade e métricas de performance.

### 2.3 Benefícios
- **Conversão maior** e **SLA menor**.
- Atendimento padronizado, sempre disponível.
- **Configuração universal** por segmento, sem código.
- Integrações nativas com stack do cliente.

---

## 3. Stakeholders e Usuários
- **Empreendedor/gestor:** define catálogo, ofertas e políticas.
- **Atendentes/vendedores:** acompanham exceções e intervenções humanas.
- **Clientes finais (WhatsApp):** recebem atendimento fluido e pagamento simplificado.
- **Equipe técnica/integradores:** cuidam de implantação, monitoramento e integrações.

---

## 4. Recursos Principais (alto nível)
1. **Conector WhatsApp** (API oficial / provedores compatíveis — ex.: Z-API): envio/recebimento, templates, mídia, botões, listas.
2. **Catálogo dinâmico**: produtos/serviços, variações, estoque básico, preços, combos/kit.
3. **Motor de Conversa**:
   - **IA (NLU/NLG)** para entendimento/geração.
   - **Regras e fluxos** (DSL declarativa) para triagem, qualificação e roteamento.
   - **Fallback humano** (transferência para atendente / fila).
4. **Checkout na conversa**: geração de links/cobranças, comprovantes, status do pagamento.
5. **Orquestração de integrações**: ERP/CRM, pagamentos, planilhas e webhooks.
6. **Configuração sem código**: intents frequentes, respostas, menus, horários, SLAs, mensagens de ausência/feriados.
7. **Relatórios e análises**: funil, taxa de conversão, tempo de resposta, ticket médio, produtos mais vendidos.
8. **Multi-tenant e multi-canal (futuro)**: WhatsApp (MVP) → Instagram, Facebook, Telegram.

---

## 5. Restrições e Limitações
- Depende de conectores/fornecedores do WhatsApp e suas políticas.
- Latência e limites de throughput podem variar por provedor.
- MVP focado em WhatsApp; demais canais entram no roadmap.

---

## 6. Critérios de Sucesso (Métricas)
- **TMR (tempo médio de resposta)**: redução ≥ 90% vs. baseline.
- **Conversão**: aumento ≥ 30% no período de 60 dias após go-live.
- **Aderência universal**: implantação bem-sucedida em ≥ 5 segmentos distintos sem alterações de código (apenas configuração).
- **Disponibilidade**: ≥ 99,5% mensal no serviço de mensagens e motor de conversa.

---

## 7. Roadmap Inicial
**Fase 0 — Fundacional (CodeX-ready)**
- Repo inicial com **VISION.md**, **ROADMAP.md**, **CONTRIBUTING.md**.
- Pipeline CI básico (lint/test/build) e templates de **issues/PRs**.
- Skeleton de serviços: gateway WhatsApp, motor de conversa, catálogo, checkout.

**Fase 1 — MVP (WhatsApp)**
- Conector WhatsApp estável (mensagens, mídia, templates, botões).
- DSL de fluxo/regras + blocos prontos: saudação, qualificação, catálogo, orçamento, pagamento.
- Configuração por JSON/YAML/UI simples.
- Logs/observabilidade básicos (conversas, erros, KPIs iniciais).

**Fase 2 — IA + Integrações**
- NLU customizável (intenções/entidades) e memória de sessão.
- Integrações de pagamento (ex.: Pix/links) e ERP/CRM (webhooks + mapeamento).
- Relatórios e dashboards (vendas, funil, SLA, produtos, origem de lead).

**Fase 3 — Escala e Omnichannel**
- Multi-tenant (isolamento lógico), marketplace de templates/setores.
- Canais adicionais (Instagram, FB, Telegram).
- Guardrails de compliance, auditoria e RBAC.

---

## 8. Requisitos Não Funcionais
- **Segurança**: criptografia em trânsito/repouso, sanitização de prompts, controle de sessão, RBAC.
- **Privacidade/Compliance**: LGPD (dados pessoais minimizados, consentimento, retenção configurável).
- **Escalabilidade**: horizontal nas camadas de mensageria e IA.
- **Observabilidade**: métricas, tracing, logs estruturados.
- **Localização**: pt-BR por padrão; i18n pronto para en-US/es-ES.
- **Resiliência**: tolerância a falhas de provedores terceiros (fila/retry/backoff, circuit breaker).

---

## 9. Desenvolvimento com CodeX (ChatGPT + GitHub)
- **CodeX como par programador**: geração/revisão de código, scaffolding, refactors e testes.
- **Workflow**: backlog em issues → branches por feature → PR com checklist → revisão (humana + CodeX) → merge.
- **Automação**: GitHub Actions para lint/test/build, releases semânticas e changelog automático.
- **Padrões**: monorepo (apps/services/packages) ou multi-repo; convenções de commit; versionamento semântico.
- **Infra de Dev**: templates de projeto, containers de dev, seeds de dados e mocks.

---

## 10. Riscos e Mitigações (resumo)
- **Mudanças de política do WhatsApp** → abstrair provedores; monitorar limites; fallback de envio.
- **Dependência de IA** → camadas de regras/DSL garantem comportamento determinístico em fluxos críticos.
- **Privacidade/segurança** → minimização de dados, segregação por tenant, auditoria e revisão periódica.

---

## 11. Critérios de Aceite do MVP
- Fluxos prontos: saudação, qualificação, catálogo, orçamento, checkout com link de pagamento.
- Painel simples com métricas (conversas/dia, taxa de resposta, conversões, top produtos).
- Implantação em ao menos **2 empreendimentos distintos** apenas por configuração.

---

## 12. Glossário
- **CodeX**: Integração do ChatGPT com GitHub para co-desenho, geração e revisão de código via issues/PRs.
- **DSL de fluxo**: linguagem declarativa para montar jornadas (blocos/condições/ações) sem código.
- **Multi-tenant**: arquitetura que isola dados/configuração por cliente em uma mesma base de serviços.

---

## 13. Próximos Passos
1. Criar repositório e publicar este **VISION.md**.
2. Abrir issues para **Fase 0** (skeleton, CI, templates, scaffolds).
3. Selecionar conector WhatsApp inicial e mapear limites/tarifas.
4. Desenhar DSL mínima de fluxo e catálogo v1.

