# MÓDULO — Níveis de modelo e agentes em paralelo

Leia quando for distribuir trabalho entre modelos ou agentes. Referência: seções 2 e 9 do `PROMPT_MESTRE.md`.

## Níveis (por função, não por nome — nomes mudam)

| Nível | Para quê | Quando |
|---|---|---|
| CRIATIVO (modelo mais forte) | conceito, história, hook, bíblia visual, especificação de assets, direção de áudio e do trailer, arquitetura | início do jogo, mudança grande de design, lapidação final |
| EXECUÇÃO (intermediário/barato) | código, integração, ajustes, bugs, deploy, montar assets a partir de especificação | todo o resto |

Regras:

1. O nível criativo entrega **arquivos de especificação** (ex.: `docs/DESIGN.md`, `BIBLIA_VISUAL.md`, manifesto de assets). O nível de execução só consome.
2. Escale da execução para o criativo apenas em decisão de arquitetura/design ou após **2 tentativas falhas**.
3. Em chat sem troca automática de modelo, a IA declara em 1 linha o nível que a tarefa pede.
4. Não use o modelo mais caro para tarefas simples.

## Mapeamento atual (preenchido pelo dono; revisar quando os modelos mudarem)

| Nível | Claude | Codex | ChatGPT |
|---|---|---|---|
| CRIATIVO | Fable | (preencher) | (preencher) |
| EXECUÇÃO | Sonnet | (preencher) | (preencher) |

Obs.: no Claude, o modelo Opus não é usado por padrão (economia de crédito). Os campos "(preencher)" ficam em branco de propósito: não inventar nomes de modelos de outros fornecedores.

## Agentes em paralelo

**Quando vale:** partes **independentes** (arte, música, SFX, vídeo, código) e **contratos travados** (manifesto de assets com nomes/tamanhos/pivôs/FPS; lista de eventos sonoros).

**Quando não vale:** tarefas pequenas ou acopladas (uma mexe no que a outra precisa).

**Limites padrão:**
- 3 a 4 agentes simultâneos. Mais que isso só com aprovação do dono, porque custo e conflito crescem junto.
- Um teto de custo por agente, combinado antes.
- Uma pasta/branch por agente.
- Um único **integrador** junta tudo e atualiza o ESTADO_ATUAL.
- Cada agente reporta com o Contrato de Evidência (EXECUTADO / SÓ LIDO / NÃO VERIFICADO).
