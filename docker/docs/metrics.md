Pillar — Métricas Mínimas (v1)

Este documento define as métricas mínimas obrigatórias para operar o Pillar com segurança durante o Early Access.

O objetivo não é otimização máxima, e sim visibilidade, estabilidade e confiança.


---

🎯 Princípios

Poucas métricas, mas acionáveis

Foco em saúde do pipeline

Indicadores que mostram falhas rapidamente



---

🔁 Pipeline de Ingestão

1. Eventos ingeridos por minuto

Métrica: events_ingested_total

Tipo: Counter

Alerta:

Queda súbita (>50%)



📌 Indica problemas no node ou no listener.


---

2. Lag de blocos

Métrica: block_lag

Tipo: Gauge

Definição:

Bloco atual da rede − último bloco processado



Alerta:

> 10 blocos por mais de 2 minutos





---

📦 Normalização / Schema

3. Eventos inválidos

Métrica: events_invalid_total

Tipo: Counter


Alerta:

Qualquer aumento contínuo


📌 Indica quebra de schema ou bug de parser.


---

📤 Entrega (Webhooks)

4. Taxa de sucesso de entrega

Métrica: webhook_delivery_success_ratio

Tipo: Ratio


Alerta:

< 95%



---

5. Latência de entrega

Métrica: webhook_delivery_latency_ms

Tipo: Histogram


Alvo inicial:

p95 < 2000ms



---

6. Retries

Métrica: webhook_retries_total

Tipo: Counter


📌 Aumento indica instabilidade do consumidor.


---

🔐 Segurança

7. Assinaturas inválidas

Métrica: webhook_invalid_signature_total


📌 Pode indicar erro de configuração ou tentativa maliciosa.


---

🧑‍💻 Uso

8. API Keys ativas

Métrica: active_api_keys

Tipo: Gauge



---

9. Eventos por API Key

Métrica: events_by_api_key


📌 Identifica abuso ou usuários críticos.


---

🧠 Saúde Geral (Resumo)

Dashboard mínimo deve responder:

O Pillar está ingerindo?

Está atrasado?

Está entregando?

Está falhando para quem?



---

🚧 Fora de escopo (por enquanto)

Custo por evento

Billing

SLA formal



---

> Métricas não são para gráficos bonitos. São para evitar surpresas.
