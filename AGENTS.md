# AGENTS.md — Repositório de metodologia universal para jogos (canônico)

Arquivo compartilhado por todos os agentes (Codex, Claude Code e outros). Mantenha curto.

- Este repositório mantém o **protocolo universal**, não o código de um jogo. Leia `PROMPT_MESTRE.md` para metodologia ou novo projeto; abra `modulos/` só se a tarefa pedir. Em correções pontuais, leia só o pertinente.
- O dono é o diretor criativo. Não altere decisões aprovadas sem aprovação; registre mudanças significativas.
- Modelos: trabalho **criativo** no modelo mais forte, **execução** no mais barato ou no que o dono escolher (`modulos/MODELOS_E_PARALELISMO.md`).
- Comunicação entre IAs e troca de IA no meio do jogo (revezamento, ordem de serviço, branches, regra anti-sobrescrita): `modulos/COMUNICACAO_CLAUDE_CODEX.md`.
- Qualidade do jogo: portões e scorecard em `modulos/PLAYTEST_E_QUALIDADE.md`. A nota da IA é hipótese; vale a do dono e a de jogadores reais.
- Escopo, descarte e orçamento por fase: `modulos/ESCOPO_E_ORCAMENTO.md`. Lançamento: `modulos/LANCAMENTO_E_RETENCAO.md`.
- Para mudar a metodologia: compare a versão atual, explique motivo e evidência, mantenha compatibilidade, atualize versão e `CHANGELOG.md`, valide links e modelos. Proponha por branch + PR.
- Para desenvolver um jogo, use **o repositório daquele jogo**; mantenha lá `docs/ESTADO_ATUAL.md`, `docs/DECISOES.md`, `docs/HANDOFF.md` e `docs/TAREFAS.md`.
- Antes de agir no GitHub: confira repositório, branch, commit **e PRs abertos**. Vale o histórico do Git, não só as anotações.
- Ao parar: registre concluído, pendências, testes realmente executados, arquivos e próximo passo. Em revezamento (uma IA por vez), a IA com a vez atualiza ESTADO e HANDOFF; em modo colaborativo (simultâneo), a executora escreve só `docs/handoff/T-xxx.md`. Só anuncie sincronização após commit/PR confirmado.
- Evite sobrescrever commits de outros agentes: use branches e a regra anti-sobrescrita.
- Vale o Contrato de Evidência (seção 0 do `PROMPT_MESTRE.md`).
- Skills externas são opcionais e exigem autorização para instalar: `modulos/SKILLS_EXTERNAS.md`.
- Respostas e perguntas curtas; priorize produção verificável.
