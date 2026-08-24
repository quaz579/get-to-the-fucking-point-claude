# Como instalar

<details>
<summary><strong>Antigravity (<code>agy</code>)</strong></summary>

### Instalar

```bash
agy plugin install https://github.com/quaz579/get-to-the-fucking-point-claude
```

### Verificar

```bash
agy plugin list
```

### Atualizar

```bash
agy plugin uninstall get-to-the-fucking-point-claude
agy plugin install https://github.com/quaz579/get-to-the-fucking-point-claude
```

### Desinstalar

```bash
agy plugin uninstall get-to-the-fucking-point-claude
```

Ou mantenha instalado e desative: `agy plugin disable get-to-the-fucking-point-claude`.

### Sempre ativo (opcional)

Adicione ao `~/.gemini/GEMINI.md`:

```markdown
## Estilo de resposta

A pessoa que lê tem TDAH. Estruture cada resposta para que ela possa agir:

1. Comece pela resposta ou próxima ação: comando, caminho ou trecho de código primeiro.
2. Numere trabalhos com várias etapas; uma ação bem delimitada por etapa.
3. Termine com uma próxima ação que possa ser feita em menos de dois minutos.
4. Conclua o problema atual antes de levantar outro.
5. Reafirme o progresso a cada turno ("etapa 3 de 5 concluída").
6. Dê estimativas de tempo em unidades concretas, nunca "um pouco".
7. Após uma alteração, mostre o que agora funciona.
8. Erros: informe local, causa e correção, sem drama.
9. Limite listas a 5 itens.
10. Sem preâmbulo, recapitulação ou despedida.

Exceções: explique por completo quando pedirem. Confirme antes de ações destrutivas. Após três tentativas de correção sem sucesso, pare e identifique a suposição duvidosa. Se o pedido for ambíguo, faça uma pergunta curta.
```

</details>

<details>
<summary><strong>Claude Code</strong></summary>

### Instalar

```bash
claude plugin marketplace add quaz579/get-to-the-fucking-point-claude
claude plugin install get-to-the-fucking-point-claude@get-to-the-fucking-point-claude
```

Digite `/get-to-the-fucking-point-claude`.

### Verificar

```bash
claude plugin list
```

### Atualizar

```bash
claude plugin marketplace update get-to-the-fucking-point-claude
```

### Desinstalar

```bash
claude plugin uninstall get-to-the-fucking-point-claude
claude plugin marketplace remove get-to-the-fucking-point-claude
```

Ou mantenha instalado e desative: `claude plugin disable get-to-the-fucking-point-claude`.

### Sempre ativo (opcional)

Um hook `SessionStart` carrega todas as regras no início de cada sessão; não é preciso usar `/get-to-the-fucking-point-claude`:

```bash
touch ~/.claude/.get-to-the-fucking-point-claude-always
```

Para voltar ao modo sob demanda:

```bash
rm ~/.claude/.get-to-the-fucking-point-claude-always
```

O hook só é executado quando o arquivo de sinalização existe, portanto instalar o plugin não muda nada por si só. Ele respeita `$CLAUDE_CONFIG_DIR` caso você tenha movido o diretório de configuração. "stop adhd mode" ainda o desativa na sessão atual.

</details>


<details>
<summary><strong>Codex</strong></summary>

### Instalar

```bash
codex plugin marketplace add quaz579/get-to-the-fucking-point-claude --ref main
codex plugin add get-to-the-fucking-point-claude@get-to-the-fucking-point-claude
```

Ative a skill explicitamente digitando `$get-to-the-fucking-point-claude`. O Codex não a invoca automaticamente.

### Verificar

```bash
codex plugin list
```

### Atualizar

```bash
codex plugin marketplace upgrade get-to-the-fucking-point-claude
codex plugin remove get-to-the-fucking-point-claude
codex plugin add get-to-the-fucking-point-claude@get-to-the-fucking-point-claude
```

### Desinstalar

```bash
codex plugin remove get-to-the-fucking-point-claude
codex plugin marketplace remove get-to-the-fucking-point-claude
```

### Sempre ativo (opcional)

Adicione ao `~/.codex/AGENTS.md`:

```markdown
## Estilo de resposta

A pessoa que lê tem TDAH. Estruture cada resposta para que ela possa agir:

1. Comece pela resposta ou próxima ação: comando, caminho ou trecho de código primeiro.
2. Numere trabalhos com várias etapas; uma ação bem delimitada por etapa.
3. Termine com uma próxima ação que possa ser feita em menos de dois minutos.
4. Conclua o problema atual antes de levantar outro.
5. Reafirme o progresso a cada turno ("etapa 3 de 5 concluída").
6. Dê estimativas de tempo em unidades concretas, nunca "um pouco".
7. Após uma alteração, mostre o que agora funciona.
8. Erros: informe local, causa e correção, sem drama.
9. Limite listas a 5 itens.
10. Sem preâmbulo, recapitulação ou despedida.

Exceções: explique por completo quando pedirem. Confirme antes de ações destrutivas. Após três tentativas de correção sem sucesso, pare e identifique a suposição duvidosa. Se o pedido for ambíguo, faça uma pergunta curta.
```

</details>

<details>
<summary><strong>Gemini CLI</strong></summary>

O Gemini CLI não tem marketplace de plugins, então há duas opções nativas: um **comando personalizado** (opt-in, desativado até ser invocado) ou uma **extensão** (sempre ativa após a instalação). O comando corresponde ao comportamento padrão desta skill; escolha-o, a menos que queira as regras em todas as sessões.

### Instalar (command, opt-in)

```bash
mkdir -p ~/.gemini/commands
curl -fsSL https://raw.githubusercontent.com/quaz579/get-to-the-fucking-point-claude/main/skills/get-to-the-fucking-point-claude/agents/gemini.toml \
  -o ~/.gemini/commands/get-to-the-fucking-point-claude.toml
```

Inicie uma nova sessão e digite `/get-to-the-fucking-point-claude`. A skill permanecerá ativa durante essa sessão.

### Instalar (extension, always-on)

```bash
gemini extensions install https://github.com/quaz579/get-to-the-fucking-point-claude
```

A extensão carrega `GEMINI.md`, que importa a skill completa; assim, as regras valem desde a primeira mensagem. O `git` precisa estar instalado.

### Verificar

```bash
gemini extensions list          # via extensão
ls ~/.gemini/commands           # command route: get-to-the-fucking-point-claude.toml present
```

Ou digite `/` em uma sessão e confirme que `get-to-the-fucking-point-claude` aparece na lista.

### Atualizar

```bash
gemini extensions update get-to-the-fucking-point-claude    # via extensão
# via comando: execute novamente o curl acima
```

### Desinstalar

```bash
gemini extensions uninstall get-to-the-fucking-point-claude    # via extensão
rm ~/.gemini/commands/get-to-the-fucking-point-claude.toml     # command route
```

</details>

<details>
<summary><strong>GitHub Copilot (VS Code and Copilot CLI)</strong></summary>

O Copilot lê Agent Skills nativamente: usa o mesmo `SKILL.md`, sem conversão. No projeto, ele verifica `.github/skills/`, `.claude/skills/` e `.agents/skills/`; globalmente, `~/.copilot/skills/`, `~/.claude/skills/` e `~/.agents/skills/`.

### Instalar

```bash
npx skills add quaz579/get-to-the-fucking-point-claude -a github-copilot        # este projeto
npx skills add quaz579/get-to-the-fucking-point-claude -a github-copilot -g     # todos os projetos
```

Sem a CLI, copie a pasta da skill para qualquer diretório verificado pelo Copilot:

```bash
git clone https://github.com/quaz579/get-to-the-fucking-point-claude
mkdir -p ~/.copilot/skills
cp -R get-to-the-fucking-point-claude/skills/get-to-the-fucking-point-claude ~/.copilot/skills/
```

### Verificar

Digite `/` no campo de chat e confirme que `get-to-the-fucking-point-claude` aparece. Ou:

```bash
npx skills list
npx skills ls -g    # se instalado globalmente
```

### Atualizar

```bash
npx skills update get-to-the-fucking-point-claude
```

Ou copie a pasta novamente após `git pull`.

### Desinstalar

```bash
npx skills remove get-to-the-fucking-point-claude
```

Ou exclua a pasta `get-to-the-fucking-point-claude` do diretório de skills onde ela foi instalada.

### Observação sobre ativação

O Copilot respeita `disable-model-invocation`: nada é aplicado até você invocar a skill, como no Claude Code (testado no [#60](https://github.com/quaz579/get-to-the-fucking-point-claude/pull/60)).

### Sempre ativo (opcional)

Adicione o bloco abaixo ao `.github/copilot-instructions.md` do projeto (o Copilot o lê em todo chat):

```markdown
## Estilo de resposta

A pessoa que lê tem TDAH. Estruture cada resposta para que ela possa agir:

1. Comece pela resposta ou próxima ação: comando, caminho ou trecho de código primeiro.
2. Numere trabalhos com várias etapas; uma ação bem delimitada por etapa.
3. Termine com uma próxima ação que possa ser feita em menos de dois minutos.
4. Conclua o problema atual antes de levantar outro.
5. Reafirme o progresso a cada turno ("etapa 3 de 5 concluída").
6. Dê estimativas de tempo em unidades concretas, nunca "um pouco".
7. Após uma alteração, mostre o que agora funciona.
8. Erros: informe local, causa e correção, sem drama.
9. Limite listas a 5 itens.
10. Sem preâmbulo, recapitulação ou despedida.

Exceções: explique por completo quando pedirem. Confirme antes de ações destrutivas. Após três tentativas de correção sem sucesso, pare e identifique a suposição duvidosa. Se o pedido for ambíguo, faça uma pergunta curta.
```

</details>

<details>
<summary><strong>Hermes</strong></summary>

### Instalar

```bash
hermes skills install quaz579/get-to-the-fucking-point-claude/skills/get-to-the-fucking-point-claude
```

Digite `/get-to-the-fucking-point-claude`. The skill installs into `~/.hermes/skills/` and is exposed as a slash command at the next session start.

Prefere explorar primeiro? Adicione este repositório como fonte de skills (um "tap"), depois pesquise e instale:

```bash
hermes skills tap add quaz579/get-to-the-fucking-point-claude
hermes skills search adhd
hermes skills install quaz579/get-to-the-fucking-point-claude/skills/get-to-the-fucking-point-claude
```

### Verificar

```bash
hermes skills list
```

### Atualizar

```bash
hermes skills update get-to-the-fucking-point-claude
```

### Desinstalar

```bash
hermes skills uninstall get-to-the-fucking-point-claude
```

Ou remova também o tap: `hermes skills tap remove quaz579/get-to-the-fucking-point-claude`.

### Sempre ativo (opcional)

Adicione ao `AGENTS.md` do diretório de trabalho (o Hermes o carrega por diretório) ou ao `SOUL.md` da sua persona para todas as sessões:

```markdown
## Estilo de resposta

A pessoa que lê tem TDAH. Estruture cada resposta para que ela possa agir:

1. Comece pela resposta ou próxima ação: comando, caminho ou trecho de código primeiro.
2. Numere trabalhos com várias etapas; uma ação bem delimitada por etapa.
3. Termine com uma próxima ação que possa ser feita em menos de dois minutos.
4. Conclua o problema atual antes de levantar outro.
5. Reafirme o progresso a cada turno ("etapa 3 de 5 concluída").
6. Dê estimativas de tempo em unidades concretas, nunca "um pouco".
7. Após uma alteração, mostre o que agora funciona.
8. Erros: informe local, causa e correção, sem drama.
9. Limite listas a 5 itens.
10. Sem preâmbulo, recapitulação ou despedida.

Exceções: explique por completo quando pedirem. Confirme antes de ações destrutivas. Após três tentativas de correção sem sucesso, pare e identifique a suposição duvidosa. Se o pedido for ambíguo, faça uma pergunta curta.
```

</details>

<details>
<summary><strong>Kimi Code CLI</strong></summary>

### Instalar

Inicie uma sessão do Kimi Code e:

1. Execute `/plugins`.
2. Selecione **Custom**.
3. Cole `https://github.com/quaz579/get-to-the-fucking-point-claude` e pressione Enter.
4. Selecione **Trust and install**.

Use o comando slash `/skill:get-to-the-fucking-point-claude` para invocar a skill explicitamente.

### Atualizar

Em uma sessão do Kimi Code, execute `/plugins`, posicione o cursor em **I Have ADHD** e pressione `R`.

### Desinstalar

Em uma sessão do Kimi Code, execute `/plugins`, posicione o cursor em **I Have ADHD** e pressione `D`.

</details>


<details>
<summary><strong>Pi</strong></summary>

O Pi implementa o padrão Agent Skills, portanto o mesmo `SKILL.md` é carregado diretamente, sem conversão. A invocação no Pi é diferente: as skills são chamadas como `/skill:<name>`.

### Instalar

```bash
npx skills add quaz579/get-to-the-fucking-point-claude -a pi -y
```

Prefere usar o sistema de arquivos? O Pi encontra skills em `~/.pi/agent/skills/` e `~/.agents/skills/` (global), e em `.pi/skills/` e `.agents/skills/` (projeto):

```bash
git clone https://github.com/quaz579/get-to-the-fucking-point-claude
mkdir -p ~/.pi/agent/skills
cp -R get-to-the-fucking-point-claude/skills/get-to-the-fucking-point-claude ~/.pi/agent/skills/
```

Ative os comandos de barra de skills no `settings.json` do Pi:

```json
{ "enableSkillCommands": true }
```

Inicie uma nova sessão e digite `/skill:get-to-the-fucking-point-claude`.

### Verificar

```bash
npx skills list
```

Ou digite `/skill:` em uma sessão e confirme que `get-to-the-fucking-point-claude` aparece na lista.

### Atualizar

```bash
npx skills update get-to-the-fucking-point-claude
```

Ou copie a pasta novamente após `git pull`.

### Desinstalar

```bash
npx skills remove get-to-the-fucking-point-claude
```

Ou exclua `~/.pi/agent/skills/get-to-the-fucking-point-claude`.

### Sempre ativo (opcional)

Adicione ao `AGENTS.md` do projeto:

```markdown
## Estilo de resposta

A pessoa que lê tem TDAH. Estruture cada resposta para que ela possa agir:

1. Comece pela resposta ou próxima ação: comando, caminho ou trecho de código primeiro.
2. Numere trabalhos com várias etapas; uma ação bem delimitada por etapa.
3. Termine com uma próxima ação que possa ser feita em menos de dois minutos.
4. Conclua o problema atual antes de levantar outro.
5. Reafirme o progresso a cada turno ("etapa 3 de 5 concluída").
6. Dê estimativas de tempo em unidades concretas, nunca "um pouco".
7. Após uma alteração, mostre o que agora funciona.
8. Erros: informe local, causa e correção, sem drama.
9. Limite listas a 5 itens.
10. Sem preâmbulo, recapitulação ou despedida.

Exceções: explique por completo quando pedirem. Confirme antes de ações destrutivas. Após três tentativas de correção sem sucesso, pare e identifique a suposição duvidosa. Se o pedido for ambíguo, faça uma pergunta curta.
```

</details>


<details>
<summary><strong>Qwen Code</strong></summary>

### Instalar

```bash
qwen extensions install quaz579/get-to-the-fucking-point-claude
```

O Qwen Code aceita a forma abreviada do GitHub e instala o repositório como extensão nativa. A extensão encontra a skill em `skills/`.

Digite `/get-to-the-fucking-point-claude` para invocar a skill explicitamente. Instalar a extensão não altera a saída até que a skill seja invocada.

### Verificar

```bash
qwen extensions list
```

Depois, inicie uma nova sessão do Qwen Code e execute:

```text
/skills
```

Confirme que `get-to-the-fucking-point-claude` aparece na lista.

### Atualizar

```bash
qwen extensions update get-to-the-fucking-point-claude
```

### Desinstalar

```bash
qwen extensions uninstall get-to-the-fucking-point-claude
```

</details>

<details>
<summary><strong>Zed</strong></summary>

O Agent do Zed lê Agent Skills nativamente: usa o mesmo `SKILL.md`, sem conversão. (As antigas "Rules" do Zed foram substituídas por Skills e instruções em `AGENTS.md`.)

### Instalar

No Agent Panel, abra o gerenciador de Skills, escolha **Create skill from URL** (também disponível na paleta como `agent: create skill from url`) e cole:

```
https://github.com/quaz579/get-to-the-fucking-point-claude/blob/main/skills/get-to-the-fucking-point-claude/SKILL.md
```

Salve no escopo **User** para todos os projetos ou **Project** para apenas um. Depois, digite `/get-to-the-fucking-point-claude` no Agent Panel.

Prefere o sistema de arquivos? Clone o repositório e coloque a pasta da skill no diretório de skills do usuário:

```bash
git clone https://github.com/quaz579/get-to-the-fucking-point-claude
cp -R get-to-the-fucking-point-claude/skills/get-to-the-fucking-point-claude ~/.config/zed/skills/
```

### Verificar

Abra o gerenciador de Skills no Agent Panel e confirme que `get-to-the-fucking-point-claude` aparece. Ou digite `/` e confira.

### Atualizar

Importe novamente pela mesma URL (sobrescreve) ou copie a pasta de novo após `git pull`.

### Desinstalar

Remova `get-to-the-fucking-point-claude` do gerenciador de Skills ou exclua `~/.config/zed/skills/get-to-the-fucking-point-claude`.

### Sempre ativo (opcional)

Adicione ao seu `~/.config/zed/AGENTS.md` pessoal:

```markdown
## Estilo de resposta

A pessoa que lê tem TDAH. Estruture cada resposta para que ela possa agir:

1. Comece pela resposta ou próxima ação: comando, caminho ou trecho de código primeiro.
2. Numere trabalhos com várias etapas; uma ação bem delimitada por etapa.
3. Termine com uma próxima ação que possa ser feita em menos de dois minutos.
4. Conclua o problema atual antes de levantar outro.
5. Reafirme o progresso a cada turno ("etapa 3 de 5 concluída").
6. Dê estimativas de tempo em unidades concretas, nunca "um pouco".
7. Após uma alteração, mostre o que agora funciona.
8. Erros: informe local, causa e correção, sem drama.
9. Limite listas a 5 itens.
10. Sem preâmbulo, recapitulação ou despedida.

Exceções: explique por completo quando pedirem. Confirme antes de ações destrutivas. Após três tentativas de correção sem sucesso, pare e identifique a suposição duvidosa. Se o pedido for ambíguo, faça uma pergunta curta.
```

</details>

<details>
<summary><strong>Cursor, OpenCode, Amp e qualquer outro ambiente compatível com agent-skills</strong></summary>

Funciona com qualquer ambiente que leia Agent Skills. Troque `-a <agent>` pelo seu.

### Instalar

```bash
npx skills add quaz579/get-to-the-fucking-point-claude                  # this workspace
npx skills add quaz579/get-to-the-fucking-point-claude -g               # todos os projetos
npx skills add quaz579/get-to-the-fucking-point-claude -a cursor -y     # one agent only
npx skills add quaz579/get-to-the-fucking-point-claude -a opencode -y
```

Abra um novo chat do agente e digite `/get-to-the-fucking-point-claude`.

Sem a CLI, copie a pasta da skill para o caminho verificado pelo seu agente:

```bash
git clone https://github.com/quaz579/get-to-the-fucking-point-claude
mkdir -p ~/.cursor/skills     # Cursor. Use .agents/skills no OpenCode ou o caminho próprio do agente
cp -R get-to-the-fucking-point-claude/skills/get-to-the-fucking-point-claude ~/.cursor/skills/
```

### Verificar

```bash
npx skills list
npx skills ls -g    # se instalado globalmente
```

### Atualizar

```bash
npx skills update get-to-the-fucking-point-claude
npx skills update -g    # se instalado globalmente
```

### Desinstalar

```bash
npx skills remove get-to-the-fucking-point-claude
npx skills remove get-to-the-fucking-point-claude -g    # se instalado globalmente
```

### Sempre ativo (opcional)

Cole isto no arquivo de regras persistentes do agente. Cursor: **Settings → Rules → User Rules**, ou uma regra de projeto em `.cursor/rules/` com `alwaysApply: true`. OpenCode: `~/.config/opencode/AGENTS.md`.

```markdown
## Estilo de resposta

A pessoa que lê tem TDAH. Estruture cada resposta para que ela possa agir:

1. Comece pela resposta ou próxima ação: comando, caminho ou trecho de código primeiro.
2. Numere trabalhos com várias etapas; uma ação bem delimitada por etapa.
3. Termine com uma próxima ação que possa ser feita em menos de dois minutos.
4. Conclua o problema atual antes de levantar outro.
5. Reafirme o progresso a cada turno ("etapa 3 de 5 concluída").
6. Dê estimativas de tempo em unidades concretas, nunca "um pouco".
7. Após uma alteração, mostre o que agora funciona.
8. Erros: informe local, causa e correção, sem drama.
9. Limite listas a 5 itens.
10. Sem preâmbulo, recapitulação ou despedida.

Exceções: explique por completo quando pedirem. Confirme antes de ações destrutivas. Após três tentativas de correção sem sucesso, pare e identifique a suposição duvidosa. Se o pedido for ambíguo, faça uma pergunta curta.
```
</details>


## Como a ativação funciona

1. **Instalada, mas não invocada.** No Claude Code, Qwen Code e Codex, nada acontece até que você invoque a skill explicitamente. Claude Code e Qwen Code respeitam `disable-model-invocation: true` em `SKILL.md`; o Codex respeita `policy.allow_implicit_invocation: false` em `agents/openai.yaml`. Outros ambientes podem carregar a descrição de cada skill na inicialização e ativá-la por conta própria.
2. **Você a invoca explicitamente.** Digite `/get-to-the-fucking-point-claude` no Claude Code ou Qwen Code, ou `$get-to-the-fucking-point-claude` no Codex. As regras ficam ativas nessa sessão. "stop adhd mode" ou "normal mode" as desativa.
3. **Você cria `~/.claude/.get-to-the-fucking-point-claude-always`** (Claude Code). Um hook `SessionStart` carrega todas as regras desde a primeira mensagem, em toda sessão.
4. **Você adiciona o trecho sempre ativo acima** (outros ambientes). Isso mantém as regras principais no contexto persistente do agente.

No Claude Code, Qwen Code e Codex não há meio-termo: se você não ativou, está desativado.

## Solução de problemas

**`/get-to-the-fucking-point-claude` não aparece no preenchimento automático.** Reinicie o agente. O índice de plugins é lido na inicialização.

**A flag de sempre ativo não funciona.** Atualize o plugin (`claude plugin marketplace update get-to-the-fucking-point-claude`) e reinicie. Hooks são lidos na inicialização, e a flag exige a versão que inclui `hooks/hooks.json`.

**`claude plugin marketplace add` falha.** Use o formato `owner/repo`. Um caminho local deve apontar para a raiz do repositório, não para `.claude-plugin/`.

**Instalada, mas as respostas ainda têm preâmbulo.** Abra uma nova sessão. Se continuar desviando, torne mais rigoroso o texto em `skills/get-to-the-fucking-point-claude/SKILL.md`.

**Quer regras diferentes.** Faça um fork, edite `skills/get-to-the-fucking-point-claude/SKILL.md` e troque pela sua cópia:

```bash
claude plugin uninstall get-to-the-fucking-point-claude            # remova primeiro a cópia upstream:
claude plugin marketplace remove get-to-the-fucking-point-claude   # o fork e o upstream usam o mesmo nome
claude plugin marketplace add <your-username>/get-to-the-fucking-point-claude
claude plugin install get-to-the-fucking-point-claude@get-to-the-fucking-point-claude
```

Reinicie e invoque `/get-to-the-fucking-point-claude` novamente.

**A skill não aparece após `npx skills add`.** Abra um novo chat do agente. Skills são indexadas no início da sessão. Confirme que a pasta foi instalada onde o agente procura (`~/.cursor/skills/` no Cursor, `.agents/skills/` no OpenCode) e que o `name` no frontmatter corresponde ao nome da pasta.
