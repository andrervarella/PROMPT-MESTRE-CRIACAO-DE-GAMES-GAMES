# CHANGELOG — METODOLOGIA UNIVERSAL DE GAMES COM IA

Registra **mudanças aprovadas e publicadas** na metodologia universal. Não confundir com mudanças em jogos específicos.

## [4.1] — 2026-11-13 (PR #2)

**Motivo:** pedido do dono de poder trocar de IA a qualquer momento sem uma sobrescrever a outra; revisão independente do Fable (média 6,6 de 10 na V4.0 com o PR #2 parcial; as 4 lacunas P0 e as P1 foram aplicadas aqui); e o jeito de trabalhar do dono (jogo completo de uma vez, testador único, áudio em duas fases). Nenhuma nota nova foi dada à V4.1.

- **Troca livre de IA** (`COMUNICACAO` seção 8) e **regra anti-sobrescrita**: vale o histórico do Git, não as anotações; listar branches e PRs abertos; comparar com o commit-base; editar sobre a versão recém-lida; parar e perguntar em caso de contradição.
- **Revezamento** (uma IA por vez) como modo padrão: a IA com a vez atualiza ESTADO e HANDOFF e usa a branch `dev`; merge na `main` nos portões. O modo colaborativo (executora não edita ESTADO/TAREFAS) só vale com duas IAs ao mesmo tempo. Corrige a contradição entre README/AGENTS e COMUNICACAO.
- **Modo "jogo completo"** (`MODO_JOGO_COMPLETO`): o dono aprova imagens-amostra e história no começo; depois a IA toca o jogo inteiro em sequência, parando só no Portão 1, em custos e em bloqueios. Escopo do jogo completo fechado no início.
- **Abertura a sugestões:** o fluxo padrão não é trava; qualquer IA avisa e sugere outro caminho (motivo, 2 opções, recomendação) quando achar que o jogo fica melhor; muda só com o "ok" do dono e registro em DECISOES.
- **Testador único (dono) aceito** em todos os portões, registrado como "SÓ DONO" (Portão 3: "CONCLUÍDO — SÓ DONO", com aviso do risco de clareza). Jogadores de fora seguem como o ideal (3) e valem mais quando existirem.
- **Áudio em duas fases:** música durante a produção; efeitos sonoros e vozes por último (ElevenLabs ou outra ferramenta, com acesso dado pelo dono). O código toca pelo nome do evento, então trocar o arquivo não muda o código.
- **História curta** passa a fazer parte da aprovação inicial.
- **Lote-piloto de animação** antes do Portão 1 em jogo de ação (~12 quadros), porque imagem estática não prova que o controle obedece.
- **Link jogável de teste** definido na decisão técnica e entregue em todo checkpoint.
- **Novos módulos:** `MODO_JOGO_COMPLETO`, `ESCOPO_E_ORCAMENTO` (frase do jogo, pergunta do protótipo, lista de cortes, critério de descarte, orçamento por fase, tags de marco; números são proposta sem fonte) e `LANCAMENTO_E_RETENCAO`.
- **Templates:** novo `BIBLIA_VISUAL.md`; `ESTADO_ATUAL` com **commit-base** (um arquivo não contém o hash do commit que o grava), estágios mapeados aos portões e limite de ~40 linhas; `DECISOES` com DEC-001 (autorização de push na branch de trabalho, proposta); `TESTES` com coluna de notas esclarecida; abertura de sessão mais barata (ESTADO obrigatório, resto sob demanda).
- **Consistência:** agentes em paralelo padrão 2–3 (a 4.0 dizia 3–4 antes de ajustar aos planos iniciais); clareza "~30 s o objetivo, ~3 min os controles"; `GAME_FEEL` sem conflito com a regra de não desenhar por código; execução no modelo escolhido pelo dono tratada como exceção explícita; `FONTES` com URLs.
- **Não comprovado:** nenhum jogo rodou ainda com a V4.x. Claims sobre leitura de AGENTS.md pelo Claude Code seguem de fonte secundária. Tetos de orçamento não têm fonte.
- Commit/PR: PR #2.

## [4.0] — 2026-11-13 (publicada na `main` via PR #1, commit de merge e1c77f7)

**Motivo:** revisão crítica da V3.1 (duas rodadas de análise do Fable + conferência do Claude), pesquisa de repositórios e práticas públicas (ver `modulos/FONTES.md`) e pedidos do dono. A V3.1 tinha 33 KB, era repetitiva, centrada no Codex, com ordem que gastava arte antes de provar diversão, regra de Canvas inconsistente com Phaser, e sem as peças do fluxo atual.

- **Núcleo curto** `PROMPT_MESTRE.md` (nome estável, versão só no cabeçalho) + **módulos sob demanda** em `modulos/`. Entrada única: sempre a seção 1.
- **Pacote de Aprovação Visual (Portão V):** antes de gerar os assets finais, o mínimo de imagens-conceito (tela inicial com animação leve planejada, personagem, rival, cenário/mapa, HUD), uma por vez, aprovadas pelo dono. Produção completa de sprites só após os Portões V e 1. Tela inicial animada é parte do vertical slice.
- **Regra de sprites confirmada pelo dono e endurecida:** proibido desenhar personagens/cenários por código, **inclusive como placeholder**; placeholder = imagem-conceito aprovada estática. Engines que usam Canvas/WebGL só como renderizador (Phaser, PixiJS, Godot web) são permitidas; animar imagens aprovadas é permitido.
- **Contrato de Evidência** único (EXECUTADO / EXECUTADO (EMULADO) / SÓ LIDO / NÃO VERIFICADO), aplicado ao relatório de entrega; a nota da IA sobre o próprio trabalho é hipótese.
- **Nova ordem com portões:** conceito → decisão técnica → Portão V → Portão 1 (prova do core loop) → GDD → produção de assets → Portão 2 (vertical slice) → QA/playtest → Portão 3 (concluído).
- **Qualidade operável:** Portões V e 1 = 3 perguntas sim/não ao dono; Portões 2 e 3 = scorecard de 8 dimensões com nota do dono, âncoras (6/8/10), média ≥ 8 e nenhum < 6; jogadores entram como achados observados; modo "SÓ DONO". Limiares são ponto de partida.
- **Smoke test** em navegador headless para jogos web (rótulo EMULADO) e números iniciais de desempenho (≥ 55 FPS, carga ≤ 5 s).
- **Comunicação Claude↔Codex:** `AGENTS.md` canônico e autossuficiente + `CLAUDE.md` fino (`@AGENTS.md`); ordem de serviço; fila `docs/TAREFAS.md`; escritor único dos arquivos compartilhados; branches por IA (ou o nome imposto pela ferramenta); integrador padrão = dono.
- **Templates novos** em `MODELO_PROJETO/docs`: `TAREFAS`, `GDD`, `MANIFESTO_ASSETS`, `TESTES`, `handoff/T-000-exemplo`.
- **Níveis de modelo** (criativo × execução) e **paralelismo** (ajustado aos planos iniciais do dono: 2–3 agentes por padrão, teto de custo, integrador único). Codex: o dono usa o modelo mais forte do plano.
- **Assets:** nomes estáveis, proveniência por asset, estimativa de custo antes de gerar em lote, lotes reprovados registrados.
- Módulos novos: pacote de aprovação visual, playtest e qualidade, comunicação, arte/pixel art mobile, áudio, game feel (pontos de partida), vídeo/trailer, fontes. Comercial e skills externas movidos do texto antigo; skills externas atualizadas (79 skills, mapa para Phaser).
- Neutro quanto ao agente ("prompt de execução para o agente de código"). Corrigidos "V3.0" no README, `ESTADO_ATUAL.md` do modelo e exemplo do REGISTRO.
- Compatibilidade: V3.1 e V3.0 **preservadas** na raiz como histórico.
- **Não comprovado:** nenhum jogo rodou ainda com a V4.0.
- Commit/PR: PR #1 (commit de merge e1c77f7).

## [3.1] — 2026-11-10

- Adicionada como referência técnica pública, opcional e não automática, a biblioteca Awesome GameDev Agent Skills.
- Regra de consulta seletiva das skills; leitura pela web não equivale a instalação.
- Reforçadas verificações de documentação oficial, licenças, permissões e execução de ferramentas externas.

## [3.0] — 2026-11-10

- Publicado o Prompt Mestre Universal V3.0 como referência canônica.
- Fluxo Modo A (descobrir e preparar) e Modo B (executar).
- Protocolo de continuidade ChatGPT ↔ Claude ↔ Codex.
- Adicionados `AGENTS.md`, `CLAUDE.md` e `MODELO_PROJETO/`.
- Separação: metodologia aqui; código e estado de cada jogo em seu repositório.

## Como registrar futuras atualizações

Para cada versão, anote data, mudança, justificativa, impacto/compatibilidade, arquivos e commit/PR. Não atualize a referência canônica com sugestão não validada. Com outro agente trabalhando, proponha por branch e PR.
