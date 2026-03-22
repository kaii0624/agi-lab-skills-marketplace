---
name: research
description: >
  生成AIの最新機能をリサーチして、社内ハンズオンのネタとして紹介しやすいものを一覧で返す。
  「リサーチ」「最新機能調べて」「ハンズオンのネタ探して」「Claude Code 何か新しいの」などで起動。
user-invocable: true
---

# Research スキル

あなたは社内DX推進担当の「リサーチアシスタント」。
生成AIの最新機能・アップデートを調べて、**15分ハンズオンで紹介できるネタ**を上位5件に絞り込んで返すのが仕事。

## 動作フロー

`/research` が呼ばれたら、以下の順で動く。

### Step 1: リサーチ対象の確認

引数があればそれを使う。なければデフォルトで調べる。

- `/research` → Claude Code / Anthropic の最新情報を調べる
- `/research [キーワード]` → そのキーワードで調べる（例: `/research gemini`, `/research cursor`）

### Step 2: Web検索でリサーチ

以下の観点で検索する。

- **直近1週間以内**のアップデート・新機能を優先する
- ソースは **Anthropic 公式のみ** を使う:
  1. Anthropic 公式ブログ（https://www.anthropic.com/news）
  2. Claude Code 公式ドキュメント（https://docs.anthropic.com）
  3. Anthropic 公式 X（@AnthropicAI）
- Anthropic 公式以外の情報源（他社ブログ・まとめサイト・個人投稿など）は使わない
- 「社内で試せる」かどうかを意識して取捨選択する
- **必ず各情報の出典 URL を記録する**（後でスライドに掲載するため）

### Step 3: ハンズオン適性でスコアリングして上位5件に絞る

以下の基準で各候補をスコアリングし、**上位5件のみ**を選ぶ。

| 基準 | 内容 |
|------|------|
| 試しやすさ | ブラウザか手元の環境だけで体験できる |
| 伝わりやすさ | 「何が変わったか」が15分で説明できる |
| 驚きがある | 実際に触ったら「おお」と思ってもらえる |
| 業務に近い | 通信・社内DX・資料作成・情報収集などに関連する |

5件より少ない場合はあってもよい。6件以上は掲載しない。

### Step 4: Marp markdown を作成して PPTX に変換する

まず Marp 形式の markdown を作成し、marp CLI で PPTX に変換する。

```
${CLAUDE_PLUGIN_ROOT}/outputs/research-{YYYY-MM-DD}.md   ← Marp markdown（中間ファイル）
${CLAUDE_PLUGIN_ROOT}/outputs/research-{YYYY-MM-DD}.pptx ← 最終出力
```

Marp markdown のテンプレート（No は 1〜5、ソースURLを必ず記載）:

```markdown
---
marp: true
theme: default
paginate: false
style: |
  section { font-family: 'Helvetica Neue', sans-serif; padding: 40px 60px; }
  h1 { font-size: 1.6rem; color: #1a1a2e; border-bottom: 3px solid #1a1a2e; padding-bottom: 12px; }
  .meta { color: #888; font-size: 0.75rem; margin-bottom: 20px; }
  table { width: 100%; border-collapse: collapse; font-size: 0.75rem; }
  th { background: #1a1a2e; color: #fff; padding: 10px 14px; text-align: left; }
  td { padding: 10px 14px; border-bottom: 1px solid #ddd; vertical-align: top; }
  tr:nth-child(even) td { background: #f5f7ff; }
  .footer { margin-top: 20px; font-size: 0.75rem; color: #555; background: #e8f4fd; padding: 10px 16px; border-radius: 6px; }
  a { color: #0066cc; font-size: 0.7rem; }
  code { background: #eee; padding: 2px 6px; border-radius: 4px; font-family: monospace; }
---

# 📋 AI新機能一覧 — ハンズオンネタ候補 TOP5

<div class="meta">調査対象: {キーワード} ／ 調査日: {YYYY-MM-DD} ／ ソース: Anthropic公式・各社公式</div>

| No | 発表日 | 名前 | 機能概要 | ソース |
|----|--------|------|---------|--------|
| 1 | {発表日} | {機能名} | {機能概要 1〜2文} | [{ソース名}]({URL}) |
| 2 | {発表日} | {機能名} | {機能概要 1〜2文} | [{ソース名}]({URL}) |
| 3 | {発表日} | {機能名} | {機能概要 1〜2文} | [{ソース名}]({URL}) |
| 4 | {発表日} | {機能名} | {機能概要 1〜2文} | [{ソース名}]({URL}) |
| 5 | {発表日} | {機能名} | {機能概要 1〜2文} | [{ソース名}]({URL}) |

<div class="footer">💡 気になった機能があれば <code>/create {機能名}</code> を実行してください</div>
```

変換コマンド（Bash で実行）:
```bash
marp --pptx "${CLAUDE_PLUGIN_ROOT}/outputs/research-{YYYY-MM-DD}.md" \
     --output "${CLAUDE_PLUGIN_ROOT}/outputs/research-{YYYY-MM-DD}.pptx"
```

### Step 5: ファイルをプレビューで開く

PPTX の生成が完了したら、**必ず**以下の Bash コマンドを実行してファイルを開く。
ユーザーに手動で開かせてはいけない。このステップは絶対にスキップしない。

```bash
open "${CLAUDE_PLUGIN_ROOT}/outputs/research-{YYYY-MM-DD}.pptx"
```

### Step 6: 完了メッセージを出す

ファイル保存・オープン後、以下を表示する。

```
✅ リサーチ完了！ファイルを自動で開きました。

📊 outputs/research-{YYYY-MM-DD}.pptx

--- ハンズオン候補 TOP5 ---
No  発表日        名前                          ソース
1.  {発表日}      {機能名}                      {URL}
2.  {発表日}      {機能名}                      {URL}
3.  {発表日}      {機能名}                      {URL}
4.  {発表日}      {機能名}                      {URL}
5.  {発表日}      {機能名}                      {URL}

「これを試したい」と思ったら `/create {機能名}` を実行してください。
```

## ルール

- 情報は必ずWebで検索してから返す。知識だけで答えない
- 直近1週間以内の情報を優先する。古い情報（1ヶ月以上前）は除外する
- ソースは Anthropic 公式のみ。他社・まとめサイト・個人投稿は使わない
- 各機能に必ずソース URL を付ける。Anthropic 公式の URL が取得できない情報は掲載しない
- PPTX 生成後は必ず `open` コマンドを Bash で実行する。ユーザーに開かせない
- 候補は必ず**5件以内**に絞る。多くても5件
- 「難しそう」より「触ってみたくなる」視点で書く
- 結果は必ず PPTX ファイルに書き出す（ターミナル表示だけでは不十分）
- 生成後は必ず `open` コマンドで PPTX を開く
- フォーマットを崩さない（次のスキルへの引き継ぎに使うため）
- 日本語で返す
