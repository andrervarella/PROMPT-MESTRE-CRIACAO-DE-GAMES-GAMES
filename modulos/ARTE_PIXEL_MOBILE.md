# MÓDULO — Arte e pixel art para mobile

Leia ao definir a bíblia visual ou produzir sprites. Referência: seção 8 do `PROMPT_MESTRE.md`.

## Originalidade primeiro (preferência do dono)
- O visual do jogo deve ser **o mais original possível**. Personagens, cenários principais, tela inicial, mapa e cutscenes são **sempre criados para o jogo** (gerados por IA a partir da direção aprovada).
- **Assets públicos** (Kenney, OpenGameArt, itch.io etc.) só no **mínimo** e onde não dão "cara" ao jogo: partículas, ícones de sistema, cursor, fontes. Mesmo assim, ajustados à paleta do jogo. Cada uso público é registrado no manifesto com a licença (preferir CC0) e avisado ao dono.
- Se um asset público parecer necessário para algo visível e importante, a IA **pergunta antes** e oferece a alternativa original.

## Cenário longo ou pesado: procedural com peças originais
Quando o cenário for muito longo, variado ou caro de gerar imagem por imagem:
1. Gerar e aprovar um **conjunto pequeno de peças originais** do jogo: tiles, módulos de chão/parede, decorações, camadas de fundo para parallax.
2. O código **monta** o cenário combinando essas peças (regras, sementes, variações, espelhamento, troca de paleta prevista na bíblia visual). Isso é **procedural com arte original**, não desenho por código: a regra de não desenhar personagens/cenários por código continua valendo.
3. Manter **trechos-chave feitos à mão** (início de fase, chefão, momentos marcantes) para o jogo não parecer repetitivo.
4. Usar **semente fixa** quando a fase precisar ser sempre igual (testes e aprovação), e semente variável só onde a variedade for parte do jogo.
5. A IA propõe o procedural ao dono quando perceber que a produção está ficando pesada (custo, tempo ou inconsistência), com motivo e 2 opções.

## Consistência
- Resolução interna **fixa**, com escala **inteira**. Filtro *nearest*, sem anti-alias.
- Mesmo tamanho de pixel em todos os assets.
- Paleta limitada e documentada.
- Tamanho de quadro fixo por personagem; **pivô nos pés**; contato com o chão consistente.
- Atlas de até 2048 px (compatibilidade mobile).
- Nomes e caminhos estáveis: o placeholder e o asset final têm o mesmo nome (troca sem mexer no código).
- Tiles do procedural com **bordas que encaixam** (testar emendas lado a lado antes de aprovar o conjunto).

## Geração com IA (ex.: PixelLab, gerador de imagens da OpenAI, Fenaky)
- Mantenha um **personagem de referência fixo** e reutilize-o em todo pedido.
- Registre os **lotes reprovados** e o motivo, para não repetir o erro.
- Registre **proveniência** de cada asset (ferramenta, prompt, seed, data).
- Verifique frames: identidade, anatomia, apoios, duplicatas, membros soltos.

## Mobile
- Área de toque de pelo menos 48 dp; respeitar *safe area*; orientação travada.
- Elementos de HUD legíveis em tela pequena.
- Teste no aparelho do dono (seção 10 do núcleo).
