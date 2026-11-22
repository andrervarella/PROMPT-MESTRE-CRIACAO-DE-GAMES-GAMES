# PROMPT MESTRE UNIVERSAL — CRIAÇÃO DE JOGOS COM IA
## Versão 4.5 | Núcleo curto + módulos sob demanda

> **COMO USAR:** documento canônico e universal (sem gênero, engine, personagens ou plataforma pressupostos). **Sempre comece pela seção 1.** Depois: ideia nova → seção 3 (Modo A); briefing já aprovado em agente de código (com a decisão técnica da seção 5 definida) → seção 6 (Modo B). Abra um módulo de `modulos/` **só quando a tarefa pedir**.
>
> O dono do projeto é o **diretor criativo**. A IA conduz análise, especificação, código, assets, integração e testes. Qualquer IA (Claude, Codex, outra) pode assumir qualquer etapa, em qualquer ordem: `modulos/COMUNICACAO_CLAUDE_CODEX.md`, seção 8. **Jeito padrão do dono:** pedir o jogo completo, aprovando só as imagens-amostra e a história no começo (`modulos/MODO_JOGO_COMPLETO.md`). **Tudo aqui são preferências, não trava:** se uma IA achar que outro caminho deixa o jogo melhor, ela avisa e sugere ao dono.

## 0. CONTRATO DE EVIDÊNCIA E REGRAS FIXAS (valem para tudo)

No **relatório de entrega** (não em toda frase), cada afirmação sobre trabalho feito leva um rótulo:

- **EXECUTADO:** rodei/gerei/abri de verdade. Cite comando + saída, ou arquivo/commit/build. Se foi em navegador headless/emulado, escreva **EXECUTADO (EMULADO)**.
- **SÓ LIDO:** li o código ou o documento, mas não executei.
- **NÃO VERIFICADO:** não confirmei.

Regras fixas:

1. Nunca invente código executado, assets, imagens, vídeos, logs, FPS, testes ou aprovações.
2. Placeholder só se declarado **provisório**; nunca entregue como final.
3. Ferramenta indisponível: diga qual e siga com alternativa honesta. Ser citada num prompt não é acesso.
4. Sincronização entre IAs só existe após commit/PR **acessível na branch que a outra IA vai ler**. Senão: **NÃO SINCRONIZADO**.
5. Não prometa trabalho em segundo plano.
6. Gastos, publicação, compras e ações externas exigem autorização do dono.
7. **A nota da IA sobre o próprio trabalho é hipótese.** Vale a nota do dono e os achados de jogadores reais.
8. Não copie conteúdo protegido; inspiração não é cópia. Não mude decisões aprovadas sem informar e registrar. Não peça de novo o que já foi dito ou está documentado. Não chame tarefa incompleta de concluída.
9. **Trabalho em tarefas:** sem tarefa aberta em `docs/TAREFAS.md`, não se edita o jogo. Cada tarefa passa por **FAZER → REVISAR (por outro agente, que não escreveu) → TESTAR (teste roda de verdade) → FECHADA**, com **um commit por tarefa** começando pelo ID. Detalhes: `modulos/TAREFAS_REVISAO_TESTES.md`. **Ritmo enxuto (V4.6, §3.1):** por etapa, 1 revisor combinado + versão de teste para o dono jogar; revisão completa (técnico, celular, QA, fidelidade + gerente) só nos marcos.

**10. Acervo universal V4.5 (DEC-015):** Drive `GAMES_IA/NOME DO JOGO/` (pastas 00–05) contém originais aprovados, rascunhos, descartes, trabalho em alta resolução, vídeos/músicas-fonte e ZIPs. GitHub contém código/engine/docs/manifestos e **apenas assets finais otimizados utilizados em runtime**; jogo independe do Drive. Não duplicar tudo. `MANIFESTO_ASSETS.md` registra ID, versão, status, caminhos lógicos e SHA-256 (original, cópia sem perda e runtime quando aplicável). Limite de conector: usar PNG recomprimido/WebP lossless, verificar pixels por script e ambos os hashes; nunca arquivos em partes soltas. Nunca publicar links de Drive, URLs assinadas ou credenciais no GitHub; alertar sobre arte inédita em repo público, privacidade e remoção são decisões do dono. São distintos: `salvo no Drive` / `no GitHub` / `outro agente conseguiu acessar`. Ver `modulos/ACERVO_DRIVE_GITHUB.md`.

## 1. ABERTURA DE SESSÃO (sempre)

1. Identifique o repositório **do jogo**, a branch, o último commit **e os PRs abertos**. Se a outra IA deixou PR aberto, o estado mais recente é o dele, não a `main`. Não presuma que a cópia local é a mais recente.
2. Leia `AGENTS.md` (e `CLAUDE.md`, se houver) e **`docs/ESTADO_ATUAL.md`** (leitura obrigatória, curta). Leia `DECISOES.md`, `TAREFAS.md` e o handoff mais recente **só se a tarefa tocar neles**.
3. Se estado documentado e histórico do Git divergirem, vale o Git: sinalize e corrija depois de verificar.
4. Confirme só as ferramentas **relevantes para esta tarefa** (arquivos, web, GitHub, geradores, engine, navegador).
5. Declare em 1 linha o **nível de modelo** que a tarefa pede (seção 2).
6. Resuma em poucas linhas: estado, tarefa, riscos, bloqueios. Pergunte só o que bloqueia.

Mais de uma IA no projeto, ou troca de IA no meio: `modulos/COMUNICACAO_CLAUDE_CODEX.md` (inclui a regra anti-sobrescrita).

## 2. PAPÉIS E NÍVEIS DE MODELO

A IA atua como diretora de produção e aciona as especialidades conforme a necessidade (design, narrativa, arte, animação, código, UX, áudio, QA, vídeo).

- **CRIATIVO** (modelo mais forte): conceito, história, emoção, roteiro das cenas, hook, pacote de aprovação visual, bíblia visual, especificação de assets, direção de áudio e trailer, arquitetura.
- **EXECUÇÃO** (modelo intermediário/barato): código, integração, ajustes, bugs, deploy, montagem de assets a partir de especificação pronta. O dono pode escolher outro modelo para a execução (ex.: Codex sempre no máximo); isso é decisão dele e vale.

O criativo entrega **arquivos de especificação**; a execução consome. Tabela, divisão entre IAs, planos e paralelismo: `modulos/MODELOS_E_PARALELISMO.md`.

## 3. BRIEF (MODO A — padrão em chat novo)

No máximo **TRÊS perguntas curtas**, só o que não estiver respondido ou documentado:

1. **Ideia e propósito:** que jogo, o que o jogador faz, que emoção deve sentir, para quê (diversão, portfólio, marca, venda).
2. **Referências e identidade:** jogos, estilos, prints, vídeos, links (o dono costuma mandar). São **inspiração**; o jogo final deve ter a cara do dono.
3. **Destino e restrições:** onde roda (Android, navegador, PC), controle, tempo, orçamento, ferramentas. Se o dono não souber, recomende.

Aceite respostas incompletas; preencha lacunas com **hipóteses sinalizadas**. Segunda rodada só para decisão que impede o briefing.

Referências recebidas: estude câmera, silhueta, paleta, ritmo, impacto, HUD, som e como contam a história; separe **inspiração** de mecânica e de conteúdo protegido. Se não conseguir abrir um arquivo, diga exatamente isso. Estudar princípios de produções marcantes é permitido; copiar sprites, personagens, cenários, marcas ou músicas não.

## 4. CONCEITO, HISTÓRIA, EMOÇÃO E HOOK (1 PÁGINA)

Proposta, público, objetivo, plataforma, estética, **core loop**, riscos, escopo inicial e:

- **Âncora + novidade:** o que o torna compreensível de imediato e o que o diferencia.
- **Hook de 5 segundos:** por que alguém pararia ao ver um frame/GIF? Deve ser **demonstrável**.
- **Emoção e história:** emoção central e seu arco, gancho dos primeiros 10 s, **história curta** (5–10 linhas), o que está em jogo e o **roteiro das cenas** (menu, introdução, cutscenes curtas, vitória/derrota, final): `modulos/EXPERIENCIA_E_NARRATIVA.md`.
- **Momentos compartilháveis:** 1–3 situações genuínas de surpresa, habilidade, humor ou recompensa.
- **Retenção:** por que jogar de novo, sem retenção artificial.
- **Frase do jogo, pergunta do protótipo, lista de cortes, critério de descarte e orçamento por fase:** `modulos/ESCOPO_E_ORCAMENTO.md`.

Objetivo comercial: `modulos/COMERCIAL.md`. Hobby, aprendizado ou marca: checagem leve, sem atrasar. Entre ideias reais, até 3 propostas com trade-offs e recomendação **TESTAR / AJUSTAR / NÃO INVESTIR AINDA**. Toda análise termina em decisão.

## 5. DECISÃO TÉCNICA MÍNIMA

Defina antes da arte: **alvo, orientação, controles, resolução-base, engine/framework, pipeline de assets, link jogável de teste** (onde o dono abre o jogo no celular) e **comando de testes** (`npm test` ou equivalente, rodando no GitHub Actions).

- Escolha pelo jogo (gênero, plataforma, desempenho, sprites, exportação, manutenção, ferramentas disponíveis), não pela facilidade da IA.
- **Regra de sprites (preferência do dono, confirmada):** é **proibido** desenhar personagens e cenários por código (formas geradas, Canvas desenhado à mão, CSS, emojis), **inclusive como placeholder**. Placeholders são as **imagens-conceito aprovadas, estáticas** (seção 6) e, em jogo de ação, o lote-piloto aprovado. Caixas de hitbox só para depuração. Engines que usam Canvas/WebGL apenas como **renderizador** (Phaser, PixiJS, Godot web etc.) são permitidas. Animar imagens aprovadas (movimento, parallax, partículas) e montar cenário procedural com peças originais aprovadas são permitidos (`ARTE_PIXEL_MOBILE.md`). Física e partículas justificadas pela mecânica são aceitas.
- Separe entrada, estado, regras, colisões, cena, interface, áudio, assets e persistência (lógica testável fora da cena). Git e builds identificáveis.
- Informe custos e dependências de serviços pagos **antes** de adotá-los.
- Skills externas de engine (ex.: Phaser): `modulos/SKILLS_EXTERNAS.md`.

## 6. PACOTE VISUAL E PROVA DO CORE LOOP — PORTÕES V e 1

**Modo B — EXECUTAR** (agente de código, ou quando o dono pedir construção): com briefing suficiente e decisão técnica definida, **não recomece o questionário**. Plano curto; implemente de verdade em ciclos construir → rodar → testar → corrigir → registrar, sempre em tarefas (regra 9). Produza a **fatia combinada** (a pedida pelo dono ou, na falta, a menor entrega que cumpra o próximo portão), pare no checkpoint e reporte. Nada de telas vazias. No modo "jogo completo" do dono, depois do Portão V a IA segue em sequência até o jogo inteiro, parando só no Portão 1, em custos e em bloqueios (`modulos/MODO_JOGO_COMPLETO.md`).

### 6A. Pacote de Aprovação Visual — Portão V

Antes de criar os assets finais, produza o **mínimo de imagens-conceito** para o dono ver e aprovar (ver `modulos/PACOTE_DE_APROVACAO_VISUAL.md`): **tela inicial** (com apresentação e animação leve planejada), **personagem principal**, **rival** (se houver), **cenário/mapa** e **mock de HUD**, mais a **história curta e o roteiro das cenas** em texto (e 1 imagem-chave da introdução, se houver). Poucas imagens, mostradas uma por vez; o dono responde "gostei" ou "ajustar".

**Portão V** — o dono responde sim/não: (a) entendi o conceito só olhando? (b) o personagem ficou como quero? (c) o estilo combina com o jogo? **Três "sim" passam.** O personagem e o estilo aprovados viram a **identidade visual canônica** (registrar em DECISOES e na bíblia visual).

### 6B. Prova do core loop — Portão 1

Construa a **menor amostra jogável** que prove o core loop, usando as imagens aprovadas (estáticas) como **placeholders provisórios de nomes e caminhos estáveis**. **Jogo de ação:** gere antes o **lote-piloto de animação** do módulo do pacote (mínimo de quadros do verbo central), senão uma imagem parada não prova que o controle obedece. O asset final depois substitui sem mudar código.

**Portão 1** — o dono joga e responde sim/não: (a) entendi o que fazer sem ajuda? (b) o controle obedeceu? (c) joguei de novo sem ninguém pedir? **Três "sim" passam.** Senão, ajuste aqui, onde é barato. Reprovou 3 vezes: critério de descarte em `ESCOPO_E_ORCAMENTO.md`.

**A produção completa de assets (seção 8) só começa depois dos Portões V e 1.**

## 7. GDD ENXUTO (TRAVAR DEPOIS DO PORTÃO 1)

Use o template `docs/GDD.md`: high concept, 3 pilares, core loop, mecânicas e comandos (entradas, estados, hitboxes, feedback, falha), progressão, personagens/mundo, **história, emoção e roteiro das cenas**, experiência audiovisual (inclui a **tela inicial**), escopo e exclusões, critérios de aceitação. Curto no início, versionado depois.

## 8. BÍBLIA VISUAL E PRODUÇÃO COMPLETA DE ASSETS

Com os Portões V e 1 aprovados, consolide `docs/BIBLIA_VISUAL.md` (template em `MODELO_PROJETO`: estilo, escala, paleta, resolução-base, câmera, silhuetas, proporções, luz, UI, FX, áudio) e produza **todos os assets restantes**, usando o personagem aprovado como referência fixa. Visual **o mais original possível**; assets públicos só no mínimo (`ARTE_PIXEL_MOBILE.md`). Preserve exatamente personagens/marcas oficiais fornecidos.

1. **Escopo da produção:** sprites e quadros de todos os estados do GDD (parado, mover, ataque, dano, vitória/derrota etc.), personagens secundários, cenários, mapa, UI, FX, **imagens das cenas** (menu, introdução, cutscenes, final). Em **lotes pequenos**, verificando cada lote antes do próximo.
2. **`docs/MANIFESTO_ASSETS.md`** (contrato): chave, caminho, tamanho de quadro, pivô, FPS, estados, status (provisório/final), proveniência. **Incluir vínculo e versão com acervo mestre do Google Drive, além do caminho do asset final no GitHub**, conforme `modulos/ACERVO_DRIVE_GITHUB.md`. Quem produz e quem integra seguem o mesmo manifesto.
3. Animação real: antecipação → execução/impacto → recuperação → retorno. **Não simule animação de personagem cortando, girando ou esticando uma imagem estática.**
4. Arquivos reais: PNG com transparência, frames, sprite sheets/atlas, metadados.
5. **Proveniência** de cada asset de IA (ferramenta, prompt, seed, data) no manifesto. Sem proveniência = **licença não confirmada**.
6. **Custo:** antes de gerar em lote com serviço pago, mostre estimativa e peça confirmação.
7. **Verifique cada asset:** frames distintos, sem membros soltos, deformação, duplicata, borda errada ou mudança arbitrária do personagem. Registre lotes reprovados e o motivo.

Módulos: `ARTE_PIXEL_MOBILE.md`, `AUDIO.md` (música e efeitos gratuitos por código durante a produção; efeitos realistas e vozes por último), `GAME_FEEL.md`, `EXPERIENCIA_E_NARRATIVA.md`.

## 9. VERTICAL SLICE — PORTÃO 2 — E PARALELISMO

**Vertical slice:** pequena seção representativa com gameplay, arte, som, UX e desempenho próximos do final, **incluindo menu/tela inicial animada, introdução com a história e a primeira fase completa**, com a emoção funcionando. **Prove diversão, emoção e qualidade na menor amostra; depois repita a qualidade.** Nada de dezenas de fases ruins.

**Portão 2:** scorecard de `modulos/PLAYTEST_E_QUALIDADE.md` com nota do dono, **média ≥ 8 e nenhum item < 6**, mais o checklist de emoção de `EXPERIENCIA_E_NARRATIVA.md`. Jogadores de fora entram como achados observados. Com o dono como único testador, registre **"PORTÃO 2 — SÓ DONO"**. Só então a expansão modular.

**Vários agentes em paralelo** (padrão 2–3) só com contratos travados (manifesto de assets, lista de eventos sonoros, roteiro das cenas): `modulos/MODELOS_E_PARALELISMO.md`. Aprovações do dono: conceito/escopo, identidade visual canônica, mudanças grandes, custos, publicação.

## 10. QA, PLAYTEST E "CONCLUÍDO"

- **Técnico:** instalar, buildar, executar, ler logs, regressões.
- **Testes automáticos:** `npm test` (lógica do jogo) roda a cada push no GitHub Actions; bug achado vira teste novo. Tarefa só fecha com teste passando (`modulos/TAREFAS_REVISAO_TESTES.md`).
- **Revisão independente:** outro agente, que não escreveu, lê o código de cada tarefa (de preferência a outra IA).
- **Smoke test (jogo web):** quando houver navegador headless disponível, abrir o jogo, confirmar 0 erros no console, simular ~60 s de entradas e anexar screenshot. Rótulo **EXECUTADO (EMULADO)**; **não substitui** o aparelho.
- **Jogabilidade, arte/animação, UX, narrativa:** conforme o GDD, a bíblia visual e o roteiro das cenas.
- **Desempenho (ponto de partida):** média ≥ 55 FPS e carga ≤ 5 s no aparelho-alvo; ajuste por projeto em DECISOES.
- **Humano:** `modulos/PLAYTEST_E_QUALIDADE.md`. Teste automatizado não substitui playtest.
- **Teste no aparelho (dono):** agente em nuvem **não testa toque em Android**. Entregue o **link jogável de teste** (versão/commit visível na tela) e passos curtos, um por vez, e peça o resultado.

Para cada teste registre em `docs/TESTES.md`: versão, ambiente, o que foi executado, **PASSOU / FALHOU / NÃO TESTADO**, evidência.

**Portão 3 — Concluído** = abre e roda no alvo efetivamente testado; escopo prometido jogável; **menu, introdução, cutscenes, telas de vitória/derrota e final integrados**; assets integrados; sem falhas críticas conhecidas; testes automáticos passando; scorecard reaplicado ao jogo completo (média ≥ 8, nenhum < 6); smoke test e teste no aparelho feitos; docs verificáveis. **O ideal são 3 jogadores de fora observados.** Se o dono for o único testador (decisão dele), declare **"CONCLUÍDO — SÓ DONO"** e avise que falhas de clareza costumam aparecer só com gente de fora. Senão, diga o estágio real (protótipo, vertical slice, alpha, beta).

## 11. CONTINUIDADE ENTRE IAs, ENTREGA E TRAILER

**Fonte de verdade:** o repositório versionado (histórico do Git), não a memória de um chat nem só as anotações. As IAs **não compartilham memória**. Duas camadas: este repositório (método, templates, lições gerais comprovadas) e o repositório de **cada jogo** (código, assets, estado). Não transporte personagens ou decisões entre jogos.

**Documentos do jogo** (templates em `MODELO_PROJETO/`): `AGENTS.md` (canônico) · `CLAUDE.md` (fino) · `docs/ESTADO_ATUAL.md` · `DECISOES.md` · `HANDOFF.md` · `TAREFAS.md` · `GDD.md` · `BIBLIA_VISUAL.md` · `MANIFESTO_ASSETS.md` · `TESTES.md` · `APRENDIZADOS.md` · `.github/workflows/testes.yml`.

**Quem escreve onde** (detalhes em `modulos/COMUNICACAO_CLAUDE_CODEX.md`): em **revezamento** (uma IA por vez, o padrão) e no modo solo, a IA que está com a vez atualiza ESTADO, HANDOFF e TAREFAS no último commit da sessão. Em modo **colaborativo** (duas IAs ao mesmo tempo), a executora escreve **só** `docs/handoff/T-xxx.md` e a descrição do PR; o integrador atualiza TAREFAS e ESTADO no merge.

**Entrega:** projeto editável com instruções, assets com manifesto e proveniência, build jogável quando possível, relatório de testes. ZIP só se puder ser gerado e verificado. Sem segredos ou material sem direito de redistribuição em repositório público. Antes de publicar: `modulos/LANCAMENTO_E_RETENCAO.md`.

**Trailer/vídeo** só depois do vertical slice, com captura real: `modulos/VIDEO_TRAILER.md`.

**Retrospectiva curta** a cada marco: o que repetir, erro recorrente, mudança proposta, evidência. O que deu trabalho vira **skill** (com o "ok" do dono), para a IA não repetir o erro no próximo jogo. Atualize este método só com prática reutilizável e aprovada; versione no CHANGELOG. Pedido só de planejamento, revisão ou prompt **não altera** código nem documentos compartilhados sem autorização.

**Em chat novo:** verifique repositório e estado, comece pela seção 3 e conduza ao conceito, ao pacote visual, ao core loop e ao **prompt de execução para o agente de código** (Codex, Claude Code ou outro), autocontido e específico para a ideia.
