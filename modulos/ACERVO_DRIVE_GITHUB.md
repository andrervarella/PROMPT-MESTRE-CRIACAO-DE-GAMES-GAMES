# MÓDULO — Acervo de assets no Google Drive e código no GitHub

**Aplica-se a TODOS os jogos criados com esta metodologia**, independentemente de engine, IA ou plataforma. Decisão do proprietário em 15/11/2026. Ver também \`modulos/COMUNICACAO_CLAUDE_CODEX.md\` e \`modulos/ARTE_PIXEL_MOBILE.md\`.

## 1. Arquitetura padrão

**Google Drive = acervo mestre de arte e arquivos grandes**, segregado por jogo. **GitHub = fonte de verdade para código, projeto executável, documentação, decisões, tarefas, histórico e manifestos**.

- Drive: referências aprovadas em resolução original, concept sheets, personagens, assets intermediários, originais editáveis, vídeos, áudios, spritesheets de trabalho, ZIPs grandes e entregas.
- GitHub: projeto Godot/Phaser/Unity e código-fonte, cenas e dependências, arquivos de configuração, documentação, tarefas, manifestos, scripts de importação, **assets finais otimizados necessários para executar/compilar o jogo**.
- Não deixar o jogo dependente de um link privado do Drive para rodar: o build e o clone devem poder reproduzir o projeto com os assets publicados no repo ou mecanismo reprodutível documentado (ex.: Git LFS ou download autenticado autorizado no processo de build).
- O GitHub não é o armazenamento de origem de um catálogo crescente de PNGs brutos/ZIPs/vídeos. Verificar limites efetivos e considerar LFS quando necessário; nunca usar Git LFS sem documentar requisitos e custos.

## 2. Estrutura obrigatória de pastas no Drive

Criar **uma pasta principal por projeto**, com o nome do jogo, debaixo de \`GAMES_IA/\`. Preferir nomes estáveis e claros. Exemplo genérico:

\`\`\`
Meu Drive/
  GAMES_IA/
    NOME DO JOGO/
      00_REFERENCIAS_APROVADAS/
      01_ASSETS_EM_PRODUCAO/
      02_SPRITES_ANIMACOES/
      03_CENARIOS_UI/
      04_AUDIO_VIDEO/
      05_EXPORTACOES_PACOTES/
\`\`\`

- Cada jogo tem suas próprias pastas. **Não misturar** assets de jogos distintos.
- \`00_REFERENCIAS_APROVADAS\`: originais intocados, com identificador/versão e data da aprovação. Edição vai para outra pasta.
- \`01_ASSETS_EM_PRODUCAO\`: turnarounds, desmembramentos, rigs, testes, recortes ainda não aprovados.
- \`02_SPRITES_ANIMACOES\`: PNG transparente, quadros, atlas, spritesheets e prévias de movimento.
- \`03_CENARIOS_UI\`: mapas, tilesets, cenários, objetos, HUD, menus.
- \`04_AUDIO_VIDEO\`: efeitos, músicas, locução, cinemáticas e arquivos-fonte.
- \`05_EXPORTACOES_PACOTES\`: ZIPs, compilações auxiliares, versões entregáveis e pacotes de transferência.
- Subpastas adicionais podem ser criadas por fase, personagem e data, sem substituir a hierarquia.

## 3. Manifesto obrigatório no GitHub (ponte entre ferramentas)

Em **cada repositório de jogo**, manter \`docs/ACERVO_DRIVE.md\` e \`docs/MANIFESTO_ASSETS.md\`:

- \`ACERVO_DRIVE.md\`: nome e caminho lógico do acervo no Drive, responsável, organização, **permissão verificada** e link somente se expressamente autorizado a constar no GitHub.
- \`MANIFESTO_ASSETS.md\`: ID estável, título, jogo, personagem/local, tipo, versão, origem, status (aprovado/revisão/provisório/final), caminho no Drive, caminho no GitHub se houver, hash SHA-256 (se calculável), tamanho/dimensões e data. Incluir procedência de IA (ferramenta, prompt/seed quando disponíveis).
- Antes de gerar sprite, consultar **a referência canônica aprovada** identificada pelo manifesto. Um conceito/crop não é automaticamente sprite.
- Manter nomenclatura estável para importação na engine; não sobrescrever original nem alterar a identidade visual aprovada.
- Evitar publicar URLs assinadas, tokens, dados privados ou pastas pessoais de terceiros. Nome lógico do caminho não concede acesso.

## 4. Protocolo de entrega e sincronização entre ChatGPT, Claude e Codex

1. Confirmar o **jogo certo**, a branch/commit/PR no GitHub e a pasta correta no Drive.
2. Verificar efetivamente se o agente tem permissão para acessar **ambas as fontes**. Não presumir que uma conexão do ChatGPT esteja automaticamente disponível no Claude ou Codex.
3. Criar ou atualizar arte no Drive; guardar original e versão, preferencialmente sem sobrescrever.
4. Conferir upload por listagem ou metadados do Drive. Em falha ou limite técnico, declarar pendência e oferecer arquivo pequeno/particionado ou outra rota autorizada. Não afirmar upload que não aconteceu.
5. Registrar o item no manifesto do **repositório do jogo** com localização, versão, estado, checksum se disponível.
6. Integrar ao GitHub **os assets finais necessários para executar o projeto**, com tamanho apropriado, e registrar commit/PR. Não depender de arquivos apenas no computador de uma IA.
7. No handoff, informar: links verificáveis do Drive quando permitidos, arquivos e hashes, branch/commit ou PR, testes efetuados, itens ainda ausentes, próxima tarefa.
8. **Sincronizado** só quando a outra IA consegue acessar os materiais requeridos e os links/commits foram confirmados. “Salvo no Drive”, “no GitHub” e “recebido pelo outro agente” são **três estados diferentes**.

### Aprovações e privacidade

- **Não compartilhar a pasta como "qualquer pessoa com o link" automaticamente.** Solicitar aprovação antes de ampliar permissões.
- Repositórios públicos não devem conter fotos reais privadas do proprietário, imagens de familiares ou animais de estimação, material confidencial, credenciais, chaves ou links temporários.
- Gastos com Google Drive, Git LFS, geradores de sprites (PixelLab etc.) e serviços de nuvem devem ser informados e autorizados previamente.
- Acesso, upload, transformação e publicação não são equivalentes: registrar cada uma separadamente.
- Os agentes só podem usar ferramentas de nuvem a que estejam **realmente conectados**.

## 5. Exemplo atual — ARASHI VANGUARD

- Drive: \`GAMES_IA/ARASHI VANGUARD/\` — pastas \`00\` a \`05\` criadas e listadas em 15/11/2026.
- GitHub do jogo: \`andrervarella/ARASHI-VANGUARD-GAME\`.
- Este exemplo não significa que os ZIPs antigos do ChatGPT tenham sido automaticamente transferidos ao Drive nem que Claude/Codex tenham permissão de acesso. Confirmar antes de usar.
