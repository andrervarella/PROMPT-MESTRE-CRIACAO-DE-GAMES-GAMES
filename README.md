# PROMPT MESTRE UNIVERSAL — CRIAÇÃO DE GAMES COM IA

**Versão vigente: V4.0** · Metodologia compartilhada para ChatGPT, Claude, Codex e outras IAs.

Este repositório público contém **o método universal para criar e aprimorar jogos com IA**, independentemente de gênero, engine, universo ou plataforma. **Não** é o repositório do código de um jogo específico.

## Comece aqui

1. Leia o [PROMPT_MESTRE.md](PROMPT_MESTRE.md) (núcleo curto). Abra os [módulos](modulos/) só quando a tarefa pedir.
2. Agente de programação: veja também [AGENTS.md](AGENTS.md) (canônico). Claude Code: [CLAUDE.md](CLAUDE.md) (importa o AGENTS.md).
3. Para **cada jogo**, mantenha código e estado no **repositório do jogo**. Copie/adapte [MODELO_PROJETO/](MODELO_PROJETO/).
4. Ao iniciar a sessão, confira **repositório, branch, commit, ESTADO_ATUAL, DECISOES, HANDOFF e TAREFAS** do jogo. Ao encerrar, atualize esses documentos e faça commit/PR se autorizado.
5. Informe o hash do commit ou a URL do PR para comprovar a sincronização.

## Fluxo resumido

Conceito → decisão técnica → **Pacote de Aprovação Visual (Portão V)** → **prova do core loop (Portão 1)** → GDD → produção completa de assets → **vertical slice (Portão 2)** → QA/playtest → **Concluído (Portão 3)**.

## Arquivos

| Arquivo | Função |
|---|---|
| [PROMPT_MESTRE.md](PROMPT_MESTRE.md) | Método canônico (V4.0), nome estável |
| [modulos/](modulos/) | Pacote de aprovação visual, modelos e paralelismo, comunicação Claude↔Codex, playtest e qualidade, arte/pixel art mobile, áudio, game feel, vídeo/trailer, comercial, skills externas, fontes |
| [AGENTS.md](AGENTS.md) | Regras canônicas para todos os agentes |
| [CLAUDE.md](CLAUDE.md) | Fino: importa o AGENTS.md e traz só o específico do Claude |
| [REGISTRO_DE_PROJETOS.md](REGISTRO_DE_PROJETOS.md) | Índice de repositórios de jogos |
| [CHANGELOG.md](CHANGELOG.md) | Histórico das versões |
| [MODELO_PROJETO/](MODELO_PROJETO/) | Templates para cada jogo |

Histórico preservado: [V3.1](PROMPT_MESTRE_UNIVERSAL_GAMES_IA_V3_1.md) e [V3.0](PROMPT_MESTRE_UNIVERSAL_GAMES_IA_V3.md).

## Como pedir a outra IA

> Consulte o repositório público `https://github.com/andrervarella/PROMPT-MESTRE-CRIACAO-DE-GAMES-GAMES` e leia o `PROMPT_MESTRE.md`. Use-o como método, mas execute e registre o trabalho no repositório do jogo que eu indicar. Antes de modificar, confira branch e commit, decisões, tarefas e estado atual. Depois reporte mudanças, testes e o commit/PR efetivamente publicado.

## Regras de colaboração

- **Fonte de verdade:** regras universais aqui; cada jogo mantém GDD, assets, histórico e estado.
- **Um único fluxo:** todas as IAs consultam a revisão mais recente antes de trabalhar. Nenhuma IA compartilha memória com outra.
- **Honestidade:** vale o Contrato de Evidência (seção 0 do `PROMPT_MESTRE.md`).
- **Qualidade mensurável:** portões e scorecard em `modulos/PLAYTEST_E_QUALIDADE.md`.
- **Público:** não subir tokens, senhas, materiais privados ou arquivos protegidos.

**Observação:** citar o repositório não garante que a ferramenta o acessou. Cada IA depende da capacidade real de abrir links ou ler arquivos.
