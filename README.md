# Kuchibue 公式サイト

iOS アプリ **Kuchibue** のサポートページとプライバシーポリシー。
App Store Connect の「サポート URL」「プライバシーポリシー URL」に登録する。

GitHub Pages で公開する静的サイト（外部リソースへの依存なし・HTML と CSS のみ）。

## 構成

| ファイル | 用途 | App Store Connect での登録先 |
|---|---|---|
| `index.html` | 使い方・FAQ・問い合わせ先 | サポート URL |
| `privacy.html` | プライバシーポリシー | プライバシーポリシー URL |
| `style.css` | 共通スタイル（ダークモード対応） | — |

## 公開前に埋める箇所

1. **`SUPPORT_EMAIL_PLACEHOLDER`**（`index.html` / `privacy.html` の2箇所ずつ）
   問い合わせ先のメールアドレス。公開ページに載るため、個人の常用アドレスではなく
   このアプリ専用のアドレスを用意することを勧める。
2. **`EFFECTIVE_DATE_PLACEHOLDER`**（`privacy.html`）
   プライバシーポリシーの最終更新日（例: 2026年7月26日）。

## 公開手順

このリポジトリは**公開**にする必要がある（無料アカウントでは非公開リポジトリから
GitHub Pages を公開できないため）。アプリ本体のリポジトリは非公開のままでよい。

```sh
# 1. 公開リポジトリを作って push する
gh repo create kuchibue-site --public --source=. --remote=origin --push

# 2. GitHub Pages を有効にする（main ブランチのルートを公開）
gh api -X POST repos/:owner/kuchibue-site/pages -f 'source[branch]=main' -f 'source[path]=/'
```

数分後に以下で公開される。

- サポート URL: `https://<ユーザー名>.github.io/kuchibue-site/`
- プライバシーポリシー URL: `https://<ユーザー名>.github.io/kuchibue-site/privacy.html`

## 更新するとき

ファイルを直して `git push` するだけで反映される（反映まで数分かかる）。

アプリの機能を変えたら、このサイトの記述（特に FAQ とプライバシーポリシーの
「端末内に保存されるもの」）も実態と合っているか確認すること。
**プライバシーポリシーの記述と App Store Connect のプライバシー申告は必ず一致させる。**
