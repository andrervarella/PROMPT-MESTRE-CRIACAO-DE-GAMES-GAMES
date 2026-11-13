# MÓDULO — Comunicação padronizada entre Claude, Codex e outras IAs

Objetivo: mesmas normas, sem se atropelar, sem depender de memória de chat. Referência: seções 1 e 11 do `PROMPT_MESTRE.md`.

## 1. Um arquivo de regras, não dois

- **`AGENTS.md` é o canônico.** Contém **tudo** que for compartilhado, e também uma seção "Codex" para o que é só do Codex.
- **`CLAUDE.md` é fino:** a linha `@AGENTS.md` mais só o específico do Claude. **Não conte com o Codex lendo CLAUDE.md**; por isso nada compartilhado mora lá.
- Mantenha o AGENTS.md curto (~200 linhas, bem abaixo de 32 KiB; o Codex para de ler em torno disso por padrão). Detalhes ficam em `docs/`.
- O arquivo mais próximo da pasta de trabalho tem precedência em várias ferramentas; evite AGENTS.md/CLAUDE.md conflitantes em pastas superiores.
- Relatos de setembro de 2026 dizem que o Claude Code aceita AGENTS.md quando não há CLAUDE.md. **Não verificado por nós**; o wrapper `@AGENTS.md` funciona nos dois casos.
- **Chats** (ChatGPT, claude.ai) **não carregam esses arquivos sozinhos**: o dono cola o núcleo ou o link, e a IA declara o que realmente conseguiu abrir.
- O `AGENTS.md` do jogo deve ser **autossuficiente** (resumo das regras essenciais dentro dele), porque agente sem rede não busca outro repositório.

## 2. Ordem de serviço (toda tarefa delegada)

```
ID: T-007
Objetivo: (1 frase)
Nível de modelo: CRIATIVO | EXECUÇÃO
Responsável: (Claude / Codex / outro)   Branch: (ver seção 4)
Escopo (arquivos/pastas permitidos):
Fora de escopo:
Entradas: (links, arquivos, manifesto de assets)
Critério de pronto (verificável):
Teto de custo: (se usar serviço pago)
Entrega: PR / arquivo / build, com hash
```

Para pedido pequeno e direto do dono, a ordem de serviço completa não é obrigatória; vale a seção 8.

## 3. Quem escreve onde (evita conflito de merge)

- **Uma IA só no projeto (modo solo):** ela atualiza ESTADO_ATUAL e HANDOFF ao fim da sessão.
- **Várias IAs (modo colaborativo):**
  - A **IA executora NÃO edita** `docs/TAREFAS.md` nem `docs/ESTADO_ATUAL.md`.
  - Ela escreve **só** `docs/handoff/T-xxx.md` (um arquivo por tarefa) e a descrição do PR.
  - O **integrador** atualiza TAREFAS e ESTADO ao fazer o merge, na branch canônica.
  - **Integrador padrão: o dono do projeto**, se `docs/DECISOES.md` não indicar outro.
- **Atribuição:** quem atribui tarefas é o dono ou o integrador. A IA só começa tarefa atribuída a ela.
- Duas tarefas não editam o mesmo arquivo ao mesmo tempo.

## 4. Branches e PR

- Padrão: `claude/<id>-<slug>` e `codex/<id>-<slug>`. Se a ferramenta impuser outro nome, **use o dela e registre em TAREFAS** (feito pelo integrador).
- Sem commit direto na `main` em trabalho colaborativo. Toda entrega é **PR** com: o que mudou, evidências (rótulos do Contrato), o que não foi testado, decisão pedida.
- Antes de começar: buscar o remoto e conferir branch/commit. Ao terminar: informar o hash.

## 5. Mensagem de entrega (5 linhas)

```
FEITO: ...
EVIDÊNCIA: (rótulo + comando/arquivo/commit)
NÃO TESTADO: ...
DECISÃO PEDIDA: ... (ou "nenhuma")
PRÓXIMA AÇÃO: arquivo + critério de aceitação
```

A versão longa vai em `docs/handoff/T-xxx.md` (colaborativo) ou `docs/HANDOFF.md` (solo).

## 6. Conflitos e divergências

- Vale `docs/DECISOES.md`. Sem decisão registrada, **escale ao dono com 2 opções** e uma recomendação.
- Não reescreva o trabalho do outro; proponha por PR ou comentário.
- Se o ESTADO_ATUAL contradiz o código/Git, verifique e sinalize a divergência.

## 7. Papéis e modelos

Papéis (especifica, implementa, revisa, integra) são definidos **por tarefa**, na ordem de serviço, e registrados em DECISOES quando forem permanentes. Não presuma capacidades de uma ferramenta sem verificar. O nível de modelo é uma **indicação**: a IA não troca o próprio modelo; ela declara o nível, e o dono troca ou a tarefa é delegada por subagente quando a ferramenta permitir.

## 8. Trocar de IA a qualquer momento (não há ordem fixa)

Qualquer etapa pode ser feita por qualquer IA, em qualquer ordem. Exemplo: a ideia nasce no Claude, os assets saem no Codex (que tem o conector do Pixel Lab) e o jogo volta ao Claude depois. O método existe para que as duas IAs trabalhem do mesmo jeito, não para impor quem faz o quê.

**Quando o dono diz "o jogo X está no Codex, veja como está e continue":**

1. Abra o repositório do jogo e confira branch e último commit (seção 1 do `PROMPT_MESTRE.md`).
2. Aplique a **regra anti-sobrescrita** abaixo.
3. Leia `docs/ESTADO_ATUAL.md`, `docs/DECISOES.md`, `docs/TAREFAS.md` e o handoff mais recente. Não precisa de ordem de serviço formal para continuar.
4. Responda em 5 linhas: o que entendeu do estado, qual é o próximo passo e o que não conseguiu confirmar. Só depois aja.

### Regra anti-sobrescrita (antes de editar qualquer coisa)

O risco: a IA que chega trabalha sobre uma versão antiga e apaga ou contradiz o que a outra acabou de fazer. **A fonte de verdade é o histórico do Git, não as anotações**, porque anotação pode estar incompleta.

1. Busque o estado mais recente da branch: último commit e lista dos commits recentes.
2. Compare com o commit registrado em `ESTADO_ATUAL.md` e no handoff mais recente. Se existirem commits **depois** do último registrado, leia o que eles mudaram (arquivos e diferenças) **antes** de tocar em qualquer coisa. Mudança sem anotação: avise o dono e registre.
3. Crie a branch de trabalho a partir do **último commit**, nunca de uma cópia antiga.
4. Edite **sobre a versão que acabou de ler** de cada arquivo. Nunca reescreva um arquivo inteiro a partir de memória ou de cópia anterior.
5. Antes de enviar (push/PR), confira de novo se a branch não andou nesse meio tempo. Se andou, incorpore as mudanças antes de enviar.
6. Em dúvida, ou se o código contradiz as anotações: **pare e pergunte ao dono**. Não "conserte" por cima.

**Obrigação de quem para de trabalhar:** fazer commit e push e deixar no handoff (a) o hash do último commit, (b) a lista de arquivos alterados, (c) o que ficou pela metade, (d) o próximo passo. Sem isso, a próxima IA parte do zero.

**Limites que valem sempre:**

- **Só existe o que está no Git.** Uma IA não enxerga a pasta local da outra. Trabalho que ficou só no computador/ambiente de uma IA, sem commit e push, conta como **NÃO SINCRONIZADO**: a IA que recebe pede ao dono que a outra faça commit e push antes de continuar.
- **Ferramentas diferem por IA** (um conector pode existir só em uma). Cada IA declara as ferramentas que realmente tem. Se a tarefa precisa de uma que só a outra tem, avisa o dono e sugere passar a tarefa, registrando no handoff.
- **Assets gerados por qualquer IA** entram no `docs/MANIFESTO_ASSETS.md` com proveniência (ferramenta, prompt, seed, data) e seguem o mesmo Portão V. O personagem aprovado precisa estar **no repositório** (ex.: `concept/`) para a outra IA usá-lo como referência fixa, seja quem gerou.
- Duas IAs **não** trabalham ao mesmo tempo nos mesmos arquivos (seção 3). Em dia de troca, o dono avisa quem está com a vez.
