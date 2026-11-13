# 開発の進め方

AIツールへのルールは [CLAUDE.md](../CLAUDE.md) にまとめています。

## ブランチ運用

- `main` は保護されていて、直接 push できない（GitHub の Ruleset `protect-main`）
- 作業はすべて、`main` から作ったブランチで行い、プルリクエストで `main` に取り込む
- 1つのタスク ＝ 1つのブランチ ＝ 1つのプルリクエスト

### ブランチ名

| 種類 | 名前の例 | 使うとき |
| --- | --- | --- |
| `feature/` | `feature/nutrition-calc` | 機能の追加 |
| `fix/` | `fix/mets-rounding` | 不具合の修正 |
| `docs/` | `docs/requirements` | ドキュメントだけの変更 |
| `chore/` | `chore/setup-eslint` | 設定や環境づくりなどの雑務 |

### 作業の流れ

```bash
git switch main
git pull                              # main を最新にする
git switch -c feature/xxx             # ブランチを作って移動する
# 作業してコミット
git add .
git commit -m "feat: ○○を追加"
git push -u origin feature/xxx        # GitHub に送る
# GitHub でプルリクエストを作り、内容を確認してマージする
git switch main
git pull                              # マージ後の main を取り込む
git branch -d feature/xxx             # 使い終わったブランチを消す
```

## コミットメッセージ

最初に種類を書き、そのあとに内容を日本語で書く。

| 書き出し | 意味 |
| --- | --- |
| `feat:` | 機能の追加 |
| `fix:` | 不具合の修正 |
| `docs:` | ドキュメントの変更 |
| `test:` | テストの追加・修正 |
| `refactor:` | 動きを変えないコードの整理 |
| `chore:` | 設定・環境・雑務 |

例：`feat: メッツによる消費エネルギーの計算を追加`

## プルリクエスト

- テンプレート（`.github/pull_request_template.md`）にそって、何を・なぜ変えたか、どう確認したか、AIをどう使ったかを書く
- マージは **Squash and merge**（プルリクエストの中のコミットを1つにまとめて、main の履歴を読みやすくする）
- Week 3 以降は、自動テスト（GitHub Actions）が通らないとマージしない

## フォルダ構成

Week 3 でプロジェクトを作るときに追記する。
