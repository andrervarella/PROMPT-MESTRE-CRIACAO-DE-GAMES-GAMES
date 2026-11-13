# MÓDULO — Playtest e scorecard de qualidade

Objetivo: tornar "o jogo está bom?" **mensurável**. Usado nos Portões 1 e 2 e antes de declarar "Concluído" (seções 6, 9 e 10 do `PROMPT_MESTRE.md`).

> Os limiares abaixo são **ponto de partida**, baseados em práticas comuns de playtest indie. Ajuste com a experiência de cada projeto e registre a mudança em `docs/DECISOES.md`. A nota da IA é hipótese; vale a do dono e a de jogadores reais.

## Scorecard (0–10 por item)

| # | Dimensão | Pergunta |
|---|---|---|
| 1 | Clareza | Em ~30 s o jogador entende o que fazer, sem texto longo? |
| 2 | Controle / game feel | O controle responde na hora e "parece bom" no celular? |
| 3 | Core loop | Dá vontade de jogar de novo logo após perder/ganhar? |
| 4 | Hook e identidade | Um único frame/GIF é reconhecível e chama atenção? |
| 5 | Legibilidade | Silhuetas, HUD e contraste funcionam em tela pequena? |
| 6 | Coerência audiovisual | Arte, som e UI parecem do mesmo jogo? |
| 7 | Estabilidade | FPS estável, carga rápida, sem crash no aparelho-alvo? |
| 8 | Dificuldade e progressão | O jogador entende por que perdeu e sente evolução? |

**Portão 1 (prova do core loop):** itens 1, 2 e 3 com nota ≥ 7.
**Portão 2 (vertical slice):** média ≥ 8 e nenhum item < 6.

Cada nota precisa de **evidência**: o que foi observado (ex.: "3 de 4 jogadores não acharam o botão de pausa"). Nota sem evidência vale NÃO VERIFICADO.

## Protocolo de playtest

1. **Quem:** 3 a 5 pessoas do público-alvo. Poucos testes já mostram os problemas mais comuns. Quem não conhece o jogo vale mais que amigo próximo.
2. **Preparação:** escolha 1 ou 2 dúvidas por sessão (ex.: "entendem o pulo duplo?"). Escreva um **checklist de observação**.
3. **Durante:** **observe em silêncio** e não explique nem defenda o jogo. Peça, se quiser, que falem em voz alta o que pensam. Evite perguntas que induzem a resposta.
4. **Anote:** tempo até a primeira ação; onde travou (mais de ~90 s é achado crítico); pedidos de ajuda; o que tentou e o jogo não permite; se recomeçou sozinho (sinal forte de core loop bom).
5. **Critérios mensuráveis** (ponto de partida): ~90% entendem os controles em até 3 minutos sem explicação; todos usam as mecânicas básicas logo no início.
6. **Depois:** só mude algo quando o **padrão** aparecer em 2 ou mais jogadores. Elogio não é dado; comportamento é.
7. **Registre** em `docs/TESTES.md` (ou ESTADO_ATUAL): data, versão, aparelho, jogadores, achados, decisão.

## Teste no celular do dono (Android) — formato curto

A IA entrega **um passo por vez**:
1. Abrir o link/APK da versão X.
2. Jogar 2 minutos sem ajuda.
3. Responder: travou em algum ponto? O controle respondeu bem? Quer jogar de novo?
4. Enviar print/vídeo curto se algo estranho aparecer.

## Fontes

Ver `FONTES.md` (artigos de playtest e game feel consultados em 2026-11-13).
