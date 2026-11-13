# AGENTS.md — Modelo para repositório de jogo (canônico, autossuficiente)

Projeto: **[NOME]** · Método: Prompt Mestre Universal **V4.0** — [URL DO REPOSITÓRIO CENTRAL, de preferência fixada em tag/commit]/PROMPT_MESTRE.md

## Regras essenciais (resumo; valem mesmo sem acesso ao repositório central)
1. Antes de agir: confira branch/commit e leia `docs/ESTADO_ATUAL.md`, `docs/DECISOES.md`, `docs/TAREFAS.md` e o handoff da tarefa.
2. **Evidência:** relatório de entrega com rótulos EXECUTADO (ou EXECUTADO (EMULADO)) / SÓ LIDO / NÃO VERIFICADO. Nunca invente testes, assets, logs ou resultados. Placeholder só se declarado provisório.
3. **Sprites:** proibido desenhar personagens/cenários por código no lugar de assets reais. Phaser/Pixi/Godot web como renderizador são permitidos.
4. **Qualidade:** Portão 1 (3 sim/não do dono), Portão 2 (scorecard, média ≥ 8, nenhum < 6), Portão 3 (concluído). A nota da IA é hipótese; vale a do dono.
5. **Assets:** nomes/caminhos estáveis, manifesto em `docs/MANIFESTO_ASSETS.md`, proveniência de cada asset de IA, estimativa de custo antes de gerar em lote.
6. **Modelos:** criativo = [modelo forte]; execução = [modelo barato]. Escalar só em decisão de design/arquitetura ou após 2 tentativas que não passaram no critério de pronto.
7. **Várias IAs:** uma tarefa = um responsável = uma branch (`claude/<id>-...`, `codex/<id>-...`, ou o nome imposto pela ferramenta). A IA executora **não edita** `docs/TAREFAS.md` nem `docs/ESTADO_ATUAL.md`: escreve `docs/handoff/T-xxx.md` e a descrição do PR. O integrador (indicado em DECISOES; padrão: o dono) atualiza no merge.
8. Não mude decisões aprovadas sem informar e registrar. Gastos, publicação e ações externas exigem autorização do dono.
9. Preserve código e assets aprovados; não recomece do zero nem troque engine sem justificar e aprovar.
10. Ao encerrar: commit/PR apenas com acesso e autorização; informe branch e hash/PR; sem isso, declare NÃO SINCRONIZADO.

## Projeto
- Build: [COMANDO BUILD] · Testes: [COMANDO TESTES]
- Alvo/engine/resolução-base: [preencher]
- Desempenho alvo (ponto de partida): média ≥ 55 FPS e carga ≤ 5 s no aparelho-alvo.

## Codex
[Instruções que valem só para o Codex, se houver.]
