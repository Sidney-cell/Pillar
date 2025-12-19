Exemplo — Discord Bot com Pillar (Webhooks)

Este exemplo mostra como usar o Pillar na prática, recebendo eventos on-chain e enviando notificações para um canal do Discord.

O objetivo é demonstrar uso real, não performance máxima.


---

🧠 Visão Geral

Fluxo:

Blockchain → Pillar → Webhook → Bot Discord

O Pillar envia eventos (Mint / Swap / Transfer) para um endpoint HTTP. O bot recebe o evento e publica a mensagem no Discord.


---

📦 Pré-requisitos

Conta Discord

Criar um Discord Bot

Token do Bot

URL de Webhook do Discord ou permissões de envio de mensagem

API Key do Pillar (Early Access)



---

🧱 Estrutura do exemplo

examples/discord-bot/
├── README.md
├── index.js
├── package.json
└── .env.example


---

🔑 Variáveis de ambiente (.env.example)

DISCORD_BOT_TOKEN=CHANGE_ME
DISCORD_CHANNEL_ID=CHANGE_ME
PILLAR_WEBHOOK_SECRET=CHANGE_ME

⚠️ Nunca commite valores reais.


---

📩 Payload esperado do Pillar (exemplo)

{
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
  "timestamp": 1710000000
}


---

🧪 Lógica do bot (alto nível)

1. Recebe POST do Pillar


2. Valida assinatura HMAC


3. Formata mensagem


4. Envia para o Discord




---

📣 Exemplo de mensagem no Discord

🟢 Swap detectado
Chain: Ethereum
Contrato: 0x123...
Tx: 0xabc...
Amount: 100


---

🛡️ Segurança

Validar HMAC em todas as requisições

Ignorar payloads inválidos

Nunca expor token do bot



---

🎯 Por que esse exemplo existe

Mostrar uso real do Pillar

Facilitar onboarding

Servir como base para produção



---

> Este exemplo é propositalmente simples. Infra séria começa com casos claros.
