# MÓDULO — Áudio (música, efeitos sonoros, voz)

Leia ao produzir ou integrar som. Referência: seção 8 do `PROMPT_MESTRE.md` e `MODO_JOGO_COMPLETO.md`.

## Duas fases (jeito do dono)
1. **Durante a produção: música.** A IA pode criar a música do jogo com a ferramenta que **realmente tiver** (diga qual). Loop sem clique na emenda; duração e BPM combinados com o clima.
2. **No final: efeitos sonoros e vozes.** O dono deixa para o fim e dá acesso ao ElevenLabs (ou outra ferramenta) para a IA finalizar. Até lá, o jogo usa som provisório ou silêncio, e **nada quebra por falta de som**. O dono pode pedir para trocar depois.

## Regras
1. **Lista de eventos sonoros** derivada do GDD (toda ação do jogador e do jogo tem som, ou decisão explícita de silêncio). O código toca o som **pelo nome do evento** (ex.: `hit_light`), com mapeamento em um arquivo único. Assim, na fase final, trocar o arquivo não muda o código.
2. Formatos compatíveis com o alvo (ex.: OGG/MP3), volume normalizado, controle de mute/volume.
3. **Mobile:** o áudio só toca após o primeiro toque do jogador; trate o desbloqueio.
4. **Proveniência e licença** de cada arquivo no inventário (ferramenta, prompt, data). Nada de música/SFX de terceiros sem direito.
5. Voz é opcional.
6. Direção (clima, referências, lista de eventos) vem do nível CRIATIVO; geração e integração, conforme ferramentas **realmente disponíveis** (Contrato de Evidência). Estimativa de custo antes de gerar em lote.
