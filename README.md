# PROMPT MESTRE UNIVERSAL — CRIAÇÃO DE GAMES COM IA

**Versão vigente: V4.5** · Metodologia compartilhada para ChatGPT, Claude, Codex e outras IAs.

Este repositório público contém **o método universal para criar e aprimorar jogos com IA**, independentemente de gênero, engine, universo ou plataforma. **Não** é o repositório do código de um jogo específico.

## Comece aqui

1. Leia o [PROMPT_MESTRE.md](PROMPT_MESTRE.md) (núcleo curto). Abra os [módulos](modulos/) só quando a tarefa pedir.
2. Agente de programação: veja também [AGENTS.md](AGENTS.md) (canônico). Claude Code: [CLAUDE.md](CLAUDE.md) (importa o AGENTS.md).
3. Para **cada jogo**, mantenha código e estado no **repositório do jogo**. Copie/adapte [MODELO_PROJETO/](MODELO_PROJETO/).
4. Ao iniciar a sessão, confira **repositório, branch, último commit e PRs abertos**, e leia o `ESTADO_ATUAL` do jogo (as outras anotações só se a tarefa tocar nelas). Vale o histórico do Git. Todo trabalho é feito em **tarefas** (fazer → revisar → testar → fechar). Ao encerrar, a IA que está com a vez atualiza ESTADO, HANDOFF e TAREFAS (em modo colaborativo, a executora escreve só o handoff da tarefa) e faz commit/push.
5. Informe o hash do commit ou a URL do PR para comprovar a sincronização.

## Fluxo resumido

Conceito → decisão técnica → **Pacote de Aprovação Visual (Portão V)** → (ação) lote-piloto de animação → **prova do core loop (Portão 1)** → GDD → produção completa de assets → **vertical slice (Portão 2)** → QA/playtest → **Concluído (Portão 3)**. Qualquer IA pode assumir qualquer etapa. Cada mudança no jogo é uma tarefa revisada por outro agente e testada de verdade.

## Arquivos

| Arquivo | Função |
|---|---|
| [PROMPT_MESTRE.md](PROMPT_MESTRE.md) | Método canônico (V4.5), nome estável |
| [modulos/](modulos/) | Acervo Drive ↔ GitHub (pasta por jogo), modo jogo completo, pacote de aprovação visual, tarefas/revisão/testes/skills, escopo e orçamento, modelos e paralelismo, comunicação Claude↔Codex, playtest e qualidade, lançamento e retenção, arte/pixel art mobile, áudio, game feel, vídeo/trailer, comercial, skills externas, fontes |
| [AGENTS.md](AGENTS.md) | Regras canônicas para todos os agentes |
| [CLAUDE.md](CLAUDE.md) | Fino: importa o AGENTS.md e traz só o específico do Claude |
| [REGISTRO_DE_PROJETOS.md](REGISTRO_DE_PROJETOS.md) | Índice de repositórios de jogos |
| [CHANGELOG.md](CHANGELOG.md) | Histórico das versões |
| [MODELO_PROJETO/](MODELO_PROJETO/) | Templates para cada jogo (inclui verificação automática no GitHub Actions) |

Histórico preservado: [V3.1](PROMPT_MESTRE_UNIVERSAL_GAMES_IA_V3_1.md) e [V3.0](PROMPT_MESTRE_UNIVERSAL_GAMES_IA_V3.md).

## Como pedir a outra IA

> Consulte o repositório público `https://github.com/andrervarella/PROMPT-MESTRE-CRIACAO-DE-GAMES-GAMES` e leia o `PROMPT_MESTRE.md`. Use-o como método, mas execute e registre o trabalho no repositório do jogo que eu indicar. Antes de modificar, confira branch, commit e PRs abertos, o estado atual e as decisões. Trabalhe em tarefas (fazer → revisar → testar → fechar). Depois reporte mudanças, testes e o commit/PR efetivamente publicado.

## Acervo de assets entre IAs — V4.5

- **Drive:** `GAMES_IA/NOME DO JOGO/` (pastas 00–05) guarda artes originais aprovadas, rascunhos, descartes, sprites e cenários em produção, vídeos, músicas-fonte e ZIPs.
- **GitHub:** código, projeto executável, decisões, tarefas, documentação, manifestos e **somente assets finais otimizados usados pelo jogo**. O jogo não depende do Drive para rodar.
- **Manifesto por asset:** ID, versão, status, caminho lógico Drive/GitHub e SHA-256; cópias sem perda exigem checagem exata de pixels e hashes de ambas.
- **Segurança:** não publicar links do Drive/URLs assinadas/credenciais; alertar sobre arte não lançada em repositórios públicos e **não apagar assets existentes** sem autorização do proprietário.
- **Sincronização:** confirmar separadamente que está salvo no Drive, no GitHub e acessível à outra IA. Ver [módulo Drive ↔ GitHub](modulos/ACERVO_DRIVE_GITHUB.md).

## Regras de colaboração

- **Fonte de verdade:** regras universais aqui; cada jogo mantém GDD, assets, histórico e estado.
- **Um único fluxo:** todas as IAs consultam a revisão mais recente antes de trabalhar. Nenhuma IA compartilha memória com outra.
- **Honestidade:** vale o Contrato de Evidência (seção 0 do `PROMPT_MESTRE.md`).
- **Qualidade mensurável:** portões e scorecard em `modulos/PLAYTEST_E_QUALIDADE.md`; testes automáticos e revisão cruzada em `modulos/TAREFAS_REVISAO_TESTES.md`.
- **Público:** não subir tokens, senhas, materiais privados ou arquivos protegidos.

**Observação:** citar o repositório não garante que a ferramenta o acessou. Cada IA depende da capacidade real de abrir links ou ler arquivos.
