# MÓDULO — Modo "jogo completo" (jeito padrão do dono)

O dono costuma pedir o **jogo inteiro de uma vez**, aprovando só o começo (imagens-amostra e história) e deixando a IA tocar o resto. Este módulo diz como fazer isso sem perder qualidade. Referência: seções 6, 8 e 9 do `PROMPT_MESTRE.md`.

## Fluxo

0. **O dono entrega:** a ideia, a emoção que quer causar em quem joga, o estilo e as referências (imagens, jogos).
1. **IA (nível CRIATIVO):** conceito de 1 página, **história curta** (5–10 linhas) e a **lista do que é "jogo completo"** (fases, telas, personagens, mapa). Registrar no `docs/GDD.md`. Esse escopo fica **fechado**: ideia nova vai para `docs/PROXIMO_JOGO.md`.
2. **Aprovação inicial (Portão V):** poucas imagens-amostra, uma por vez (tela inicial com animação leve planejada, personagem, rival, cenário/mapa, HUD) **mais a história**. O dono responde "gostei" ou "ajustar". Veja `PACOTE_DE_APROVACAO_VISUAL.md`.
3. **Depois do "gostei", a IA toca em sequência, sem pedir aprovação a cada passo:** lote-piloto de animação (jogo de ação) → prova do core loop → GDD travado → assets completos em lotes → código do jogo inteiro → **música** → integração → QA. Paradas permitidas: Portão 1 (curto), custos acima do combinado, decisão grande de design e bloqueios.
4. **Áudio em duas fases** (veja `AUDIO.md`): música durante a produção; **efeitos sonoros e vozes por último**, quando o dono der acesso ao ElevenLabs (ou outra ferramenta). Até lá, o jogo roda com som provisório ou em silêncio, sem quebrar.
5. **Testes:** o dono é o único testador. A IA entrega o **link jogável de teste**, o dono joga e relata em passos curtos; a IA corrige. Fica registrado como **"SÓ DONO"** (ver `PLAYTEST_E_QUALIDADE.md`).

## Por que manter o Portão 1 mesmo no jogo completo
Se o controle ou o loop não forem bons, todos os assets e todo o código serão refeitos. Jogar 5–10 minutos uma amostra pequena custa quase nada perto disso. É a única parada obrigatória depois do Portão V.

## Risco do testador único (avisar o dono, sem bloquear)
Quem fez o jogo ou o conhece tende a não enxergar o que confunde um jogador novo (instrução, primeiro minuto, dificuldade). A IA compensa assim: confere a clareza do começo com um **checklist** (o primeiro objetivo aparece em ~30 s? os controles são dedutivos?), e sugere ao dono mostrar o jogo para uma pessoa de fora **se for fácil**, mas isso não é exigência.

## Liberdade de propor outro caminho
Este é o jeito padrão do dono, não uma trava. **Qualquer IA (Claude, Codex, outra) deve avisar e sugerir mudança** quando achar que o jogo fica melhor por outro caminho (outra ordem, mais amostras, cortar escopo, trocar de ferramenta). Como propor: o motivo em 1 frase, 2 opções e uma recomendação. Só muda com o "ok" do dono, e a decisão vai para `docs/DECISOES.md`.
