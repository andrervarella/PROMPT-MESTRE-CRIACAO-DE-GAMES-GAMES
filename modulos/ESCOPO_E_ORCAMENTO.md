# MÓDULO — Escopo, protótipo, descarte e orçamento

Objetivo: não gastar crédito e tempo no jogo errado, e não deixar o escopo crescer. Referência: seções 4 e 6 do `PROMPT_MESTRE.md`.

> Boa parte vem de práticas comuns de desenvolvedores indie (prototipar uma pergunta por vez, manter lista de prioridades, congelar recursos). Os **números de orçamento abaixo são proposta inicial sem fonte**: o dono ajusta e registra em `docs/DECISOES.md`.

## 1. Frase do jogo
Uma frase: **o que o jogador faz, o que tem de interessante, como deve parecer.** Recurso que não serve à frase é cortado.

## 2. Pergunta do protótipo
Cada protótipo responde **UMA pergunta** (ex.: "bater é gostoso?", "o puzzle é compreensível em 30 s?"). Registre a pergunta e a resposta em `docs/DECISOES.md`. Polir um loop sem graça esconde o problema em vez de resolver.

## 3. Lista de cortes (4 colunas)
**PRECISA** · **DEVERIA** · **PODERIA** · **NÃO NESTA VERSÃO**. Ideia nova no meio do caminho vai para `docs/PROXIMO_JOGO.md` e só é revista no fim de um marco. Depois do Portão 1, recursos novos só entram trocando por outro de igual tamanho.

## 4. Critério de descarte
- Portão 1 reprovado **3 vezes**, ou **2 jogadores de fora** que não recomeçam sozinhos: **mude o verbo central ou arquive a ideia.**
- Arquivar cedo é resultado válido: registre o aprendizado em `APRENDIZADOS.md`.

## 5. Orçamento por fase (ponto de partida)
| Fase | Teto sugerido |
|---|---|
| Conceito | 1 sessão no modelo forte |
| Portão V | até 6 imagens, 3 rodadas por imagem |
| Lote-piloto + Portão 1 | ~12 quadros + até 3 ciclos de ajuste |
| Produção | lotes de 1 personagem por vez |

**Estourou o teto:** pare e reporte ao dono antes de continuar. Também vale para o uso do plano de cada IA (veja `MODELOS_E_PARALELISMO.md`).

## 6. Marcos no Git
Tag a cada portão aprovado (`portao-v`, `portao-1`, `portao-2`, `v1.0`). Voltar atrás = voltar à tag.
