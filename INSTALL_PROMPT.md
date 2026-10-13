# Prompt para instalar o conjunto de skills

Copie o texto abaixo em um Codex conectado à internet:

```text
Instale globalmente as seguintes skills no diretório de skills do usuário do Codex, sem modificar arquivos do projeto atual.

Use a skill `skill-installer` se ela estiver disponível. Caso contrário, faça o download seguro dos diretórios do GitHub e coloque cada skill em `~/.codex/skills/<nome>`. Não sobrescreva uma skill existente: informe o status e preserve-a.

Instale estas fontes:

1. `impeccable`
   - Repositório: `pbakaus/impeccable`
   - Caminho: `.agents/skills/impeccable`

2. `frontend-design`
   - Repositório: `anthropics/skills`
   - Caminho: `skills/frontend-design`

3. `grill-me`
   - Repositório: `mattpocock/skills`
   - Caminho: `skills/productivity/grill-me`

4. `web-design-guidelines`
   - Repositório: `vercel-labs/agent-skills`
   - Caminho: `skills/web-design-guidelines`

5. `mega-token-saver`
   - Repositório: `danilolana/mega-token-saver-codex`
   - Caminho: `skills/mega-token-saver`

Ao terminar, informe para cada skill se foi instalada, se já existia ou se falhou. Não instale dependências nem altere configurações do projeto. Avise que novas skills ficam disponíveis na próxima mensagem.
```
