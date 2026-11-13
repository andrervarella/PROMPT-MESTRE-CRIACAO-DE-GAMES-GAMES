# PROMPT MESTRE UNIVERSAL — CRIAÇÃO DE GAMES COM IA

**Versão vigente: V4.0** · Metodologia compartilhada para ChatGPT, Claude, Codex e outras IAs.

Este repositório público contém **o método universal para criar e aprimorar jogos com IA**, independentemente de gênero, engine, universo ou plataforma. **Não** é o repositório do código de um jogo específico.

## Comece aqui

1. Leia o [PROMPT_MESTRE.md](PROMPT_MESTRE.md) (núcleo curto). Abra os [módulos](modulos/) só quando a tarefa pedir.
2. Agente de programação: veja também [AGENTS.md](AGENTS.md). Claude Code: [CLAUDE.md](CLAUDE.md).
3. Para **cada jogo**, mantenha código e estado no **repositório do jogo**. Copie/adapte [MODELO_PROJETO/](MODELO_PROJETO/).
4. Ao iniciar a sessão, confira **repositório, branch, commit, ESTADO_ATUAL, DECISOES e HANDOFF** do jogo. Ao encerrar, atualize esses documentos e faça commit/PR se autorizado.
5. Informe o hash do commit ou a URL do PR para comprovar a sincronização.

## Arquivos

| Arquivo | Função |
|---|---|
| [PROMPT_MESTRE.md](PROMPT_MESTRE.md) | Método canônico (V4.0), nome estável |
| [modulos/](modulos/) | Modelos e paralelismo, arte/pixel art mobile, áudio, game feel, vídeo/trailer, comercial, skills externas |
| [AGENTS.md](AGENTS.md) | Regras para Codex e agentes similares |
| [CLAUDE.md](CLAUDE.md) | Instruções para Claude Code |
| [REGISTRO_DE_PROJETOS.md](REGISTRO_DE_PROJETOS.md) | Índice de repositórios de jogos |
| [CHANGELOG.md](CHANGELOG.md) | Histórico das versões |
| [MODELO_PROJETO/](MODELO_PROJETO/) | Templates para cada jogo |

Histórico preservado: [V3.1](PROMPT_MESTRE_UNIVERSAL_GAMES_IA_V3_1.md) e [V3.0](PROMPT_MESTRE_UNIVERSAL_GAMES_IA_V3.md).

## Como pedir a outra IA

> Consulte o repositório público `https://github.com/andrervarella/PROMPT-MESTRE-CRIACAO-DE-GAMES-GAMES` e leia o `PROMPT_MESTRE.md`. Use-o como método, mas execute e registre o trabalho no repositório do jogo que eu indicar. Antes de modificar, confira branch e commit, decisões e estado atual. Depois reporte mudanças, testes e o commit/PR efetivamente publicado.

## Regras de colaboração

- **Fonte de verdade:** regras universais aqui; cada jogo mantém GDD, assets, histórico e estado.
- **Um único fluxo:** todas as IAs consultam a revisão mais recente antes de trabalhar. Nenhuma IA compartilha memória com outra.
- **Honestidade:** vale o Contrato de Evidência (seção 0 do `PROMPT_MESTRE.md`).
- **Público:** não subir tokens, senhas, materiais privados ou arquivos protegidos.

**Observação:** Claude Code pode reconhecer `CLAUDE.md` em projeto ao qual tenha acesso. Claude em chat e outras IAs dependem da capacidade real de abrir links ou ler arquivos; citar o repositório não garante que a ferramenta o acessou.
