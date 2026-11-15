# MÓDULO — Tarefas, revisão independente, testes e skills

Objetivo: a IA trabalhar como alguém do time, que **segue regra, testa, documenta e melhora a cada projeto**, em vez de dizer "pronto" sem prova. Referência: seção 0 (regra 9), 10 e 11 do `PROMPT_MESTRE.md`.

> Inspirado em práticas públicas de desenvolvimento com agentes (quadro de tarefas para agentes, revisão por agente separado, registro de decisões, skills). Tudo aqui usa recursos **gratuitos**: Git, GitHub, GitHub Actions, Vitest/Playwright, skills em arquivo.

## 1. Sem tarefa aberta, não se edita o jogo

- Antes de mexer em qualquer arquivo do jogo, a IA abre (ou pega) uma tarefa em `docs/TAREFAS.md` com ID, objetivo e **critério de pronto verificável**.
- Pedido direto do dono ("corrige o pulo") vira tarefa na hora: a IA cria a linha e segue. Não precisa pedir licença para criar a tarefa.
- Em **revezamento** (uma IA por vez, o padrão), a IA com a vez edita `TAREFAS.md`. Em **colaborativo**, vale a regra do integrador (`COMUNICACAO_CLAUDE_CODEX.md`, seção 3).
- Exceção: documentos de estado (`ESTADO_ATUAL`, `HANDOFF`) e o próprio `TAREFAS.md` podem ser editados sem tarefa.
- Limite honesto: hoje isso é **regra escrita** no `AGENTS.md`, não trava automática. Ver seção 6.

## 2. Etapas de toda tarefa

`FAZER → REVISAR → TESTAR → FECHADA` (ou `BLOQUEADA`, com motivo).

| Etapa | Quem | Para avançar |
|---|---|---|
| FAZER | IA responsável | Código/asset feito na branch de trabalho |
| REVISAR | **outro agente**, que não escreveu | Revisão registrada com achados (ou "sem achados") |
| TESTAR | IA responsável | Testes automáticos **rodaram de verdade e passaram** (saída anexada) + teste no aparelho quando a tarefa mexe em controle/visual |
| FECHADA | IA responsável | Commit com o ID da tarefa e linha atualizada em `TAREFAS.md` |

**"Pronto" sem prova não avança.** Se o teste falhar, a tarefa volta para FAZER. Rótulos do Contrato de Evidência valem em cada etapa.

## 3. Revisão independente (revisão cruzada)

- **Quem revisa não escreveu o código.** Ordem de preferência: (1) a outra IA (Claude revisa o que o Codex fez e vice-versa); (2) um subagente novo, sem o contexto de quem escreveu; (3) se nenhum for possível, declarar **REVISÃO NÃO FEITA** (a tarefa pode fechar só com o "ok" do dono).
- O revisor **lê o código e as regras**, não confia no relato. Checklist mínimo:
  - A lógica faz o que o GDD e o critério de pronto pedem?
  - **Tempo:** efeitos visuais e de interface usam o relógio certo? (ex.: flash ou tremor medidos pelo tempo do jogo ficam lentos demais em câmera lenta/hit-stop; use tempo real quando o efeito não deve desacelerar.)
  - Estados e transições: tem estado preso, entrada ignorada, timer que nunca zera, objeto que não é destruído?
  - Mobile: toque, áudio desbloqueado no primeiro toque, desempenho.
  - Regras do protocolo: nada desenhado por código, assets pelo manifesto, sons pelo nome do evento.
- Registro curto (5 linhas) em `docs/handoff/` ou na descrição do PR: o que olhou, achados, gravidade, decisão.
- **Economia de crédito:** tarefas pequenas da mesma sessão podem ser revisadas **em lote**, uma vez no fim. Tarefas só de texto/documentação ou troca de arquivo de asset sem código: revisão leve (o próprio dono olha ou a IA confere o checklist), registrada como tal.

## 4. Testes que rodam de verdade

- Todo jogo tem um comando `npm test` (ou equivalente da engine) desde o primeiro código.
- **Lógica do jogo** (dano, pontuação, colisão, timers, progressão): testes unitários, ex.: Vitest (gratuito).
- **Smoke test** do jogo web: navegador headless (ex.: Playwright, gratuito) abre o jogo, 0 erros no console, ~60 s de entradas, screenshot. Rótulo EXECUTADO (EMULADO).
- **GitHub Actions** roda os testes a cada push (modelo em `MODELO_PROJETO/.github/workflows/testes.yml`). Gratuito em repositório público; em privado, há cota mensal gratuita de minutos (conferir no GitHub).
- Bug achado vira **teste novo** antes da correção, para não voltar.
- Teste automático não substitui o dono jogando no celular.

## 5. Um commit por tarefa

- Mensagem começa com o ID: `T-012: flash do golpe usa tempo real`. Assim dá para saber por que cada linha existe (`git log`, `git blame`).
- Decisão importante tomada na tarefa vai para `docs/DECISOES.md` (o que foi decidido, por quê, **o que muda**), citando o ID.

## 6. Trava automática (opcional)

- No GitHub, regras de proteção de branch podem impedir o merge na `main` com teste falhando. **Em repositório público é gratuito; em privado pode exigir plano pago** — verificar antes de prometer.
- No Claude Code, hooks podem bloquear edição sem tarefa aberta. Só adotar depois do primeiro jogo, se a regra escrita não estiver sendo seguida.

## 7. Skills: o que a IA aprendeu não se perde

- Quando algo deu trabalho e exigiu várias tentativas (ex.: gerar sprite no Pixel Lab, montar vídeo de devlog, acertar o áudio), ao terminar a IA propõe **registrar o jeito certo numa skill**: instruções curtas, exemplos e, se houver, scripts. Inclui as reclamações do dono ("som do jogo baixo", "não desenhar por código").
- Onde guardar: skills do jogo em `.claude/skills/<nome>/SKILL.md` e cópia em `.agents/skills/<nome>/SKILL.md` (pasta lida por outros agentes; suporte do Codex a essa pasta **não verificado** — na dúvida, o `AGENTS.md` aponta para o arquivo). Skills úteis para todos os jogos sobem para este repositório central, em `skills/`, por PR.
- Skill só entra com o "ok" do dono e depois de ter funcionado ao menos uma vez.
