# CHANGELOG

Todas as mudanças notáveis neste projeto serão documentadas aqui.  
Este formato segue as recomendações do [Keep a Changelog](https://keepachangelog.com/pt-BR/1.1.0/) e este projeto adota a [Semantic Versioning](https://semver.org/lang/pt-BR/).

---

## [Unreleased]
### Adicionado
- Estrutura inicial do repositório com **CodeX** (VISION.md, ROADMAP.md, CONTRIBUTING.md).
- Documento de visão do projeto.
- Roadmap detalhado com fases de desenvolvimento.
- Guia de contribuição para colaboradores.

### Planejado
- Configuração inicial de **CI/CD** no GitHub Actions.
- Criação do esqueleto do backend (gateway WhatsApp, motor de conversa, catálogo, checkout).
- Template para *issues* e *pull requests*.

---

## [0.1.0] — Previsto para Outubro 2025
### Adicionado
- Integração inicial com WhatsApp Business API (ou conector alternativo, ex.: Z-API).  
- Cadastro e listagem de produtos/serviços em catálogo dinâmico.  
- Respostas automáticas baseadas em regras (FAQ, saudações).  
- Fluxo básico de qualificação de leads (nome, interesse, orçamento, localização).  
- Geração de links/QR Code para pagamentos via Pix.  
- Painel administrativo inicial com visão de conversas, leads e pedidos.  
- Persistência de dados em banco relacional.  

### Alterado
- Ajustes no pipeline de CI/CD para deploy contínuo em ambiente de staging.  

### Critérios de Aceite
- O robô deve responder automaticamente a clientes no WhatsApp.  
- Catálogo navegável com pelo menos 10 produtos cadastrados.  
- Capacidade de fechar vendas simples pelo WhatsApp.  
- Disponibilidade mínima de 95 %.  

---

## [1.0.0] — Previsto para Março 2026
### Adicionado
- Integração com modelo de IA (GPT via CodeX) para interpretação de linguagem natural.  
- Aprendizado contínuo: ajuste automático das respostas baseado no histórico de conversas.  
- Mensagens personalizadas por segmento, cliente e idioma (pt-BR, en-US, es-ES).  
- Dashboard aprimorado com filtros, relatórios exportáveis e análise de conversão.  

### Critérios de Aceite
- Aumento de 30 % na taxa de conversão em relação ao MVP.  
- Robô capaz de lidar com mensagens abertas e consultas complexas.  
- Suporte a mais de 1 000 conversas simultâneas sem degradação significativa.  

---

## [2.0.0] — Previsto para Junho 2026
### Adicionado
- Suporte **multiempresa (multi-tenant)** com catálogos independentes.  
- Gestão de usuários e permissões (admin, gerente, vendedor, suporte).  
- Balanceamento de carga e autoscaling em produção.  
- Estratégia de backup e recuperação de desastres implementada.  

### Critérios de Aceite
- Plataforma em uso por pelo menos 5 empresas diferentes.  
- Tempo médio de resposta < 2 segundos em picos de uso.  

---

## [2.5.0] — Previsto para Setembro 2026
### Adicionado
- Integrações com CRMs (Salesforce, HubSpot, RD Station).  
- Integrações com e-commerce (Shopify, WooCommerce, Magento).  
- Conector de marketplace (ex.: Mercado Livre, Shopee).  
- API pública e endpoints de webhook para integrações customizadas.  

### Critérios de Aceite
- Pelo menos 2 integrações de CRM/ERP e 1 integração de e-commerce disponíveis.  
- Documentação pública da API pronta.  

---

## [3.0.0] — Previsto para Dezembro 2026
### Adicionado
- Marketplace de plug-ins/extensões da comunidade.  
- Canal oficial de suporte e comunidade (Discord/Slack).  
- Programa de parceiros e desenvolvedores externos.  
- Melhorias contínuas em segurança, monitoramento e escalabilidade.  

### Critérios de Aceite
- Comunidade ativa com contribuidores externos.  
- Reconhecimento de mercado como solução de referência em automação de vendas via WhatsApp.  

---

