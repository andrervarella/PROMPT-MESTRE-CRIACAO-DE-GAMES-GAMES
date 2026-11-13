# MÓDULO — Pacote de Aprovação Visual (Portão V)

Objetivo: o dono **vê e aprova o conceito visual com o mínimo de imagens** antes de a IA gastar tempo e crédito criando todos os assets. Referência: seções 6 e 8 do `PROMPT_MESTRE.md`.

## Quando
Depois do conceito (seção 4) e da decisão técnica (seção 5). **Antes** da prova do core loop e de qualquer produção completa de sprites.

## Conteúdo mínimo (orçamento: até ~6 imagens, só o necessário)

| # | Imagem | Para quê |
|---|---|---|
| 1 | **Tela inicial** (arte principal) com título/logo, personagem(s) e clima | Mostrar o conceito do jogo de relance |
| 2 | **Personagem principal**: 1 folha de modelo (visões principais, 2–3 poses-chave, paleta) | Aprovar o visual do herói |
| 3 | **Rival/inimigo principal** (1 imagem), se houver | Aprovar o antagonista |
| 4 | **Cenário principal** (1 imagem) e, se o jogo tiver mapa ou fases, o **mapa** (1 imagem esquemática) | Aprovar o mundo |
| 5 | **Mock de HUD/tela de jogo** na proporção do celular do alvo | Ver legibilidade e disposição |

Mais imagens só se o dono pedir. Menos, se o jogo não precisar (ex.: sem rival, sem mapa).

## Tela inicial (todo jogo 2D tem)
- Apresentação do jogo: título, personagem(s), atmosfera, botão de jogar.
- **Animação leve** planejada junto da imagem (ex.: personagem em idle, fundo com parallax, partículas, botão pulsando). Descreva em 2–4 linhas no pacote.
- A animação final é feita **animando as imagens aprovadas dentro da engine** (movimento, parallax, partículas). Isso não é desenhar personagem por código.

## Regras
1. **Imagens estáticas**, na proporção do alvo, coerentes com a **direção de estilo definida no conceito** (estilo, paleta, resolução-base). A bíblia visual completa só é consolidada depois dos Portões V e 1.
2. Nomes e caminhos estáveis, por exemplo `concept/tela_inicial.png`, **dentro do repositório** (para qualquer IA usar como referência). Registrar no `docs/MANIFESTO_ASSETS.md` com status **provisório** e a **proveniência** (ferramenta, prompt, seed, data).
3. Se usar serviço pago, mostrar **estimativa de custo** e pedir confirmação antes.
4. Dizer qual ferramenta de imagem foi realmente usada; não fingir.

## Ciclo de aprovação
1. A IA mostra **uma imagem por vez**, com 1 linha dizendo o que olhar.
2. O dono responde por imagem: **"gostei"** ou **"ajustar: ..."**.
3. A IA ajusta e mostra de novo. Ponto de partida: no máximo 3 rodadas por imagem; passando disso, repensar a direção em vez de insistir.
4. Registrar em `docs/DECISOES.md` o que foi **reprovado e por quê**, para não repetir o erro.

## Portão V (o dono responde sim/não)
1. Entendi o conceito do jogo só olhando as imagens?
2. O personagem principal ficou do jeito que eu quero?
3. O estilo (cores e estética) combina com o jogo?

**Três "sim" passam.** Então o personagem e o estilo aprovados viram a **identidade visual canônica**: registrar em DECISOES e na `docs/BIBLIA_VISUAL.md`, e usar a imagem aprovada como **referência fixa** em todo pedido seguinte, seja qual for a IA.

## Lote-piloto de animação (jogo de ação), depois do Portão V
Sem movimento real, o Portão 1 não responde "o controle obedeceu?". Por isso, **antes** da prova do core loop:
- Gere só o mínimo de quadros do personagem principal para o **verbo central** (ex.: parado + 1 ataque + 1 dano; teto de ~12 quadros). Não é produção em massa.
- Serve a dois fins: testar o controle no Portão 1 e **provar que a ferramenta mantém o personagem** entre quadros (identidade, proporção, emenda do loop).
- Registre no manifesto como piloto/provisório. Se o lote falhar **2 vezes**, troque de ferramenta ou de estilo antes de gastar mais.
- Jogos sem ação em tempo real (puzzle, texto etc.) podem dispensar o lote-piloto; diga isso na decisão.

## Depois do Portão V
- **Prova do core loop (Portão 1):** usa as imagens aprovadas (e o lote-piloto, se houver) como placeholders de nome estável. Sem personagem desenhado por código. Caixas de hitbox só para depuração.
- **Produção completa** só depois dos Portões V **e** 1: sprites e quadros de todos os estados do GDD (parado, mover, ataque, dano, vitória/derrota etc.), cenários, mapa, UI e FX, em lotes pequenos, verificando cada lote e registrando reprovados.
- Ordem sugerida: personagem principal → rival → cenário/mapa → UI → FX → tela inicial animada.
