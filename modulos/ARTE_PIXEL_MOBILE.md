# MÓDULO — Arte e pixel art para mobile

Leia ao definir a bíblia visual ou produzir sprites. Referência: seção 8 do `PROMPT_MESTRE.md`.

## Consistência
- Resolução interna **fixa**, com escala **inteira**. Filtro *nearest*, sem anti-alias.
- Mesmo tamanho de pixel em todos os assets.
- Paleta limitada e documentada.
- Tamanho de quadro fixo por personagem; **pivô nos pés**; contato com o chão consistente.
- Atlas de até 2048 px (compatibilidade mobile).

## Geração com IA (ex.: PixelLab)
- Mantenha um **personagem de referência fixo** e reutilize-o em todo pedido.
- Registre os **lotes reprovados** e o motivo, para não repetir o erro.
- Verifique frames: identidade, anatomia, apoios, duplicatas, membros soltos.

## Mobile
- Área de toque de pelo menos 48 dp; respeitar *safe area*; orientação travada.
- Elementos de HUD legíveis em tela pequena.
- Teste no aparelho do dono (seção 10 do núcleo).
