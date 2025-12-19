Pillar — Arquitetura (Visão Geral)

Este documento descreve a arquitetura do Pillar em alto nível, com foco em confiabilidade, isolamento e operação em produção.

O Pillar é projetado como infraestrutura de dados e eventos, não como um explorer ou aplicação de frontend.


---

🎯 Objetivos de Arquitetura

Confiabilidade em produção

Baixo acoplamento entre componentes

Recuperação automática de falhas

Escalabilidade horizontal

Segurança por padrão



---

🧱 Componentes Principais

1. Ingestão On-chain

Responsável por:

Conectar ao node RPC (HTTP + WS)

Ler blocos e logs

Detectar eventos relevantes

Lidar com reorgs


Características:

Stateless

Resiliente a falhas de RPC

Controlado por confirmações de bloco



---

2. Normalização

Responsável por:

Converter eventos brutos em payloads padronizados

Garantir consistência entre chains

Versionar schemas de eventos


Benefícios:

Payload previsível para clientes

Evolução sem quebra



---

3. Persistência (Data Layer)

Responsável por:

Armazenar eventos processados

Garantir idempotência

Permitir reprocessamento


Tecnologias:

PostgreSQL (v1)

Volume persistente



---

4. API Layer

Responsável por:

Expor dados via HTTP

Autenticação por API Key

Rate limiting

Auditoria básica


Isolado do pipeline de ingestão.


---

5. Webhook Engine

Responsável por:

Entrega de eventos em tempo real

Assinatura HMAC

Retry com backoff

Garantia de entrega


Projetado para tolerar falhas do cliente.


---

6. Observabilidade

Responsável por:

Métricas (latência, falhas, throughput)

Logs estruturados

Saúde do sistema


Ferramentas:

Prometheus

Grafana



---

🔐 Segurança

Segredos via variáveis de ambiente

Nenhum segredo em código

API Keys isoladas por cliente

Rate limit por chave



---

🌐 Fluxo de Dados

Blockchain
   ↓
Ingestão
   ↓
Normalização
   ↓
Persistência
   ↓
Webhook / API


---

🧠 Princípios de Design

Fail fast

Backpressure

Idempotência

Observabilidade antes de features



---

🚧 Limites conhecidos (v1)

Single region

PostgreSQL único

Escala vertical prioritária


Esses limites são intencionais no Early Access.


---

🗺️ Evolução Planejada

Múltiplas chains

Streams WS

Data Lake

Escala multi-region



---

> Pillar é projetado para ser boring. Infra previsível é infra confiável.
