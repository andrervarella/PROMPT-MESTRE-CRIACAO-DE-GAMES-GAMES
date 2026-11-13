# MÓDULO — Níveis de modelo e agentes em paralelo

Leia quando for distribuir trabalho entre modelos ou agentes. Referência: seções 2 e 9 do `PROMPT_MESTRE.md`. Ordem de serviço e branches: `COMUNICACAO_CLAUDE_CODEX.md`.

## Níveis (por função, não por nome — nomes mudam)

| Nível | Para quê | Quando |
|---|---|---|
| CRIATIVO (modelo mais forte) | conceito, história, hook, bíblia visual, especificação de assets, direção de áudio e trailer, arquitetura | início do jogo, mudança grande de design, lapidação final |
| EXECUÇÃO (intermediário/barato) | código, integração, ajustes, bugs, deploy, montar assets a partir de especificação | todo o resto |

Regras:

1. O criativo entrega **arquivos de especificação** (`docs/GDD.md`, `docs/BIBLIA_VISUAL.md`, `docs/MANIFESTO_ASSETS.md`). A execução só consome.
2. Escale da execução para o criativo apenas em decisão de arquitetura/design ou após **2 tentativas que não passaram no critério de pronto** da ordem de serviço.
3. Em chat sem troca automática de modelo, a IA declara em 1 linha o nível que a tarefa pede; o dono troca, ou a tarefa é delegada por subagente quando possível.
4. Não use o modelo mais caro para tarefa simples.

## Mapeamento atual (preenchido pelo dono; revisar quando os modelos mudarem)

| Nível | Claude | Codex | ChatGPT |
|---|---|---|---|
| CRIATIVO | Fable | (preencher) | (preencher) |
| EXECUÇÃO | Sonnet | (preencher) | (preencher) |

No Claude, Opus não é usado por padrão (economia de crédito). Campos "(preencher)" ficam em branco de propósito: não inventar nomes de modelos de outros fornecedores.

## Agentes em paralelo

**Quando vale:** partes **independentes** (arte, música, SFX, vídeo, código) e **contratos travados** (manifesto de assets; lista de eventos sonoros).
**Quando não vale:** tarefas pequenas ou acopladas.

**Limites padrão:**
- 3 a 4 agentes simultâneos; mais só com aprovação do dono (custo e conflito crescem juntos).
- Teto de custo por agente, combinado antes.
- Uma pasta/branch por agente.
- Um único **integrador** junta tudo (modo colaborativo, seção 3 de COMUNICACAO).
- Cada agente reporta com os rótulos do Contrato de Evidência.
