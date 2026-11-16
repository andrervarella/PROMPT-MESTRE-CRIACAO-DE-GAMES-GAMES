# MÓDULO — Acervo Google Drive × GitHub (V4.5)

**Regra universal para TODOS os jogos.** Aprovada pelo proprietário em 15/11/2026; refinamento baseado na DEC-015 de `andrervarella/ARASHI-VANGUARD-GAME` (`dev`, `docs/DECISOES.md` e `docs/ACERVO_DRIVE.md`). Complementa `modulos/COMUNICACAO_CLAUDE_CODEX.md`.

## 1. Divisão obrigatória, sem duplicação integral

**GitHub — apenas assets finais de runtime e arquivos de desenvolvimento necessários:**
- Código, projeto da engine (Godot/Phaser/Unity etc.), cenas, dependências, configuração, documentação, decisões, tarefas, manifestos e testes.
- Sprites, cenários, UI, efeitos sonoros e músicas **finais e otimizados**, realmente utilizados pelo jogo.
- O clone/build do projeto deve funcionar sem buscar manualmente arquivos no Drive. O Drive não pode ser dependência de runtime nem substituto para arquivos obrigatórios do jogo.
- **Não usar GitHub como biblioteca de originais e rascunhos.** Não inserir novas artes de conceito não lançadas no repositório público só para compartilhar entre agentes. Os arquivos de referência já publicados permanecem até decisão expressa do dono; **nunca apagá-los automaticamente**.

**Google Drive — acervo mestre de originais e produção:**
- Referências aprovadas, originais em resolução máxima, arquivos editáveis e fontes.
- Rascunhos, testes, versões rejeitadas/descartadas, recortes, turnarounds, sprites em produção, cenários e UI em alta resolução.
- Vídeos, gravações/músicas-fonte e ZIPs/pacotes úteis ainda não arquivados.
- **Não duplicar tudo** nas duas plataformas. A exceção lógica é: **arquivo final otimizado que o jogo utiliza no GitHub; fonte/original correspondente no Drive**. Nem sempre são bytes iguais.

## 2. Estrutura padrão por jogo no Drive

```text
Meu Drive/
  GAMES_IA/
    NOME DO JOGO/
      00_REFERENCIAS_APROVADAS/
      01_ASSETS_EM_PRODUCAO/
      02_SPRITES_ANIMACOES/
      03_CENARIOS_UI/
      04_AUDIO_VIDEO/
      05_EXPORTACOES_PACOTES/
```

- Criar **uma pasta separada para cada jogo**, sem misturar personagens ou assets de projetos diferentes.
- `00`: originais intactos e identidade visual aprovada; `01`: conceitos, testes, descartes, trabalhos intermediários; `02`: sprites, atlas e animações **de produção/fonte**; `03`: cenários/UI e fontes em alta resolução; `04`: originais de áudio, vídeo e música; `05`: pacotes exportados, ZIPs e entregáveis.
- As versões finais **otimizadas utilizadas no jogo** vão para o GitHub do jogo, mesmo quando o material-fonte está no Drive.
- Pastas adicionais de organização são permitidas; conservar caminhos lógicos estáveis.

## 3. Manifesto obrigatório (ponte Drive × GitHub)

Em **cada repositório de jogo**, manter `docs/MANIFESTO_ASSETS.md` e `docs/ACERVO_DRIVE.md`.

Para cada asset, registrar pelo menos:
1. **ID estável**, nome/tipo, **versão** e **status** (referência aprovada, em produção, descartado, final etc.).
2. **Caminho lógico no Drive** da fonte ou original, se existir; **caminho no GitHub** do final de runtime, se existir.
3. **SHA-256 de cada arquivo efetivamente existente** (original/fonte do Drive, cópia recomprimida do Drive, runtime do GitHub), com `pendente` quando não calculável. Nunca inventar hash.
4. Metadados pertinentes: dimensões, pivô, frames, FPS, proveniência/gerador, prompt/seed quando disponíveis, licença, data e responsável pela aprovação.
5. Se uma cópia de imagem sem perda foi necessária, registrar **formato e dois hashes diferentes** (bytes da origem e bytes da cópia), além do resultado da checagem de pixels.

O manifesto não substitui verificação da existência dos arquivos nem da permissão de acesso. Um concept/crop é referência, não um sprite jogável.

## 4. Limites de upload: preservar pixels, não enviar partes soltas

- **Limites dependem de cada conector/conta**, não são um limite universal do Google Drive. No conector do Claude observado em ARASHI VANGUARD, o teto prático foi cerca de **3,1 MB por arquivo enviado**.
- Se o conector recusar o arquivo grande, **não fragmentar uma imagem em partes soltas no Drive**: os pedaços não são uma imagem utilizável.
- Primeiro, testar **PNG recomprimido sem perda**. Se não couber, usar **WebP lossless (sem perda)** quando a ferramenta e o pipeline aceitarem.
- **Antes de declarar equivalência**, usar script para comparar os pixels decodificados de ambas as imagens, incluindo largura, altura e valores RGBA de **todos** os pixels (e outros metadados relevantes para o uso, quando houver). A equivalência deve ser **exata**, não apenas visual. Não usar JPEG ou WebP com perda para substituir originais aprovados.
- Calcular e registrar separadamente **SHA-256 do original** e **SHA-256 da cópia sem perda**, pois os bytes/formato podem mudar mesmo com pixels idênticos. Manter a origem disponível e registrar qual representação está no Drive.
- Verificar upload por listagem/leitura ou metadados. Se nenhuma opção couber, marcar **PENDENTE** e propor envio manual íntegro ou outra rota autorizada; **não afirmar sincronização**.
- **ZIP com conteúdo já existente e inventariado no acervo não precisa ser reenviado**. Confirmar cobertura por IDs/hashes, sem supor redundância.

## 5. Repositório público, privacidade e autorizações

- **AVISO OBRIGATÓRIO:** um repositório público expõe sprites, cenários, músicas e outras artes **ainda não lançadas** que forem enviados ao GitHub. Informar o dono **antes** de publicar novas artes não lançadas.
- **Só o proprietário decide** tornar o repositório privado. Não alterar visibilidade sem aprovação.
- **Não apagar assets que já estejam no GitHub sem aprovação do proprietário**, mesmo que se considere que deveriam estar no Drive.
- **NUNCA publicar no GitHub links do Google Drive**, IDs privados como links, URLs assinadas, tokens, senhas ou credenciais. Guardar **somente caminhos lógicos** `GAMES_IA/NOME DO JOGO/... ` nos documentos públicos; fornecer links apenas em comunicação autorizada fora do repositório.
- Não abrir permissões do Drive ("qualquer pessoa com o link") por iniciativa própria.
- Serviços pagos, novas integrações ou custos adicionais exigem aprovação prévia.

## 6. Comunicação e confirmação de sincronização

**Três estados independentes:**
1. `SALVO NO DRIVE`: arquivo criado/enviado e verificado no Drive.
2. `NO GITHUB`: arquivo/código/manifesto publicado e commit/branch/PR verificáveis.
3. `OUTRO AGENTE CONSEGUIU ACESSAR`: Claude, Codex ou ChatGPT confirmou acesso real ao arquivo solicitado, não apenas ao link.

**Só declarar `SINCRONIZADO` quando os três estados relevantes para o handoff estiverem confirmados**, com caminho/versão/hash e evidência. Um conector do ChatGPT não significa conexão do Claude/Codex.

Ordem de trabalho: identificar repositório e branch → verificar PRs/commits → localizar pasta do jogo → conferir permissões → produzir/preservar fontes no Drive → testar upload e integridade → atualizar manifesto no GitHub → integrar apenas runtime final necessário → testar build/jogo → verificar acesso do agente de destino → relatar pendências.

No handoff, listar arquivos verificados em cada lugar, os hashes realmente calculados, teste de pixels (quando houver), branch/commit/PR, permissões comprovadas e o que **não** foi testado.

## 7. Referência operacional de origem

- A **DEC-015** de `ARASHI-VANGUARD-GAME`, branch `dev`, foi a origem deste refinamento universal. Seu `docs/ACERVO_DRIVE.md` registra cópias sem perda com verificação de pixels e um limite observado no conector do Claude.
- **Não transportar arquivos entre repositórios nem apagar materiais existentes** por conta desta atualização de regras.
