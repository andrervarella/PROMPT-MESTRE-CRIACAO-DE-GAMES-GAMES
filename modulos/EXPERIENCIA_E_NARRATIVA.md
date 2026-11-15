# MÓDULO — Experiência, narrativa e emoção

Objetivo: o jogo não ser só jogabilidade fluida. Ele tem que **prender a pessoa desde o primeiro segundo**, contar uma história bonita e fazer sentir a emoção que o dono quer. Referência: seções 4, 9 e 10 do `PROMPT_MESTRE.md`.

> Preferência forte do dono, não regra cega: a IA pode propor outro jeito (motivo, 2 opções, recomendação). Em jogos anteriores, faltaram menu, introdução e história; este módulo existe para isso não se repetir.

## 1. A "embalagem" mínima de todo jogo completo

| Peça | O que é | Custo |
|---|---|---|
| **Tela inicial / menu** | título, arte principal com animação leve, Jogar, Opções (som), Créditos | baixo (imagens aprovadas + código) |
| **Introdução com a história** | 20–60 s que apresentam o mundo, o herói, o problema e o que está em jogo | baixo a médio |
| **Cutscenes curtas** entre fases ou nos marcos | 5–15 s cada, com propósito emocional (revelação, perda, vitória, ameaça) | médio (Fenaky) |
| **Telas de vitória e derrota** | com personalidade, não só texto | baixo |
| **Final** | fecha o arco emocional; recompensa quem chegou lá | baixo a médio |

Todas podem ser **puladas** com um toque, e o jogo funciona sem elas.

## 2. Hook e emoção (o que prende)

Na fase de conceito, a IA define junto com o dono:
- **Emoção central** (ex.: tensão, coragem, nostalgia, humor, vingança, superação) e **como ela muda** ao longo do jogo (arco: início → virada → clímax → final).
- **Gancho dos primeiros 10 segundos:** algo acontece logo (imagem forte, ameaça, mistério, frase de impacto). Nada de tela parada explicando regras.
- **Pergunta aberta:** o que a pessoa quer descobrir e só descobre jogando (curiosidade).
- **O que está em jogo:** algo que o herói pode perder, para o jogador se importar.
- **Recompensas emocionais** nos marcos (cutscene, revelação, nova habilidade) e não só pontos.
- **Primeiro minuto jogável bonito:** a introdução leva direto para a ação.

Sobre "neurociência da persuasão": o que funciona na prática é conhecido do cinema e do game design (impacto rápido, curiosidade, personagem com quem se importar, ritmo de tensão e alívio, recompensa). Use isso para **emocionar**, não para manipular: nada de truques de retenção artificial (notificações forçadas, timers falsos, punição por sair).

## 3. Economia (poucos tokens e créditos)

Para emocionar gastando pouco, nesta ordem:
1. **Cenas com imagens paradas animadas na engine** (pan lento, zoom, parallax, texto aparecendo, tremor, flash, música no ponto certo). Custa só algumas imagens aprovadas e código. É o padrão.
2. **Painéis de quadrinho** (3–6 imagens) com texto curto.
3. **Vídeo gerado (Fenaky)** só nos 1–3 momentos mais importantes (introdução, clímax, final), com o personagem aprovado como referência. Custo mostrado antes.

Texto: frases curtas, poucas palavras por tela, tom combinado com a emoção. Música e silêncio fazem metade do trabalho.

## 4. Onde isso entra no processo

- **Conceito (seção 4):** emoção central, arco, gancho dos 10 s, história curta e **roteiro das cenas** (lista: cena, duração, emoção, imagens necessárias, música).
- **Portão V:** a tela inicial e a história já vão para aprovação; se houver introdução, 1 imagem-chave dela também.
- **Vertical slice (Portão 2):** menu + introdução + primeira fase completas, com a emoção funcionando.
- **Portão 3:** toda a embalagem do item 1 integrada.

## 5. Checklist rápido (o dono responde)
1. Nos primeiros 10 segundos, algo me pegou?
2. Eu sei quem é o herói e o que ele pode perder?
3. Senti a emoção que eu queria em algum momento?
4. Quero ver o que vem depois?
