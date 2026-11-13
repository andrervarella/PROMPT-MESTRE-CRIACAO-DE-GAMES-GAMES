# AGENTS.md — Modelo para repositório de jogo (canônico)

- Este repositório contém o jogo **[NOME]**, que usa o Prompt Mestre Universal **V4.0** (`PROMPT_MESTRE.md`). [LINK DO REPOSITÓRIO CENTRAL DA METODOLOGIA].
- Antes de modificar sistemas relevantes, conferir branch/commit e `docs/ESTADO_ATUAL.md`, `docs/DECISOES.md`, `docs/HANDOFF.md`, `docs/TAREFAS.md` e as partes necessárias do GDD.
- Preservar código e assets aprovados; não começar do zero se já existir um projeto. Não trocar engine ou arquitetura sem justificar e aprovar.
- Rodar testes aplicáveis: [COMANDO BUILD] / [COMANDO TESTES]. Registrar evidências reais; quando não rodar, marcar NÃO TESTADO.
- Modelos: criativo = [modelo forte]; execução = [modelo barato]. Ver `modulos/MODELOS_E_PARALELISMO.md` do repositório central.
- Trabalho com várias IAs: ordem de serviço, uma tarefa = um dono = uma branch (`claude/<id>-...`, `codex/<id>-...`), PR e integrador definido em `docs/DECISOES.md`. Ver `modulos/COMUNICACAO_CLAUDE_CODEX.md` do repositório central.
- Evitar sprites genéricos, animações deformadas e imitações sem licença. Respeitar a direção artística específica deste jogo. Assets com proveniência registrada.
- Antes de encerrar: atualizar estado, decisões novas, tarefas e handoff; commit/PR apenas com acesso/autorização, informando branch e hash/PR.
