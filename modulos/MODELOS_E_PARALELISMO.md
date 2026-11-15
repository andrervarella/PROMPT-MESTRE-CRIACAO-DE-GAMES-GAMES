# MÓDULO — Níveis de modelo e agentes em paralelo

Leia quando for distribuir trabalho entre modelos ou agentes. Referência: seções 2 e 9 do `PROMPT_MESTRE.md`. Ordem de serviço e branches: `COMUNICACAO_CLAUDE_CODEX.md`.

## Divisão padrão de trabalho (definida pelo dono em 2026-11-14)

Ponto de partida, não trava: qualquer IA pode sugerir outra divisão (motivo, 2 opções, recomendação).

| Etapa | Quem |
|---|---|
| Conceito, história, emoção do jogo, lista do jogo completo (discutidos com o dono) | **Claude** (nível CRIATIVO). Segunda opinião do ChatGPT é opcional. |
| Especificação de cada imagem, cutscene e vídeo (o que gerar, tamanho, poses, estados, paleta, referência fixa, roteiro) | **Claude**, no `docs/MANIFESTO_ASSETS.md` e na bíblia visual |
| Imagens de amostra (Portão V), lote-piloto, sprites, cenários, mapa, tela inicial, UI | **ChatGPT / Codex** (gerador de imagens da OpenAI, PixelLab). Alternativa: **Fenaky** (imagens e pixel art) |
| Cutscenes entre fases (CGs) e vídeos promocionais/trailer | **Fenaky** (vídeo), a partir do roteiro do Claude e das imagens aprovadas como referência |
| Música | **Fenaky** (Fenaky Music) ou outra ferramenta disponível |
| Aprovação das imagens, cutscenes e músicas | **Dono** |
| Código do jogo, integração (inclui tocar as cutscenes), testes, link jogável | **Claude** |
| Revisão do código | **Codex** (quem não escreveu revisa) |
| Revisão dos sprites e cutscenes (personagem mudou? segue o manifesto?) | **Claude** |
| Efeitos sonoros e vozes no final (ElevenLabs) | Quem tiver o acesso |

**Tudo passa pelo Git.** Imagem, vídeo ou música que ficar só num chat ou num link não existe para a outra IA. Os arquivos são salvos no repositório do jogo (pelo Codex, por quem gerou ou pelo dono), com nome e caminho do manifesto e a proveniência (ferramenta, prompt, data).

### Fenaky (conectado ao Claude e ao Codex; plano pago do dono)
- Usar para: **cutscenes entre fases**, **vídeos promocionais/trailer**, **música**, e imagens/pixel art quando fizer sentido.
- **Antes de gerar, mostrar o custo** (cotação da própria ferramenta) e pedir o "ok" do dono.
- **Links de resultado expiram** (o Fenaky informa validade de 24 h): baixar e salvar no repositório logo depois de gerar.
- Cutscenes usam o **personagem aprovado como referência** de imagem, para manter a identidade; seguem o mesmo ciclo de aprovação (uma por vez, "gostei"/"ajustar").
- Cutscene é curta e pulável; o jogo não pode depender dela para funcionar.

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

O dono usa planos **iniciais/baratos**: Claude (~R$100/mês) e Codex (~R$100/mês), e pretende pagar o Fenaky. Créditos e limites de uso são finitos. Consequências:

1. **Gaste o forte só onde rende:** conceito, pacote visual e bíblia visual. No Claude, todo o resto no modelo de execução.
2. **Aprovar antes de produzir** (Pacote de Aprovação Visual) é também economia: evita refazer lotes inteiros de sprites e vídeos.
3. **Reparta o trabalho entre os planos:** se um chegar perto do limite, a tarefa passa para a outra IA via ordem de serviço, sem esperar.
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
