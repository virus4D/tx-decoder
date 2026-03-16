# tx-decoder 🔍

> cola um hash — entende o que realmente aconteceu.

Ferramenta que decodifica qualquer transação na rede **Base** e explica em linguagem simples o que aconteceu, quanto custou e o que observar — combinando dados diretos do RPC com análise de IA via Groq.

---

## o que faz

```
① TX DATA    → tipo, de/para, valor ETH + USD, status (sucesso/falhou)
② CONTRATO   → detecta swap, transfer, approval, mint — verificado ou não
③ GAS USD    → gas usado, gas price em Gwei, custo total em USD
④ EXPLICAR   → agente IA explica em português o que essa tx fez
```

---

## demo

🔗 **[virus4d.github.io/tx-decoder](https://virus4d.github.io/tx-decoder)**

---

## como usar

1. Cola o hash de qualquer transação na rede Base (`0x...`)
2. Clica **DECODIFICAR**
3. Lê o que o agente explica

exemplo de hashes para testar:
- qualquer tx do seu histórico no [basescan.org](https://basescan.org)
- copie o hash de uma tx recente da sua wallet MetaMask

---

## tipos de transação detectados

```
TRANSFER        → envio de ETH simples entre wallets
TOKEN TRANSFER  → envio de token ERC-20 (USDC, DAI, etc.)
SWAP            → troca de tokens (Uniswap, Aerodrome, etc.)
APPROVAL        → autorização de gasto para um contrato
DEPOSIT         → depósito em protocolo DeFi
WITHDRAW        → saque de protocolo DeFi
MINT            → criação de tokens ou NFTs
CONTRACT CALL   → qualquer outra interação com contrato
```

---

## stack

```
Base RPC         → eth_getTransactionByHash + eth_getTransactionReceipt (sem CORS)
Etherscan API V2 → verificação de contrato + nome
CoinGecko API    → preço ETH em USD para calcular gas
Groq LLM         → llama-3.3-70b explica a tx em português
Vanilla JS       → sem frameworks, sem dependências
```

---

## o que aprendi construindo isso

- `eth_getTransactionByHash` e `eth_getTransactionReceipt` via RPC — sem CORS, direto no browser
- function signatures dos 4 bytes iniciais do input data identificam o tipo de chamada
- gas cost em USD = `gasUsed × gasPrice × ETH_price` — simples mas útil
- Groq com temperatura baixa (0.5) é mais preciso para análise técnica

---

## projetos relacionados

| tool | descrição | link |
|------|-----------|------|
| 🔍 tx-decoder | decodifica transações on-chain | você está aqui |
| 🤖 sentinel-agent | monitora wallets e alerta em tempo real | [ver repo](https://github.com/virus4D/sentinel-agent) |
| 📊 token-scanner | analisa tokens ERC-20 on-chain | [ver repo](https://github.com/virus4D/token-scanner) |
| 🔎 wallet-lens | scan de transações ETH on-chain | [ver repo](https://github.com/virus4D/wallet-lens) |
| 🤖 defi-agent-v0 | agente IA que analisa wallets na Base | [ver repo](https://github.com/virus4D/defi-agent-v0) |

---

<div align="center">

construindo em público · errando em público · chegando lá

[![X](https://img.shields.io/badge/@Virus__4D-000000?style=flat-square&logo=x&logoColor=cc0000)](https://x.com/Virus_4D)
[![GitHub](https://img.shields.io/badge/virus4D-000000?style=flat-square&logo=github&logoColor=cc0000)](https://github.com/virus4D)

</div>
