# MANIFESTO DE ASSETS — [NOME DO JOGO]

**Ponte entre Google Drive e GitHub conforme V4.5.** Não publicar link do Drive; usar apenas caminhos lógicos. O GitHub tem os arquivos realmente usados pelo jogo, e o Drive, suas fontes/originais. Não duplicar tudo.

| ID | Versão | Status | Arquivo-fonte (Drive, caminho lógico) | Cópia sem perda (Drive, se houver) | Arquivo runtime (GitHub, se houver) | SHA-256 original | SHA-256 cópia lossless | SHA-256 runtime | Pixels idênticos? (script/data) | Quadro/estado/FPS/pivô | Proveniência / aprovação |
|---|---|---|---|---|---|---|---|---|---|---|---|
| player_idle | v001 | provisório | GAMES_IA/[NOME DO JOGO]/02_SPRITES_ANIMACOES/player_idle_fonte.png | — | assets/player/idle.png | pendente | — | pendente | não aplicável | 64×64 / idle / 8 / pés | [ferramenta/prompt/seed/data] |

**Regras do inventário:**
- Registrar a existência e o hash de **cada representação efetivamente criada**; não inferir hashes nem presença. Sem arquivo de runtime, deixar seu caminho como `—`.
- Se houver PNG recomprimido ou WebP lossless, validar **dimensões e RGBA pixel a pixel** com script; registrar os **dois hashes** de origem e cópia, mesmo quando os pixels forem iguais. Incluir data/comando/resultado da verificação.
- Original aprovado não é substituído ou sobrescrito, e concept/crop não vira automaticamente sprite final. Arquivos finais otimizados de runtime entram no GitHub para o jogo rodar sem Drive.
- Não enviar imagens divididas em partes soltas ao Drive; se falhar, status = `pendente`. ZIP cujo conteúdo já esteja inventariado no acervo dispensa reenvio.
- Registrar autoria/licença, aprovação e versões rejeitadas quando existirem. Asset sem proveniência = licença não confirmada.

## Áudio
| ID / evento | Fonte (Drive) | Runtime (GitHub) | Versão / status | SHA-256 fonte | SHA-256 runtime | Formato / loop | Proveniência/licença |
|---|---|---|---|---|---|---|---|
