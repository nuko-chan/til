## 毎回やる手順（最短 4 ステップ）

1. Issue 作る（1 コマンド）

`gh issue create -t "..." -b "Goal:\n...\n\nAcceptance:\n- ..."`

2. その Issue からブランチ作ってチェックアウト（1 コマンド）

Issue 番号が 123 なら：

`gh issue develop 123 --checkout --name "feat/123-short-slug"`

3. 普通に作業して push

`git push -u origin HEAD`

4. PR 作る（Closes だけ入れる）

`gh pr create -t "..." -b "Closes #123"`

これで Issue ⇄ Branch ⇄ PR が一本の糸で繋がって、番号が増えても追跡が破綻しにくい

## これ以上足さない方がいいもの（最小運用を崩す原因）

- Project 上で手でステータスを動かす（すぐ嘘になる）
- Issue と別に独自のタスク番号体系を作る（番号地獄の再発）
- ブランチ名に Issue 番号を入れない（リンク切れが起きる）

## Issue 本文は、最低でもこの 2 行だけでいい：

1. Goal: 何を達成するか
2. Acceptance: どうなったら完了か（箇条書き 1〜3 個）
