# AGENTS.md — Modelo para repositório de jogo (canônico, autossuficiente)

Projeto: **[NOME]** · Método: Prompt Mestre Universal **V4.1** — [URL DO REPOSITÓRIO CENTRAL, de preferência fixada em tag/commit]/PROMPT_MESTRE.md

## Regras essenciais (resumo; valem mesmo sem acesso ao repositório central)
1. **Antes de agir (vale ao assumir um jogo que outra IA mexeu):** liste branches e PRs abertos; se a outra IA deixou PR aberto ou usa a branch `dev`, o estado mais recente é o dela, não a `main`. Compare o último commit com o **commit-base** de `docs/ESTADO_ATUAL.md` (leitura obrigatória, curta). Se houver commits depois, leia o que mudaram **antes** de editar. Crie sua branch a partir do último commit e edite sempre sobre a versão recém-lida dos arquivos; nunca reescreva arquivo inteiro de uma cópia antiga. Antes de enviar, confira de novo se a branch não andou. Em dúvida ou contradição: pare e pergunte ao dono. `DECISOES.md`, `TAREFAS.md` e o handoff só se a tarefa tocar neles. Vale o Git, não as anotações.
2. **Evidência:** relatório de entrega com rótulos EXECUTADO (ou EXECUTADO (EMULADO)) / SÓ LIDO / NÃO VERIFICADO. Nunca invente testes, assets, logs ou resultados. Placeholder só se declarado provisório.
3. **Sprites:** proibido desenhar personagens/cenários por código, inclusive como placeholder. Placeholder = imagem-conceito aprovada, estática (e o lote-piloto aprovado, em jogo de ação). Phaser/Pixi/Godot web como renderizador são permitidos; animar imagens aprovadas é permitido.
4. **Visual primeiro:** antes de gerar os assets finais, crie o **Pacote de Aprovação Visual** mínimo (tela inicial com animação leve planejada, personagem, rival, cenário/mapa, HUD) e a **história curta**, mostre uma imagem por vez e espere o **Portão V** (3 sim/não do dono). Em jogo de ação, depois do V gere o **lote-piloto de animação** (~12 quadros) antes do Portão 1. A produção completa de sprites só começa depois dos Portões V e 1. O personagem aprovado fica no repositório (ex.: `concept/`) como referência fixa para qualquer IA.
5. **Qualidade:** Portão 1 (3 sim/não do dono), Portão 2 (scorecard, média ≥ 8, nenhum < 6), Portão 3 (concluído; o ideal são 3 jogadores de fora; se só o dono testa, declarar "CONCLUÍDO — SÓ DONO"). A nota da IA é hipótese; vale a do dono.
6. **Assets:** nomes/caminhos estáveis, manifesto em `docs/MANIFESTO_ASSETS.md`, proveniência de cada asset de IA, estimativa de custo antes de gerar em lote, lotes reprovados registrados.
7. **Modelos:** criativo = [modelo forte]; execução = [modelo barato ou o que o dono escolheu]. Escalar só em decisão de design/arquitetura ou após 2 tentativas que não passaram no critério de pronto.
8. **Quem escreve onde:** em **revezamento** (uma IA por vez, o padrão), a IA com a vez atualiza `docs/ESTADO_ATUAL.md` e `docs/HANDOFF.md` no último commit da sessão e trabalha na branch `dev`; o merge na `main` acontece nos portões, com o dono. Em **colaborativo** (duas IAs ao mesmo tempo), uma tarefa = um responsável = uma branch (`claude/<id>-...`, `codex/<id>-...`, ou o nome imposto pela ferramenta); a executora **não edita** `docs/TAREFAS.md` nem `ESTADO_ATUAL.md`: escreve `docs/handoff/T-xxx.md` e a descrição do PR, e o integrador (padrão: o dono) atualiza no merge.
9. Não mude decisões aprovadas sem informar e registrar. Gastos, publicação e ações externas exigem autorização do dono. Preserve código e assets aprovados; não recomece do zero nem troque engine sem justificar e aprovar. **Se achar que outro caminho deixa o jogo melhor, avise e sugira ao dono** (motivo, 2 opções, recomendação); o fluxo padrão não é trava.
10. **Ao parar de trabalhar:** faça commit e push na branch de trabalho (autorização em `DECISOES.md`, DEC-001) e deixe no handoff o **commit-base** (o último commit antes desta atualização), os arquivos alterados, o que ficou pela metade e o próximo passo. Sem commit/push publicado, declare NÃO SINCRONIZADO.

## Projeto
- Build: [COMANDO BUILD] · Testes: [COMANDO TESTES]
- Alvo/engine/resolução-base: [preencher]
- **Link jogável de teste:** [URL fixa — GitHub Pages/Vercel/itch]. Todo checkpoint e todo portão entregam esse link atualizado, com versão/commit visível na tela.
- Áudio: música durante a produção; efeitos sonoros e vozes por último (som provisório ou silêncio até lá; o código toca pelo nome do evento).
- Desempenho alvo (ponto de partida): média ≥ 55 FPS e carga ≤ 5 s no aparelho-alvo.

## Codex
[Instruções que valem só para o Codex, se houver.]
