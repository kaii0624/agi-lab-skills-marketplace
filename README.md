# Handson Hub Agent — easy-handson

生成AIの最新機能をリサーチして、社内ハンズオンをすぐ開催できる一式を生成するエージェントです。
DX推進担当者が「ハンズオンをやりたいけど準備が大変」を解消するために作りました。

## easy-handson を試すには

```bash
# In Claude Code
/plugin marketplace add kaii0624/agi-lab-skills-marketplace
/plugin install easy-handson@agi-lab-skills
```

## コマンド

| コマンド | 内容 |
|---------|------|
| `/handson-research` | Anthropic公式から直近1ヶ月のClaude Code新機能TOP3をリサーチしてPPTX生成・自動プレビュー |
| `/handson-research [キーワード]` | キーワード指定でリサーチ（例: `/handson-research hooks`） |
| `/handson-create [機能名]` | 選んだ機能のスライド・手順書・周知文を一括生成・自動プレビュー |

## 生成物

`outputs/{機能名スラッグ}/` に以下が生成されます。

- `slides.pptx` — 紹介スライド（7枚、最終ページがディスカッション）
- `handson.md` — 参加者向け手順書（15分で完走できる粒度）
- `announce.txt` — Teams/Slack 周知文のテンプレート

## 必要環境

- Claude Code（インストール・ログイン済み）
- marp CLI（PPTX生成に使用）

```bash
npm install -g @marp-team/marp-cli
```

## Repository Structure

```text
.claude-plugin/
└── marketplace.json

plugins/
└── easy-handson/
    ├── .claude-plugin/
    │   └── plugin.json
    ├── skills/
    │   ├── handson-research/
    │   │   └── SKILL.md
    │   └── handson-create/
    │       └── SKILL.md
    └── outputs/           ← 生成物の保存先（自動作成）
```

## License

MIT
