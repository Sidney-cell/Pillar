Pillar — Definição do Ambiente de Produção

Este documento define como o ambiente de produção do Pillar deve ser organizado, separado e operado.

O objetivo é evitar improviso, reduzir risco e permitir crescimento controlado.


---

🎯 Princípios

Separação clara entre ambientes

Nenhuma configuração sensível em repositório público

Tudo reproduzível via Docker



---

🧱 Ambientes definidos

1. Local (dev)

Uso:

Desenvolvimento

Testes rápidos


Características:

Docker Compose local

.env local

Sem dados reais



---

2. Staging (opcional, mas recomendado)

Uso:

Testar versões antes do prod

Validar migrações


Características:

Infra parecida com produção

API Keys separadas

Webhooks de teste



---

3. Produção (prod)

Uso:

Usuários reais

Early Access


Características obrigatórias:

Domínio próprio

HTTPS

Secrets fora do Git

Logs persistentes



---

🌍 Domínios sugeridos

API: api.pillar.network

Webhooks: hooks.pillar.network

Docs: docs.pillar.network


(Staging)

staging-api.pillar.network



---

🔐 Gestão de Segredos

Nunca versionar:

API Keys

Secrets HMAC

Tokens


Usar:

.env no servidor

Variáveis de ambiente do Docker



---

🧠 Componentes em Produção

Ingestor (listener)

Processor / Normalizer

Dispatcher (webhooks)

API pública

Banco de dados

Observabilidade



---

🧰 Infraestrutura base

Recomendado:

VPS dedicada (Hetzner / similar)

Docker + Docker Compose

Reverse Proxy (Traefik ou Nginx)



---

📊 Observabilidade mínima

Obrigatório:

Logs persistentes

Métricas expostas

Alertas básicos



---

🛑 Regras de Produção

Deploy só via Docker

Nenhum hotfix manual

Mudanças documentadas



---

> Produção não é lugar para testes. É lugar para previsibilidade.
