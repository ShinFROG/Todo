# Todo

GitHub Pages で動く Todo アプリ（試験版）。

このリポジトリは公開されているため、**画面（コード）だけ**を置いている。
Todo の中身は別の**非公開リポジトリ**に JSON として保存し、ブラウザから GitHub API で読み書きする。

```
[ブラウザ] ── このリポジトリの Pages（画面だけ・公開）
    │  初回だけトークンを入力 → この端末のブラウザ内に保存
    ▼
GitHub API ── 非公開リポジトリの todos.json を読み書き
```

- ページを開いても、トークンが無ければ設定画面しか表示されない
- 保存のたびに非公開リポジトリへコミットされるので、変更履歴が残る
- 2 台で同時に編集して衝突した場合は、最新を読み直してから自分の変更を適用し直す
- 外部のスクリプトや CDN は読み込まず、通信先は `api.github.com` だけに制限している（CSP）
- 接続先が公開リポジトリだった場合は接続を拒否する

## 使い方

1. **トークンを作る**
   GitHub → Settings → Developer settings → Personal access tokens → **Fine-grained tokens** → Generate new token
   - Repository access: **Only select repositories** → データ用の非公開リポジトリだけを選ぶ
   - Permissions → Repository permissions → **Contents: Read and write**
   - Expiration（有効期限）は必ず設定する
2. Pages の URL を開き、データ用リポジトリ・ファイル名・トークンを入力して「接続する」

## 注意

このリポジトリには個人的な情報を書かない（Issues、コミットメッセージを含む）。
公開リポジトリの履歴は、後から消しても完全には消えない。
