# MÓDULO — Níveis de modelo e agentes em paralelo

Leia quando for distribuir trabalho entre modelos ou agentes. Referência: seções 2 e 9 do `PROMPT_MESTRE.md`. Ordem de serviço e branches: `COMUNICACAO_CLAUDE_CODEX.md`.

## Níveis (por função, não por nome — nomes mudam)

| Nível | Para quê | Quando |
|---|---|---|
| CRIATIVO (modelo mais forte) | conceito, história, hook, pacote de aprovação visual, bíblia visual, especificação de assets, direção de áudio e trailer, arquitetura | início do jogo, mudança grande de design, lapidação final |
| EXECUÇÃO (intermediário/barato) | código, integração, ajustes, bugs, deploy, montar assets a partir de especificação | todo o resto |

Regras:

1. O criativo entrega **arquivos de especificação** (`docs/GDD.md`, `docs/BIBLIA_VISUAL.md`, `docs/MANIFESTO_ASSETS.md`). A execução só consome.
2. Escale da execução para o criativo apenas em decisão de arquitetura/design ou após **2 tentativas que não passaram no critério de pronto** da ordem de serviço.
3. Em chat sem troca automática de modelo, a IA declara em 1 linha o nível que a tarefa pede; o dono troca, ou a tarefa é delegada por subagente quando possível.
4. Não use o modelo mais caro para tarefa simples (exceto onde o dono definiu o contrário, ver mapeamento abaixo).

## Mapeamento atual (definido pelo dono; revisar quando os modelos mudarem)

| Nível | Claude | Codex | ChatGPT |
|---|---|---|---|
| CRIATIVO | Fable | modelo mais forte disponível no plano | (preencher) |
| EXECUÇÃO | Sonnet | modelo mais forte disponível no plano (escolha do dono: usa sempre o máximo) | (preencher) |

No Claude, Opus não é usado por padrão (economia de crédito). No Codex, o dono usa sempre o modelo mais inteligente (o que mais gasta crédito); o **nome exato não está registrado** de propósito, porque nomes mudam e não devem ser inventados. Campos "(preencher)" ficam em branco de propósito.

Observação de custo: o modelo máximo no Codex consome o plano mais rápido. Se o limite apertar, o dono pode trocar para um modelo menor nas tarefas de execução simples; isso não exige mudar o método.

## Planos do dono (contexto de custo)

O dono usa planos **iniciais/baratos**: Claude (~R$100/mês) e Codex (~R$100/mês). Créditos e limites de uso são finitos. Consequências:

1. **Gaste o forte só onde rende:** conceito, pacote visual e bíblia visual. No Claude, todo o resto no modelo de execução.
2. **Aprovar antes de produzir** (Pacote de Aprovação Visual) é também economia: evita refazer lotes inteiros de sprites.
3. **Reparta o trabalho entre os dois planos:** se um chegar perto do limite, a tarefa passa para a outra IA via ordem de serviço, sem esperar.
4. Antes de gerar em lote (imagens, áudio, vídeo), mostre a **estimativa de custo/uso** e peça confirmação.
5. Os limites dos planos mudam; confira no próprio serviço, não neste documento.

## Agentes em paralelo

**Quando vale:** partes **independentes** (arte, música, SFX, vídeo, código) e **contratos travados** (manifesto de assets; lista de eventos sonoros).
**Quando não vale:** tarefas pequenas ou acopladas.

**Limites padrão (ajustados aos planos iniciais):**
- **2 a 3 agentes simultâneos** como padrão; 4 ou mais só com aprovação do dono (custo e conflito crescem juntos, e cada agente consome os mesmos créditos do plano).
- Teto de custo por agente, combinado antes.
- Uma pasta/branch por agente.
- Um único **integrador** junta tudo (modo colaborativo, seção 3 de COMUNICACAO).
- Cada agente reporta com os rótulos do Contrato de Evidência.
