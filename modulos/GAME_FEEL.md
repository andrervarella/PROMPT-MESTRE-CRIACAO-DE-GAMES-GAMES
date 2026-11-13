# MÓDULO — Game feel (checklist)

Use na prova do core loop (controle) e no vertical slice (polimento).

## Princípios
- **Teste de remoção:** o jogo deve ser envolvente mesmo sem arte, som e história. Se não for, o problema é o controle ou o loop, não falta de polimento.
- **Juice ecoa a mecânica.** Cada efeito reforça o que o jogador fez ou o que aconteceu; nada de efeito decorativo aleatório. Efeito que atrapalha a leitura sai.
- **Visual, som e vibração são desenhados juntos**, não em sequência.
- Polimento só depois que o core loop está sólido (Portão 1).

## Checklist
- Resposta ao toque/comando **imediata**; *input buffer* quando fizer sentido.
- Impacto: *hit-stop* (pausa curta), *screen shake*, *knockback* e *flash* na medida certa.
- *Squash/stretch*, partículas e flashes que reforçam leitura, sem poluir.
- Som em toda ação importante; feedback claro de sucesso, falha e dano.
- Tempo curto até a **primeira ação** do jogador.
- Nada "aparece do nada": entradas e saídas com transição curta.
- Dificuldade justa: o jogador entende por que perdeu.
- Teste no aparelho do dono: o controle "parece bom" no celular?

## Pontos de partida (ajustar no aparelho)
- Hit-stop: ~2–3 quadros em golpe comum; mais longo só em golpe pesado/final. Quanto maior a pausa, mais "pesado" parece.
- Todo inimigo/alvo atingido mostra feedback (flash claro); knockback proporcional ao dano.
- Shake proporcional à importância da ação e com decaimento rápido; evitar acumular vários efeitos fortes ao mesmo tempo.
- Vibração no Android: curta e opcional, com opção de desligar.
- Efeitos não podem derrubar o FPS no aparelho-alvo.

Valores são heurísticas de blogs e práticas de indie dev, não regra científica. Ver `FONTES.md`.
