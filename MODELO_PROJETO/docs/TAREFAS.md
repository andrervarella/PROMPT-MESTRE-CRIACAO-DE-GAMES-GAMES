# TAREFAS — [NOME DO JOGO]

Fila única. **Sem tarefa aberta, nenhuma IA edita arquivo do jogo** (`modulos/TAREFAS_REVISAO_TESTES.md`). Pedido direto do dono vira tarefa na hora.

**Quem edita este arquivo:** em revezamento (uma IA por vez, o padrão), a IA com a vez. Em colaborativo (duas IAs ao mesmo tempo), o integrador; a executora escreve `docs/handoff/T-xxx.md`.

Etapas: **FAZER → REVISAR → TESTAR → FECHADA** · ou **BLOQUEADA** (com motivo).

| ID | Objetivo | Nível | Responsável | Revisor (não escreveu) | Etapa | Critério de pronto | Teste (comando + resultado) | Commit |
|---|---|---|---|---|---|---|---|---|
| T-001 | (1 frase) | EXECUÇÃO | Claude | Codex | FAZER | (verificável) | — | — |

- Commit de cada tarefa começa com o ID: `T-001: ...`.
- Teste falhou: a tarefa volta para FAZER.
- Revisão impossível: escrever REVISÃO NÃO FEITA (fecha só com "ok" do dono).

## Ordem de serviço

Use o formato de `modulos/COMUNICACAO_CLAUDE_CODEX.md` (seção 2) do repositório central quando a tarefa for delegada a outra IA.
