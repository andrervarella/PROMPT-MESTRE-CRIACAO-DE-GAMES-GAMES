# CHANGELOG — METODOLOGIA UNIVERSAL DE GAMES COM IA

Registra **mudanças aprovadas e publicadas** na metodologia universal. Não confundir com mudanças em jogos específicos.

## [4.0] — 2026-11-13 (proposta via PR; vale após merge)

**Motivo:** revisão crítica da V3.1 (análise do Fable + conferência do Claude). Documento de 33 KB, repetitivo, centrado no Codex, com ordem que gastava arte antes de provar diversão, regra de Canvas inconsistente com Phaser, e sem as peças do fluxo atual (níveis de modelo, paralelismo, áudio, vídeo, game feel, pixel art mobile).

- **Núcleo curto** `PROMPT_MESTRE.md` (nome estável, versão só no cabeçalho) + **módulos sob demanda** em `modulos/`.
- **Contrato de Evidência** único (EXECUTADO / SÓ LIDO / NÃO VERIFICADO) no lugar de dezenas de repetições de "não invente".
- **Nova ordem:** abertura → brief → conceito/hook → decisão técnica mínima → **prova do core loop com portão de diversão** → GDD → bíblia visual e assets → vertical slice → QA → continuidade/entrega/trailer.
- **Níveis de modelo** (criativo × execução) e **regras de paralelismo** (3–4 agentes, teto de custo, integrador único).
- Novos módulos: arte/pixel art mobile, áudio, game feel, vídeo/trailer.
- **Regra de sprites reformulada:** mantém a intenção do dono (proibido desenhar personagens/cenários por código no lugar de sprites reais), mas permite engines que usam Canvas/WebGL só como renderizador (Phaser, PixiJS, Godot web). **Requer confirmação do dono.**
- Neutro quanto ao agente: "prompt de execução para o agente de código" (não só Codex).
- Modo B: "produza a fatia combinada e pare no checkpoint" (antes: "o máximo concluível"), para controlar custo.
- Bloco "Teste no aparelho (dono)" no QA.
- Corrigidos: rótulo "V3.0" no README, `ESTADO_ATUAL.md` do modelo e exemplo do REGISTRO.
- Compatibilidade: V3.1 e V3.0 **preservadas** na raiz como histórico.
- Commit/PR: ver o PR `claude/protocolo-v4-0`.

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
