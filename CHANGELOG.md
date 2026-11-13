# CHANGELOG — METODOLOGIA UNIVERSAL DE GAMES COM IA

Registra **mudanças aprovadas e publicadas** na metodologia universal. Não confundir com mudanças em jogos específicos.

## [4.0] — 2026-11-13 (proposta via PR; vale após merge)

**Motivo:** revisão crítica da V3.1 (análise do Fable + conferência do Claude) e pesquisa de repositórios e práticas públicas (ver `modulos/FONTES.md`). A V3.1 tinha 33 KB, era repetitiva, centrada no Codex, com ordem que gastava arte antes de provar diversão, regra de Canvas inconsistente com Phaser, e sem as peças do fluxo atual.

- **Núcleo curto** `PROMPT_MESTRE.md` (nome estável, versão só no cabeçalho) + **módulos sob demanda** em `modulos/`.
- **Contrato de Evidência** único (EXECUTADO / SÓ LIDO / NÃO VERIFICADO); a nota da IA sobre o próprio trabalho é hipótese.
- **Nova ordem:** abertura → brief → conceito/hook → decisão técnica mínima → **prova do core loop (Portão 1)** → GDD → bíblia visual e assets → **vertical slice (Portão 2)** → QA/playtest → continuidade/entrega/trailer.
- **Qualidade mensurável:** módulo `PLAYTEST_E_QUALIDADE` com scorecard de 8 dimensões, limiares dos portões e protocolo de playtest (observação silenciosa, 3–5 jogadores, critérios mensuráveis). Limiares são ponto de partida.
- **Comunicação Claude↔Codex:** módulo `COMUNICACAO_CLAUDE_CODEX` — `AGENTS.md` canônico e `CLAUDE.md` fino (`@AGENTS.md`), ordem de serviço, fila `docs/TAREFAS.md`, branches por IA, PR, integrador, mensagem de entrega. Template `TAREFAS.md` em `MODELO_PROJETO/docs`.
- **Níveis de modelo** (criativo × execução) e **paralelismo** (3–4 agentes, teto de custo, integrador único).
- **Assets:** placeholders com nomes estáveis, proveniência por asset, estimativa de custo antes de gerar em lote.
- Módulos novos: arte/pixel art mobile, áudio, game feel (com pontos de partida), vídeo/trailer, fontes. Comercial e skills externas movidos do texto antigo; skills externas atualizadas (79 skills, mapa para Phaser).
- **Regra de sprites reformulada:** mantém a intenção do dono (proibido desenhar personagens/cenários por código no lugar de sprites reais), mas permite engines que usam Canvas/WebGL só como renderizador. **Requer confirmação do dono.**
- Neutro quanto ao agente ("prompt de execução para o agente de código"). Modo B: "fatia combinada e parar no checkpoint".
- Corrigidos "V3.0" no README, `ESTADO_ATUAL.md` do modelo e exemplo do REGISTRO.
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
