# AGENTS.md — Repositório de metodologia universal para jogos (canônico)

Arquivo compartilhado por todos os agentes (Codex, Claude Code e outros). Mantenha curto.

- Este repositório mantém o **protocolo universal**, não o código de um jogo. Leia `PROMPT_MESTRE.md` para metodologia ou novo projeto; abra `modulos/` só se a tarefa pedir. Em correções pontuais, leia só o pertinente.
- O dono é o diretor criativo. Não altere decisões aprovadas sem aprovação; registre mudanças significativas.
- Modelos: trabalho **criativo** no modelo mais forte, **execução** no mais barato (`modulos/MODELOS_E_PARALELISMO.md`).
- Comunicação entre IAs (ordem de serviço, fila `docs/TAREFAS.md`, branches, PR, integrador): `modulos/COMUNICACAO_CLAUDE_CODEX.md`.
- Qualidade do jogo: portões e scorecard em `modulos/PLAYTEST_E_QUALIDADE.md`. A nota da IA é hipótese; vale a do dono e a de jogadores reais.
- Para mudar a metodologia: compare a versão atual, explique motivo e evidência, mantenha compatibilidade, atualize versão e `CHANGELOG.md`, valide links e modelos. Proponha por branch + PR.
- Para desenvolver um jogo, use **o repositório daquele jogo**; mantenha lá `docs/ESTADO_ATUAL.md`, `docs/DECISOES.md`, `docs/HANDOFF.md` e `docs/TAREFAS.md`.
- Antes de agir no GitHub: confira repositório, branch e commit.
- Após trabalho significativo: registre concluído, pendências, testes realmente executados, arquivos e próximo passo. Só anuncie sincronização após commit/PR confirmado.
- Evite sobrescrever commits de outros agentes; use branches e PR.
- Vale o Contrato de Evidência (seção 0 do `PROMPT_MESTRE.md`).
- Skills externas são opcionais e exigem autorização para instalar: `modulos/SKILLS_EXTERNAS.md`.
- Respostas e perguntas curtas; priorize produção verificável.
