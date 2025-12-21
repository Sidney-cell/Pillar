# Pillar — Use Case Oficial

## Infraestrutura de Eventos On-chain para Agentes de IA

Este documento descreve um **caso de uso oficial e vendável** do Pillar para **empresas de IA, agentes autônomos e sistemas automatizados**.

O objetivo é mostrar claramente **onde o Pillar se encaixa**, **o valor entregue** e **como monetizar**.

---

## 🧠 Problema das Empresas de IA

Empresas que constroem agentes de IA enfrentam desafios ao integrar blockchain:

* Dados on-chain são ruidosos e difíceis de interpretar
* RPCs são instáveis e caros
* Logs brutos não são consumíveis por modelos
* Reorgs quebram pipelines

Esses problemas tornam a blockchain **hostil para IA em produção**.

---

## ✅ Solução Pillar

O Pillar atua como uma **camada intermediária inteligente** entre blockchain e IA:

```
Blockchain → Pillar → Eventos Normalizados → IA / Agente
```

O agente recebe **JSON confiável**, versionado e em tempo quase real.

---

## 🤖 Caso de Uso: Agente de IA Reativo

### Exemplo

Um agente de IA monitora swaps relevantes e reage automaticamente.

Fluxo:

1. Swap ocorre on-chain
2. Pillar detecta e normaliza o evento
3. Pillar envia webhook
4. Agente de IA processa o evento
5. Ação automática é executada

---

## 📦 Evento Consumido pelo Agente

```json
{
  "event": "swap",
  "chain_id": 1,
  "contract": "0x123...",
  "data": {
    "amount": "250000",
    "token": "USDC"
  },
  "confidence": "high",
  "timestamp": 1710000000
}
```

👉 O agente **não interpreta logs**, apenas reage.

---

## 🧠 Benefícios para IA

* Dados previsíveis
* Baixa latência
* Sem necessidade de rodar node
* Sem dependência de ABI
* Pronto para pipelines de ML

---

## 🧩 Onde o Pillar agrega valor único

* Normalização cross-chain
* Deduplicação
* Garantia de entrega
* Observabilidade

IA consome **sinais**, não dados crus.

---

## 💰 Modelo de Monetização (IA)

### Planos sugeridos

**AI Starter**

* Até X eventos/mês
* Latência padrão

**AI Pro**

* Eventos ilimitados
* Prioridade de entrega
* Webhooks dedicados

**Enterprise / Partnership**

* SLA
* Eventos customizados
* White-label

---

## 🤝 Modelo de Parceria

Para empresas de IA:

* Pillar como backend invisível
* Marca do parceiro
* Faturamento por volume

👉 Receita recorrente.

---

## 🎯 Perfil de Cliente Ideal

* Startups de agentes de IA
* Plataformas de automação
* Fundos quantitativos
* Ferramentas de monitoramento

---

## 🚀 Como vender o Pillar para IA

Pitch simples:

> We deliver clean, real-time on-chain events designed for AI agents.
> No nodes. No raw logs. Just signals.

---

## 🏁 Conclusão

O Pillar não compete com modelos de IA.

Ele **alimenta** esses modelos com dados on-chain confiáveis.

> Infra invisível é infra vencedora.
