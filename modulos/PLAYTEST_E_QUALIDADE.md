# MÓDULO — Playtest e scorecard de qualidade

Objetivo: tornar "o jogo está bom?" **operável e mensurável**. Usado nos Portões 1, 2 e 3 (seções 6, 9 e 10 do `PROMPT_MESTRE.md`).

> Limiares são **ponto de partida**, baseados em práticas comuns de playtest indie. Ajuste por projeto e registre em `docs/DECISOES.md`.

## Quem pontua

- **Quem dá a nota é o dono.** A IA só propõe nota **com evidência** (ex.: "3 de 4 jogadores não acharam o botão de pausa"). Jogador não dá nota em 8 dimensões: ele **joga e é observado**.
- Jogadores reais entram como **achados observados**. Sem jogadores, registre "SÓ DONO" (aceito no Portão 2; **não** no Portão 3).
- Nota sem evidência vale NÃO VERIFICADO.

## Portão 1 — prova do core loop (3 perguntas sim/não ao dono)

1. Entendi o que fazer sem ajuda?
2. O controle obedeceu?
3. Joguei de novo sem ninguém pedir?

**Três "sim" passam.** A pergunta 3 vale mais quando feita a **1 pessoa que nunca viu o jogo** (observe se ela recomeça sozinha). Jogo de ação: use o lote-piloto de animação, não só imagem parada. Reprovou 3 vezes: critério de descarte em `ESCOPO_E_ORCAMENTO.md`.

## Portão 2 e 3 — scorecard 0–10 (nota do dono)

| # | Dimensão | Pergunta |
|---|---|---|
| 1 | Clareza | Em ~30 s entende o objetivo e, em até ~3 min, os controles, sem texto longo? |
| 2 | Controle / game feel | Responde na hora e "parece bom" no celular? |
| 3 | Core loop | Dá vontade de jogar de novo? |
| 4 | Hook e identidade | Um frame/GIF é reconhecível e chama atenção? |
| 5 | Legibilidade | Silhuetas, HUD e contraste funcionam em tela pequena? |
| 6 | Coerência audiovisual | Arte, som e UI parecem do mesmo jogo? |
| 7 | Estabilidade | FPS e carga dentro do alvo, sem crash no aparelho? |
| 8 | Dificuldade e progressão | Entende por que perdeu e sente evolução? |

**Âncoras:** **6** = funciona, com atrito. **8** = sem atrito observado. **10** = jogador elogia ou quer mostrar espontaneamente.

**Portão 2 (vertical slice):** média ≥ 8 e nenhum item < 6.
**Portão 3 (Concluído):** mesmo critério, aplicado ao jogo completo, com smoke test e teste no aparelho feitos e **no mínimo 3 jogadores de fora observados**. Sem eles, o estágio declarado é **beta**.

## Protocolo de playtest

1. **Quem:** 3 a 5 pessoas do público-alvo (poucos testes já mostram os problemas mais comuns). Quem não conhece o jogo vale mais que amigo próximo.
2. **Preparação:** 1 ou 2 dúvidas por sessão (ex.: "entendem o pulo duplo?") e um **checklist de observação**.
3. **Durante:** **observe em silêncio**; não explique nem defenda o jogo. Pode pedir que falem em voz alta o que pensam. Evite perguntas que induzem a resposta.
4. **Anote:** tempo até a primeira ação; onde travou (> ~90 s é achado crítico); pedidos de ajuda; o que tentaram e o jogo não permite; se recomeçaram sozinhos.
5. **Meta de partida:** a maioria entende os controles em até 3 minutos sem explicação (e o objetivo em ~30 s). Com 3–5 jogadores, trate como sinal, não estatística.
6. **Depois:** só mude algo quando o **padrão** aparecer em 2 ou mais jogadores. Comportamento vale mais que elogio.
7. **Registre** em `docs/TESTES.md`: data, versão, aparelho, jogadores, achados, decisão.

## Teste no celular do dono (Android) — formato curto

A IA entrega o **link jogável de teste** (versão/commit visível na tela) e **um passo por vez**:
1. Abrir o link da versão X.
2. Jogar 2 minutos sem ajuda.
3. Responder: travou? O controle respondeu bem? Quer jogar de novo?
4. Enviar print/vídeo curto se algo estranho aparecer.

Fontes: `FONTES.md`.
