# CHANGELOG — METODOLOGIA UNIVERSAL DE GAMES COM IA

Registra **mudanças aprovadas e publicadas** na metodologia universal. Não confundir com mudanças em jogos específicos.

## [4.0] — 2026-11-13 (proposta via PR; vale após merge)

**Motivo:** revisão crítica da V3.1 (duas rodadas de análise do Fable + conferência do Claude), pesquisa de repositórios e práticas públicas (ver `modulos/FONTES.md`) e pedidos do dono. A V3.1 tinha 33 KB, era repetitiva, centrada no Codex, com ordem que gastava arte antes de provar diversão, regra de Canvas inconsistente com Phaser, e sem as peças do fluxo atual.

- **Núcleo curto** `PROMPT_MESTRE.md` (nome estável, versão só no cabeçalho) + **módulos sob demanda** em `modulos/`. Entrada única: sempre a seção 1.
- **Pacote de Aprovação Visual (Portão V):** antes de gerar os assets finais, o mínimo de imagens-conceito (tela inicial com animação leve planejada, personagem, rival, cenário/mapa, HUD), uma por vez, aprovadas pelo dono. Produção completa de sprites só após os Portões V e 1. Tela inicial animada é parte do vertical slice.
- **Regra de sprites confirmada pelo dono e endurecida:** proibido desenhar personagens/cenários por código, **inclusive como placeholder**; placeholder = imagem-conceito aprovada estática. Engines que usam Canvas/WebGL só como renderizador (Phaser, PixiJS, Godot web) são permitidas; animar imagens aprovadas é permitido.
- **Contrato de Evidência** único (EXECUTADO / EXECUTADO (EMULADO) / SÓ LIDO / NÃO VERIFICADO), aplicado ao relatório de entrega; a nota da IA sobre o próprio trabalho é hipótese.
- **Nova ordem com portões:** conceito → decisão técnica → Portão V → Portão 1 (prova do core loop) → GDD → produção de assets → Portão 2 (vertical slice) → QA/playtest → Portão 3 (concluído).
- **Qualidade operável:** Portões V e 1 = 3 perguntas sim/não ao dono; Portões 2 e 3 = scorecard de 8 dimensões com nota do dono, âncoras (6/8/10), média ≥ 8 e nenhum < 6; jogadores entram como achados observados; modo "SÓ DONO". Limiares são ponto de partida.
- **Smoke test** em navegador headless para jogos web (rótulo EMULADO) e números iniciais de desempenho (≥ 55 FPS, carga ≤ 5 s).
- **Comunicação Claude↔Codex:** `AGENTS.md` canônico e autossuficiente + `CLAUDE.md` fino (`@AGENTS.md`); ordem de serviço; fila `docs/TAREFAS.md`; **escritor único** dos arquivos compartilhados (executora escreve `docs/handoff/T-xxx.md`, integrador atualiza TAREFAS/ESTADO); branches por IA (ou o nome imposto pela ferramenta); integrador padrão = dono; regra para chats.
- **Templates novos** em `MODELO_PROJETO/docs`: `TAREFAS`, `GDD`, `MANIFESTO_ASSETS`, `TESTES`, `handoff/T-000-exemplo`.
- **Níveis de modelo** (criativo × execução) e **paralelismo** (3–4 agentes, teto de custo, integrador único).
- **Assets:** nomes estáveis, proveniência por asset, estimativa de custo antes de gerar em lote, lotes reprovados registrados.
- Módulos novos: pacote de aprovação visual, playtest e qualidade, comunicação, arte/pixel art mobile, áudio, game feel (pontos de partida), vídeo/trailer, fontes. Comercial e skills externas movidos do texto antigo; skills externas atualizadas (79 skills, mapa para Phaser).
- Neutro quanto ao agente ("prompt de execução para o agente de código"). Modo B: "fatia combinada e parar no checkpoint".
- Corrigidos "V3.0" no README, `ESTADO_ATUAL.md` do modelo e exemplo do REGISTRO.
- Compatibilidade: V3.1 e V3.0 **preservadas** na raiz como histórico.
- **Não comprovado:** nenhum jogo rodou ainda com a V4.0. Os primeiros projetos devem devolver aprendizados ao método (`APRENDIZADOS.md`).
- Commit/PR: preencher com o hash do merge.

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
