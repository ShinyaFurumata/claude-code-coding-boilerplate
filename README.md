# 概要
このボイラープレートは Claude Code の性能を最大限活かして、AI エージェントが下記を意識して自走できるように作ったものです。
補助的にCodexを利用するために、Codexのロングランタスク用の環境も作成しています。
- 長時間タスクを行うことができる
- Claude CodeのFrontEndSkillを有効活用することができる
- 自分好みのフレームワークやライブラリを選択できる

# 使い方
## SPEC の準備
SPEC.mdを完成させてください。

## MCP の準備
MCP-example.md を確認して、エージェントに合わせた MCP 設定を行ってください。
- Claude Code, Codex, Cursor用のサンプルMCPファイルを作成済みです
- Context7はAPI Keyを用意してください（無料）
- Motion+の有料版では、API Keyを用意する必要があります。無料版の場合は適宜内容を変更してください。

## 環境構築 の開始
```
SPEC.mdを確認して、0からの環境構築するまでの手順をfeatures.jsonに追加してください。
```

# Vibe Coding の仕方
## 小さなタスク
特に意識することはないです。
通常通り、ファイルのメンション等を用いて、エージェントに指示を出してください。

## 長期的のタスク実行
### Claude Code
Plan mode を利用して、タスクの説明をしてください。

### Codex
長時間のタスクを ExecPlan を作ることを明示的に指示して、プロンプトを作成してください。
※ 指示がなくても、複雑な設計や大規模な作業であれば、エージェントは自動的に ExecPlan を実行します。

# おすすめの開発フロー
1.実装
小さなタスクは Cursor の Agents で、長期的なタスクは Codex, Claude Code で実装します。

2.ローカルレビュー
- Claude Codeから`/code-review local`(uncommit changes)または`/code-review development`(develop branchからの差分)を実行します
- or Codex CLI を利用して、`/review`コマンドを実行します。

3.PR レビュー
Codex で Codex review を走らせます。

4.マージ

# TIps
## どの粒度で Exec プランを作るか迷ったとき
まずは環境構築・ライブラリ設定だけをお願いする

```
@SPEC.md を読んで、最小限プロダクトを作るための環境構築をするタスクをfeatures.jsonに追加してください。
まずは各フレームワークのインストールとライブラリのインストール、設定まででよいです。プロダクトを作り始める必要はありません。
```

ExacPlan の粒度と順番のアドバイスをもらう
```
@SPEC.md を確認して、MVP時点でのゴールを達成するためにどの粒度、順番でタスクをこなすべきかを考え、features.jsonに追加してください。
```

## 参考になる記事
Designが気に入らないときは、frontend-design-skillを導入すると良い
- https://www.claude.com/blog/improving-frontend-design-through-skills
- https://www.anthropic.com/engineering/effective-harnesses-for-long-running-agents
- https://platform.claude.com/docs/en/build-with-claude/prompt-engineering/claude-4-best-practices#long-horizon-reasoning-and-state-tracking