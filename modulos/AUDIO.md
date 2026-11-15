# MÓDULO — Áudio (música, efeitos sonoros, voz)

Leia ao produzir ou integrar som. Referência: seção 8 do `PROMPT_MESTRE.md` e `MODO_JOGO_COMPLETO.md`.

## Duas fases (jeito do dono)
1. **Durante a produção: música** (ex.: Fenaky Music) **e efeitos sonoros gratuitos gerados por código** (abaixo). A IA usa a ferramenta que **realmente tiver** e diz qual. Loop de música sem clique na emenda; duração e BPM combinados com o clima.
2. **No final: efeitos sonoros mais realistas e vozes**, onde fizer diferença. O dono dá acesso ao ElevenLabs (ou outra ferramenta) para a IA finalizar. **Nada quebra por falta de som**, e o dono pode pedir para trocar depois.

## Efeitos sonoros gratuitos (padrão inicial)
- **ZzFX** (licença MIT): gera o som direto no código, sem arquivo de áudio; tem um editor web para criar e ajustar cada som. Primeira opção para jogos web/Phaser.
- **jsfxr / sfxr.me**: efeitos de 8 bits no navegador ou como biblioteca; bom para estilo retrô. Exporta WAV.
- **Bancos CC0** (ex.: Kenney): só quando o som gerado não servir (ex.: tecido, passos realistas). Conferir a licença de cada arquivo; "grátis para uso pessoal" não serve para jogo.
- Os parâmetros de cada som gerado ficam no mapeamento de eventos (versão no Git), para a outra IA conseguir ajustar.

## Regras
1. **Lista de eventos sonoros** derivada do GDD (toda ação do jogador e do jogo tem som, ou decisão explícita de silêncio). O código toca o som **pelo nome do evento** (ex.: `hit_light`), com mapeamento em um arquivo único. Assim, trocar o som (gerado → arquivo do ElevenLabs) não muda o resto do código.
2. Formatos compatíveis com o alvo (ex.: OGG/MP3), volume normalizado, controle de mute/volume.
3. **Mobile:** o áudio só toca após o primeiro toque do jogador; trate o desbloqueio.
4. **Proveniência e licença** de cada arquivo no inventário (ferramenta, prompt, data). Nada de música/SFX de terceiros sem direito.
5. Voz é opcional.
6. Direção (clima, referências, lista de eventos) vem do nível CRIATIVO; geração e integração, conforme ferramentas **realmente disponíveis** (Contrato de Evidência). Estimativa de custo antes de gerar em lote com serviço pago.
