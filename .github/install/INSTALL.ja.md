# インストール方法

<details>
<summary><strong>Antigravity (<code>agy</code>)</strong></summary>

### インストール

```bash
agy plugin install https://github.com/quaz579/get-to-the-fucking-point-claude
```

### 確認

```bash
agy plugin list
```

### 更新

```bash
agy plugin uninstall get-to-the-fucking-point-claude
agy plugin install https://github.com/quaz579/get-to-the-fucking-point-claude
```

### アンインストール

```bash
agy plugin uninstall get-to-the-fucking-point-claude
```

インストールしたまま無効にする場合は、`agy plugin disable get-to-the-fucking-point-claude` を実行します。

### 常時有効（任意）

`~/.gemini/GEMINI.md` に追加します：

```markdown
## 出力スタイル

読み手には ADHD があります。すぐ行動に移せるよう、すべての回答を次のように構成してください：

1. 回答または次の行動から始める。コマンド、パス、スニペットを先に示す。
2. 複数手順の作業には番号を付け、1 ステップにつき 1 つの明確な行動にする。
3. 2 分以内にできる次の行動を 1 つ示して終える。
4. 新しい問題を挙げる前に、現在の問題を終わらせる。
5. 各ターンで進捗を言い直す（「5 ステップ中 3 ステップ完了」）。
6. 所要時間は具体的な単位で示し、「少し」とは言わない。
7. 変更後は、何が動くようになったかを示す。
8. エラーは場所、原因、修正方法を淡々と示す。
9. リストは最大 5 項目にする。
10. 前置き、要約、締めの言葉を入れない。

例外：説明を求められた場合は十分に説明する。破壊的な操作の前には確認する。修正に 3 回失敗したら止まり、疑わしい前提を明示する。依頼が曖昧なら短い質問を 1 つする。
```

</details>

<details>
<summary><strong>Claude Code</strong></summary>

### インストール

```bash
claude plugin marketplace add quaz579/get-to-the-fucking-point-claude
claude plugin install get-to-the-fucking-point-claude@get-to-the-fucking-point-claude
```

`/get-to-the-fucking-point-claude` と入力します。

### 確認

```bash
claude plugin list
```

### 更新

```bash
claude plugin marketplace update get-to-the-fucking-point-claude
```

### アンインストール

```bash
claude plugin uninstall get-to-the-fucking-point-claude
claude plugin marketplace remove get-to-the-fucking-point-claude
```

インストールしたまま無効にする場合は、`claude plugin disable get-to-the-fucking-point-claude` を実行します。

### 常時有効（任意）

`SessionStart` フックが各セッションの開始時に完全なルールセットを読み込むため、`/get-to-the-fucking-point-claude` は不要です：

```bash
touch ~/.claude/.get-to-the-fucking-point-claude-always
```

オンデマンドに戻す場合：

```bash
rm ~/.claude/.get-to-the-fucking-point-claude-always
```

フックはフラグファイルが存在する場合のみ動作するため、プラグインをインストールしただけでは何も変わりません。設定ディレクトリを移動している場合は `$CLAUDE_CONFIG_DIR` が使われます。「stop adhd mode」と入力すれば、現在のセッションでは無効にできます。

</details>


<details>
<summary><strong>Codex</strong></summary>

### インストール

```bash
codex plugin marketplace add quaz579/get-to-the-fucking-point-claude --ref main
codex plugin add get-to-the-fucking-point-claude@get-to-the-fucking-point-claude
```

`$get-to-the-fucking-point-claude` を明示的に入力して有効化します。Codex がこのスキルを自動で呼び出すことはありません。

### 確認

```bash
codex plugin list
```

### 更新

```bash
codex plugin marketplace upgrade get-to-the-fucking-point-claude
codex plugin remove get-to-the-fucking-point-claude
codex plugin add get-to-the-fucking-point-claude@get-to-the-fucking-point-claude
```

### アンインストール

```bash
codex plugin remove get-to-the-fucking-point-claude
codex plugin marketplace remove get-to-the-fucking-point-claude
```

### 常時有効（任意）

`~/.codex/AGENTS.md` に追加します：

```markdown
## 出力スタイル

読み手には ADHD があります。すぐ行動に移せるよう、すべての回答を次のように構成してください：

1. 回答または次の行動から始める。コマンド、パス、スニペットを先に示す。
2. 複数手順の作業には番号を付け、1 ステップにつき 1 つの明確な行動にする。
3. 2 分以内にできる次の行動を 1 つ示して終える。
4. 新しい問題を挙げる前に、現在の問題を終わらせる。
5. 各ターンで進捗を言い直す（「5 ステップ中 3 ステップ完了」）。
6. 所要時間は具体的な単位で示し、「少し」とは言わない。
7. 変更後は、何が動くようになったかを示す。
8. エラーは場所、原因、修正方法を淡々と示す。
9. リストは最大 5 項目にする。
10. 前置き、要約、締めの言葉を入れない。

例外：説明を求められた場合は十分に説明する。破壊的な操作の前には確認する。修正に 3 回失敗したら止まり、疑わしい前提を明示する。依頼が曖昧なら短い質問を 1 つする。
```

</details>

<details>
<summary><strong>Gemini CLI</strong></summary>

Gemini CLI にはプラグインマーケットプレイスがないため、ネイティブな方法は 2 つあります。呼び出すまで無効な**カスタムコマンド**（オプトイン）と、インストール後は常時有効な**拡張機能**です。コマンド方式がこのスキルの既定の動作に合うため、すべてのセッションでルールを使いたい場合を除き、こちらを選んでください。

### インストール (command, opt-in)

```bash
mkdir -p ~/.gemini/commands
curl -fsSL https://raw.githubusercontent.com/quaz579/get-to-the-fucking-point-claude/main/skills/get-to-the-fucking-point-claude/agents/gemini.toml \
  -o ~/.gemini/commands/get-to-the-fucking-point-claude.toml
```

新しいセッションを開始して `/get-to-the-fucking-point-claude` と入力します。そのセッション中は有効のままです。

### インストール (extension, always-on)

```bash
gemini extensions install https://github.com/quaz579/get-to-the-fucking-point-claude
```

拡張機能は完全なスキルをインポートする `GEMINI.md` を読み込むため、最初のメッセージからルールが適用されます。`git` のインストールが必要です。

### 確認

```bash
gemini extensions list          # 拡張機能方式
ls ~/.gemini/commands           # command route: get-to-the-fucking-point-claude.toml present
```

または、セッションで `/` と入力し、`get-to-the-fucking-point-claude` が一覧にあることを確認します。

### 更新

```bash
gemini extensions update get-to-the-fucking-point-claude    # 拡張機能方式
# コマンド方式：上記の curl を再実行
```

### アンインストール

```bash
gemini extensions uninstall get-to-the-fucking-point-claude    # 拡張機能方式
rm ~/.gemini/commands/get-to-the-fucking-point-claude.toml     # command route
```

</details>

<details>
<summary><strong>GitHub Copilot (VS Code and Copilot CLI)</strong></summary>

Copilot は Agent Skills をネイティブに読み取るため、同じ `SKILL.md` を変換なしで使えます。プロジェクトでは `.github/skills/`、`.claude/skills/`、`.agents/skills/`、グローバルでは `~/.copilot/skills/`、`~/.claude/skills/`、`~/.agents/skills/` を検索します。

### インストール

```bash
npx skills add quaz579/get-to-the-fucking-point-claude -a github-copilot        # このプロジェクト
npx skills add quaz579/get-to-the-fucking-point-claude -a github-copilot -g     # すべてのプロジェクト
```

CLI を使わない場合は、Copilot が検索するいずれかのディレクトリにスキルフォルダーをコピーします：

```bash
git clone https://github.com/quaz579/get-to-the-fucking-point-claude
mkdir -p ~/.copilot/skills
cp -R get-to-the-fucking-point-claude/skills/get-to-the-fucking-point-claude ~/.copilot/skills/
```

### 確認

チャット入力欄に `/` と入力し、`get-to-the-fucking-point-claude` が表示されることを確認します。または：

```bash
npx skills list
npx skills ls -g    # グローバルにインストールした場合
```

### 更新

```bash
npx skills update get-to-the-fucking-point-claude
```

または、`git pull` の後にフォルダーを再度コピーします。

### アンインストール

```bash
npx skills remove get-to-the-fucking-point-claude
```

または、配置先の skills ディレクトリから `get-to-the-fucking-point-claude` フォルダーを削除します。

### 有効化に関する注意

Copilot は `disable-model-invocation` を尊重します。Claude Code と同様、スキルを呼び出すまで何も適用されません（[#60](https://github.com/quaz579/get-to-the-fucking-point-claude/pull/60) で検証済み）。

### 常時有効（任意）

以下のブロックをプロジェクトの `.github/copilot-instructions.md` に追加します（Copilot はすべてのチャットでこれを読み込みます）：

```markdown
## 出力スタイル

読み手には ADHD があります。すぐ行動に移せるよう、すべての回答を次のように構成してください：

1. 回答または次の行動から始める。コマンド、パス、スニペットを先に示す。
2. 複数手順の作業には番号を付け、1 ステップにつき 1 つの明確な行動にする。
3. 2 分以内にできる次の行動を 1 つ示して終える。
4. 新しい問題を挙げる前に、現在の問題を終わらせる。
5. 各ターンで進捗を言い直す（「5 ステップ中 3 ステップ完了」）。
6. 所要時間は具体的な単位で示し、「少し」とは言わない。
7. 変更後は、何が動くようになったかを示す。
8. エラーは場所、原因、修正方法を淡々と示す。
9. リストは最大 5 項目にする。
10. 前置き、要約、締めの言葉を入れない。

例外：説明を求められた場合は十分に説明する。破壊的な操作の前には確認する。修正に 3 回失敗したら止まり、疑わしい前提を明示する。依頼が曖昧なら短い質問を 1 つする。
```

</details>

<details>
<summary><strong>Hermes</strong></summary>

### インストール

```bash
hermes skills install quaz579/get-to-the-fucking-point-claude/skills/get-to-the-fucking-point-claude
```

`/get-to-the-fucking-point-claude` と入力します。 The skill installs into `~/.hermes/skills/` and is exposed as a slash command at the next session start.

先に内容を確認したい場合は、このリポジトリをスキルソース（「tap」）として追加してから、検索してインストールします：

```bash
hermes skills tap add quaz579/get-to-the-fucking-point-claude
hermes skills search adhd
hermes skills install quaz579/get-to-the-fucking-point-claude/skills/get-to-the-fucking-point-claude
```

### 確認

```bash
hermes skills list
```

### 更新

```bash
hermes skills update get-to-the-fucking-point-claude
```

### アンインストール

```bash
hermes skills uninstall get-to-the-fucking-point-claude
```

tap も削除する場合は、`hermes skills tap remove quaz579/get-to-the-fucking-point-claude` を実行します。

### 常時有効（任意）

作業ディレクトリの `AGENTS.md`（Hermes が作業ディレクトリごとに読み込みます）、または全セッション用のペルソナ `SOUL.md` に追加します：

```markdown
## 出力スタイル

読み手には ADHD があります。すぐ行動に移せるよう、すべての回答を次のように構成してください：

1. 回答または次の行動から始める。コマンド、パス、スニペットを先に示す。
2. 複数手順の作業には番号を付け、1 ステップにつき 1 つの明確な行動にする。
3. 2 分以内にできる次の行動を 1 つ示して終える。
4. 新しい問題を挙げる前に、現在の問題を終わらせる。
5. 各ターンで進捗を言い直す（「5 ステップ中 3 ステップ完了」）。
6. 所要時間は具体的な単位で示し、「少し」とは言わない。
7. 変更後は、何が動くようになったかを示す。
8. エラーは場所、原因、修正方法を淡々と示す。
9. リストは最大 5 項目にする。
10. 前置き、要約、締めの言葉を入れない。

例外：説明を求められた場合は十分に説明する。破壊的な操作の前には確認する。修正に 3 回失敗したら止まり、疑わしい前提を明示する。依頼が曖昧なら短い質問を 1 つする。
```

</details>

<details>
<summary><strong>Kimi Code CLI</strong></summary>

### インストール

Kimi Code セッションを開始してから、次を実行します：

1. `/plugins` を実行する。
2. **Custom** を選ぶ。
3. `https://github.com/quaz579/get-to-the-fucking-point-claude` を貼り付けて Enter を押す。
4. **Trust and install** を選ぶ。

slash コマンド `/skill:get-to-the-fucking-point-claude` を使って、このスキルを明示的に呼び出します。

### 更新

Kimi Code セッションで `/plugins` を実行し、**I Have ADHD** にカーソルを合わせて `R` を押します。

### アンインストール

Kimi Code セッションで `/plugins` を実行し、**I Have ADHD** にカーソルを合わせて `D` を押します。

</details>


<details>
<summary><strong>Pi</strong></summary>

Pi は Agent Skills 標準を実装しているため、同じ `SKILL.md` を変換なしで直接読み込めます。呼び出し方法は他と異なり、スキルは `/skill:<name>` で呼び出します。

### インストール

```bash
npx skills add quaz579/get-to-the-fucking-point-claude -a pi -y
```

ファイルシステムを使う場合、Pi は `~/.pi/agent/skills/` と `~/.agents/skills/`（グローバル）、`.pi/skills/` と `.agents/skills/`（プロジェクト）からスキルを検出します：

```bash
git clone https://github.com/quaz579/get-to-the-fucking-point-claude
mkdir -p ~/.pi/agent/skills
cp -R get-to-the-fucking-point-claude/skills/get-to-the-fucking-point-claude ~/.pi/agent/skills/
```

Pi の `settings.json` でスキルのスラッシュコマンドを有効にします：

```json
{ "enableSkillCommands": true }
```

新しいセッションを開始して `/skill:get-to-the-fucking-point-claude` と入力します。

### 確認

```bash
npx skills list
```

または、セッションで `/skill:` と入力し、`get-to-the-fucking-point-claude` が一覧にあることを確認します。

### 更新

```bash
npx skills update get-to-the-fucking-point-claude
```

または、`git pull` の後にフォルダーを再度コピーします。

### アンインストール

```bash
npx skills remove get-to-the-fucking-point-claude
```

または、`~/.pi/agent/skills/get-to-the-fucking-point-claude` を削除します。

### 常時有効（任意）

プロジェクトの `AGENTS.md` に追加します：

```markdown
## 出力スタイル

読み手には ADHD があります。すぐ行動に移せるよう、すべての回答を次のように構成してください：

1. 回答または次の行動から始める。コマンド、パス、スニペットを先に示す。
2. 複数手順の作業には番号を付け、1 ステップにつき 1 つの明確な行動にする。
3. 2 分以内にできる次の行動を 1 つ示して終える。
4. 新しい問題を挙げる前に、現在の問題を終わらせる。
5. 各ターンで進捗を言い直す（「5 ステップ中 3 ステップ完了」）。
6. 所要時間は具体的な単位で示し、「少し」とは言わない。
7. 変更後は、何が動くようになったかを示す。
8. エラーは場所、原因、修正方法を淡々と示す。
9. リストは最大 5 項目にする。
10. 前置き、要約、締めの言葉を入れない。

例外：説明を求められた場合は十分に説明する。破壊的な操作の前には確認する。修正に 3 回失敗したら止まり、疑わしい前提を明示する。依頼が曖昧なら短い質問を 1 つする。
```

</details>


<details>
<summary><strong>Qwen Code</strong></summary>

### インストール

```bash
qwen extensions install quaz579/get-to-the-fucking-point-claude
```

Qwen Code は GitHub の短縮表記をサポートし、このリポジトリをネイティブ拡張機能としてインストールします。拡張機能は `skills/` 配下のスキルを検出します。

スキルを明示的に呼び出すには `/get-to-the-fucking-point-claude` を入力します。拡張機能をインストールしただけでは、スキルを呼び出すまで出力は変わりません。

### 確認

```bash
qwen extensions list
```

次に新しい Qwen Code セッションを開始し、以下を実行します：

```text
/skills
```

一覧に `get-to-the-fucking-point-claude` が表示されることを確認します。

### 更新

```bash
qwen extensions update get-to-the-fucking-point-claude
```

### アンインストール

```bash
qwen extensions uninstall get-to-the-fucking-point-claude
```

</details>

<details>
<summary><strong>Zed</strong></summary>

Zed の Agent は Agent Skills をネイティブに読み取るため、同じ `SKILL.md` を変換なしで使えます（従来の「Rules」は Skills と `AGENTS.md` の指示に置き換えられました）。

### インストール

Agent Panel で Skills マネージャーを開き、**Create skill from URL**（コマンドパレットでは `agent: create skill from url`）を選択して、次を貼り付けます：

```
https://github.com/quaz579/get-to-the-fucking-point-claude/blob/main/skills/get-to-the-fucking-point-claude/SKILL.md
```

すべてのプロジェクトで使う場合は **User** スコープ、1 つだけなら **Project** スコープに保存します。その後、Agent Panel で `/get-to-the-fucking-point-claude` と入力します。

ファイルシステムを使う場合は、リポジトリをクローンし、ユーザーの skills ディレクトリにスキルフォルダーを配置します：

```bash
git clone https://github.com/quaz579/get-to-the-fucking-point-claude
cp -R get-to-the-fucking-point-claude/skills/get-to-the-fucking-point-claude ~/.config/zed/skills/
```

### 確認

Agent Panel で Skills マネージャーを開き、`get-to-the-fucking-point-claude` が一覧にあることを確認します。または、`/` と入力して表示されることを確認します。

### 更新

同じ URL から再インポート（上書き）するか、`git pull` の後にフォルダーを再度コピーします。

### アンインストール

Skills マネージャーから `get-to-the-fucking-point-claude` を削除するか、`~/.config/zed/skills/get-to-the-fucking-point-claude` を削除します。

### 常時有効（任意）

個人用の `~/.config/zed/AGENTS.md` に追加します：

```markdown
## 出力スタイル

読み手には ADHD があります。すぐ行動に移せるよう、すべての回答を次のように構成してください：

1. 回答または次の行動から始める。コマンド、パス、スニペットを先に示す。
2. 複数手順の作業には番号を付け、1 ステップにつき 1 つの明確な行動にする。
3. 2 分以内にできる次の行動を 1 つ示して終える。
4. 新しい問題を挙げる前に、現在の問題を終わらせる。
5. 各ターンで進捗を言い直す（「5 ステップ中 3 ステップ完了」）。
6. 所要時間は具体的な単位で示し、「少し」とは言わない。
7. 変更後は、何が動くようになったかを示す。
8. エラーは場所、原因、修正方法を淡々と示す。
9. リストは最大 5 項目にする。
10. 前置き、要約、締めの言葉を入れない。

例外：説明を求められた場合は十分に説明する。破壊的な操作の前には確認する。修正に 3 回失敗したら止まり、疑わしい前提を明示する。依頼が曖昧なら短い質問を 1 つする。
```

</details>

<details>
<summary><strong>Cursor、OpenCode、Amp、その他の agent-skills 対応環境</strong></summary>

Agent Skills を読み取るすべての環境で動作します。`-a <agent>` を使用するエージェントに置き換えてください。

### インストール

```bash
npx skills add quaz579/get-to-the-fucking-point-claude                  # this workspace
npx skills add quaz579/get-to-the-fucking-point-claude -g               # すべてのプロジェクト
npx skills add quaz579/get-to-the-fucking-point-claude -a cursor -y     # one agent only
npx skills add quaz579/get-to-the-fucking-point-claude -a opencode -y
```

新しいエージェントチャットで `/get-to-the-fucking-point-claude` と入力します。

CLI を使わない場合は、エージェントが検索するパスにスキルフォルダーをコピーします：

```bash
git clone https://github.com/quaz579/get-to-the-fucking-point-claude
mkdir -p ~/.cursor/skills     # Cursor。OpenCode は .agents/skills、その他はエージェント固有のパスを使用
cp -R get-to-the-fucking-point-claude/skills/get-to-the-fucking-point-claude ~/.cursor/skills/
```

### 確認

```bash
npx skills list
npx skills ls -g    # グローバルにインストールした場合
```

### 更新

```bash
npx skills update get-to-the-fucking-point-claude
npx skills update -g    # グローバルにインストールした場合
```

### アンインストール

```bash
npx skills remove get-to-the-fucking-point-claude
npx skills remove get-to-the-fucking-point-claude -g    # グローバルにインストールした場合
```

### 常時有効（任意）

これをエージェントの永続ルールファイルに貼り付けます。Cursor：**Settings → Rules → User Rules**、または `.cursor/rules/` 配下のプロジェクトルールで `alwaysApply: true` を指定します。OpenCode：`~/.config/opencode/AGENTS.md`。

```markdown
## 出力スタイル

読み手には ADHD があります。すぐ行動に移せるよう、すべての回答を次のように構成してください：

1. 回答または次の行動から始める。コマンド、パス、スニペットを先に示す。
2. 複数手順の作業には番号を付け、1 ステップにつき 1 つの明確な行動にする。
3. 2 分以内にできる次の行動を 1 つ示して終える。
4. 新しい問題を挙げる前に、現在の問題を終わらせる。
5. 各ターンで進捗を言い直す（「5 ステップ中 3 ステップ完了」）。
6. 所要時間は具体的な単位で示し、「少し」とは言わない。
7. 変更後は、何が動くようになったかを示す。
8. エラーは場所、原因、修正方法を淡々と示す。
9. リストは最大 5 項目にする。
10. 前置き、要約、締めの言葉を入れない。

例外：説明を求められた場合は十分に説明する。破壊的な操作の前には確認する。修正に 3 回失敗したら止まり、疑わしい前提を明示する。依頼が曖昧なら短い質問を 1 つする。
```
</details>


## 有効化の仕組み

1. **インストール済み、未呼び出し。** Claude Code、Qwen Code、Codex では、明示的に呼び出すまで何も起きません。Claude Code と Qwen Code は `SKILL.md` の `disable-model-invocation: true` を、Codex は `agents/openai.yaml` の `policy.allow_implicit_invocation: false` を尊重します。その他の環境では、起動時に各スキルの説明を読み込み、自動で有効化する場合があります。
2. **明示的に呼び出す。** Claude Code と Qwen Code では `/get-to-the-fucking-point-claude`、Codex では `$get-to-the-fucking-point-claude` を入力します。そのセッションでルールが有効になります。「stop adhd mode」または「normal mode」で無効にできます。
3. **`~/.claude/.get-to-the-fucking-point-claude-always` を作成する**（Claude Code）。`SessionStart` フックが、すべてのセッションで最初のメッセージから完全なルールセットを読み込みます。
4. **上記の常時有効スニペットを追加する**（その他の環境）。中核となるルールをエージェントの永続コンテキストに保持します。

Claude Code、Qwen Code、Codex では中間状態はありません。有効にしていなければ無効です。

## トラブルシューティング

**`/get-to-the-fucking-point-claude` が自動補完に表示されない。** エージェントを再起動してください。プラグインのインデックスは起動時に読み込まれます。

**常時有効フラグが効かない。** プラグインを更新（`claude plugin marketplace update get-to-the-fucking-point-claude`）して再起動してください。フックは起動時に読み込まれ、フラグには `hooks/hooks.json` を含むバージョンが必要です。

**`claude plugin marketplace add` が失敗する。** `owner/repo` 形式を使用してください。ローカルパスは `.claude-plugin/` ではなく、リポジトリのルートを指す必要があります。

**インストールしたが回答にまだ前置きが入る。** 新しいセッションを開いてください。それでも逸脱する場合は、`skills/get-to-the-fucking-point-claude/SKILL.md` の文言をより厳密にしてください。

**別のルールを使いたい。** Fork して `skills/get-to-the-fucking-point-claude/SKILL.md` を編集し、自分のコピーに切り替えます：

```bash
claude plugin uninstall get-to-the-fucking-point-claude            # 先に上流のコピーを削除：
claude plugin marketplace remove get-to-the-fucking-point-claude   # fork と上流はどちらも同じ名前を使用
claude plugin marketplace add <your-username>/get-to-the-fucking-point-claude
claude plugin install get-to-the-fucking-point-claude@get-to-the-fucking-point-claude
```

再起動してから、`/get-to-the-fucking-point-claude` をもう一度呼び出します。

**`npx skills add` の後にスキルが見つからない。** 新しいエージェントチャットを開始してください。スキルはセッション開始時にインデックス化されます。フォルダーがエージェントの検索先（Cursor は `~/.cursor/skills/`、OpenCode は `.agents/skills/`）に配置され、frontmatter の `name` がフォルダー名と一致していることを確認してください。
