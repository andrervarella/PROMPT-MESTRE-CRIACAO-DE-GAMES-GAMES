# MÓDULO — Comunicação padronizada entre Claude, Codex e outras IAs

Objetivo: as IAs trabalharem com as **mesmas normas**, sem se atropelar e sem depender de memória de chat. Referência: seções 1 e 11 do `PROMPT_MESTRE.md`.

## 1. Um arquivo de regras, não dois

- **`AGENTS.md` é o canônico.** Codex e muitas outras ferramentas leem esse formato aberto.
- **`CLAUDE.md` é fino:** importa o AGENTS.md com a linha `@AGENTS.md` e acrescenta **só** o que é específico do Claude (ex.: nível de modelo, uso de ferramentas). Nunca duplique regras.
- Mantenha o AGENTS.md curto: ~200 linhas ou menos e bem abaixo de 32 KiB (o Codex para de ler em torno de 32 KiB por padrão; a recomendação do Claude Code é CLAUDE.md abaixo de ~200 linhas). Detalhes ficam em `docs/` e `modulos/`.
- Arquivo mais próximo da pasta de trabalho tem precedência em várias ferramentas; evite AGENTS.md/CLAUDE.md conflitantes em pastas superiores.
- Observação: relatos de setembro de 2026 dizem que o Claude Code passou a aceitar AGENTS.md quando não há CLAUDE.md. **Reconfirme na versão em uso**; com o wrapper `@AGENTS.md` funciona nos dois casos.

## 2. Ordem de serviço (toda tarefa delegada)

Use este formato curto, em `docs/TAREFAS.md` ou na mensagem:

```
ID: T-007
Objetivo: (1 frase)
Nível de modelo: CRIATIVO | EXECUÇÃO
Dono: (Claude / Codex / outro)  Branch: claude/T-007-slug ou codex/T-007-slug
Escopo (arquivos/pastas permitidos):
Fora de escopo:
Entradas: (links, arquivos, manifesto de assets)
Critério de pronto (verificável):
Teto de custo: (se usar serviço pago)
Entrega: PR / arquivo / build, com hash
```

## 3. Fila de tarefas única

`docs/TAREFAS.md` lista as tarefas com **um dono e uma branch cada**. Status: A FAZER · EM ANDAMENTO · EM REVISÃO · FEITO · BLOQUEADO.

- Quem **atribui** é o dono do projeto ou o integrador. A IA só começa tarefa atribuída a ela (evita duas IAs pegarem a mesma).
- Duas tarefas não editam o mesmo arquivo ao mesmo tempo. Se precisarem, a segunda espera ou combina antes.

## 4. Branches, PR e integrador

- Nome: `claude/<id>-<slug>`, `codex/<id>-<slug>`. Nunca commitar direto na `main` em trabalho colaborativo.
- Toda entrega é **PR** com descrição curta: o que mudou, evidências (EXECUTADO / SÓ LIDO / NÃO VERIFICADO), o que não foi testado, decisão pedida.
- **Um integrador** (indicado pelo dono em `docs/DECISOES.md`) revisa conflitos, faz o merge e atualiza o ESTADO_ATUAL.
- Antes de começar: buscar o remoto e conferir a branch/commit. Ao terminar: informar o hash.

## 5. Mensagem de entrega (5 linhas)

```
FEITO: ...
EVIDÊNCIA: (rótulo + comando/arquivo/commit)
NÃO TESTADO: ...
DECISÃO PEDIDA: ... (ou "nenhuma")
PRÓXIMA AÇÃO: arquivo + critério de aceitação
```

O mesmo conteúdo, mais detalhado, vai em `docs/HANDOFF.md`.

## 6. Conflitos e divergências

- Vale o que está em `docs/DECISOES.md`. Sem decisão registrada, **escale ao dono com 2 opções** e uma recomendação.
- Não reescreva o trabalho do outro; proponha mudança por PR ou comentário.
- Se o ESTADO_ATUAL contradiz o código/Git, verifique e corrija o registro, sinalizando a divergência.

## 7. Papéis

Papéis (quem especifica, quem implementa, quem revisa, quem integra) são definidos **por tarefa**, na ordem de serviço, e registrados em DECISOES quando forem permanentes. Não presuma capacidades de uma ferramenta sem verificar (Contrato de Evidência).
