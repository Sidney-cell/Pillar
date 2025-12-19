Pillar — Webhooks

Esta documentação descreve como os Webhooks do Pillar funcionam, como validar eventos e boas práticas para uso em produção.

Os Webhooks são o principal mecanismo de entrega event‑driven do Pillar.


---

🧠 Conceito

Um webhook é uma requisição HTTP POST enviada pelo Pillar sempre que um evento relevante ocorre on‑chain.

O cliente fornece uma URL, e o Pillar entrega eventos assinados.


---

🔔 Tipos de eventos (v1)

transfer

mint

swap


Cada evento possui schema versionado.


---

📩 Requisição HTTP

Método

POST

Headers

Content-Type: application/json
X-Pillar-Signature: sha256=HEX
X-Pillar-Event: swap
X-Pillar-Chain-Id: 1


---

📦 Payload (exemplo)

{
  "id": "evt_01HXYZ",
  "event": "swap",
  "chain_id": 1,
  "tx_hash": "0xabc...",
  "block_number": 19234567,
  "contract": "0x123...",
  "data": {
    "from": "0xaaa...",
    "to": "0xbbb...",
    "amount": "100"
  },
  "timestamp": 1710000000,
  "schema_version": "1.0"
}


---

🔐 Assinatura HMAC (OBRIGATÓRIO)

O Pillar assina todos os webhooks usando HMAC‑SHA256.

Como validar

1. Leia o corpo bruto da requisição


2. Gere o HMAC usando o segredo compartilhado


3. Compare com o header X-Pillar-Signature



Pseudocódigo

expected = hmac_sha256(secret, raw_body)
assert timing_safe_equal(expected, signature)

⚠️ Nunca confie em payload sem validação.


---

🔁 Retries e Garantia de Entrega

Timeout padrão: 5s

Até 5 tentativas

Backoff progressivo


Códigos considerados sucesso:

200

201

204



---

⏱️ Idempotência

Eventos podem ser reenviados.

Recomenda‑se:

Usar id como chave única

Ignorar duplicados



---

🛡️ Boas práticas

Responder rápido (<200ms)

Processar de forma assíncrona

Nunca bloquear o endpoint

Logar falhas de validação



---

🚧 Limites

Payload máximo: 256KB

Rate limitado por API Key



---

🧪 Testes

Use um endpoint local com ferramentas como:

ngrok

localtunnel



---

> Webhooks são contratos. Trate‑os como parte crítica da sua infra.
