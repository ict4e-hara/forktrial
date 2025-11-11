# forktrial — Git研修用リポジトリ

このリポジトリは、Git の基礎から実践的な操作までを学ぶための演習用リポジトリです。授業や社内研修、ハンズオンワークショップでの利用を想定しています。実際に手を動かしながら、フォーク・クローン・ブランチ・マージ・コンフリクト解決・PR（プルリクエスト）などの流れを体験できます。

## 目的
- Git の基本操作を安全に体験する（ローカル・リモートの操作）
- ブランチ戦略と Pull Request ベースのワークフローを理解する
- マージコンフリクトや履歴操作（rebase / squash / revert など）を実践で学ぶ

## 推奨対象
- Git 普段使っているが、再度確認したい方
- コードレビューや共同開発の練習をしたい方

## リポジトリ構成（例）
- exercises/ — 演習用問題（課題ファイル）
- solutions/ — 解答例（参加者は直接触らない）
- docs/ — 解説資料やコマンドまとめ
- .github/ — ワークフローやテンプレート（PR/ISSUE）

※実際のフォルダは随時追加・更新されます。演習を追加したい場合は issue を立ててください。

## はじめ方（基本ワークフロー）
1. このリポジトリをフォーク
2. ローカルにクローン
   ```bash
   git clone https://github.com/<あなたのユーザ名>/forktrial.git
   cd forktrial
   ```
3. ブランチを作成して作業
   ```bash
   git checkout -b feature/your-name-task1
   # 変更を行う
   git add .
   git commit -m "feat: 課題1の実装（短い説明）"
   git push origin feature/your-name-task1
   ```
4. GitHub 上で Pull Request を作成
5. 指定されたレビューワーにコードレビューを依頼、指摘を反映してマージ

## 演習（サンプル）
- 課題 A: README に自分の名前を追加して PR を作る
- 課題 B: 新しいファイルを追加し、ブランチ → PR → マージの流れを体験する
- 課題 C: 故意にコンフリクトを発生させて解決する
- 課題 D: コミット履歴を squash して整理する
- 課題 E: rebase を使って履歴を整理する（上級）

各演習には手順と期待される成果物を exercises/ 以下に用意しています（担当インストラクタが配布）。

## コミットメッセージのガイドライン（推奨）
- type: short description（例: feat: add exercise-1）
- type は feat / fix / docs / chore / refactor / test など
- 1行で要点を。詳細は本文に追記しても可

## よく使うコマンド例
- 変更の確認: git status, git diff
- 履歴の確認: git log --oneline --graph --all
- ブランチ一覧: git branch -a
- リモートの取得: git fetch origin
- コンフリクト解消後: git add . && git commit
- 最新の main を取り込む（merge）:
  ```bash
  git checkout feature/your-branch
  git fetch origin
  git merge origin/main
  ```
- 最新の main を取り込む（rebase・上級者向け）:
  ```bash
  git checkout feature/your-branch
  git fetch origin
  git rebase origin/main
  ```

## PR 作成チェックリスト（テンプレ）
- [ ] 目的と変更点を明確に書いた
- [ ] ローカルでビルド・テストが通っている（必要な場合）
- [ ] レビュワーを指名した
- [ ] 必要であればスクリーンショットや補足資料を添付した

## トラブルシューティング（よくあるケース）
- 間違ってコミットを取り消したい: git revert または git reset（注意して利用）
- ローカルでうまく戻せない / 取り消しが必要: git reflog を確認して復元
- マージ後に不具合があれば revert で PR を作成してロールバック

## コントリビューション
このリポジトリは学習目的が主です。新しい演習や改善案は Issue を立ててください。PR での直接修正提案も歓迎します。

## ライセンス
研修用リポジトリのため、特に制約がない場合は MIT ライセンスを推奨します。必要に応じて LICENSE ファイルを追加してください。

---

作成者 / Maintainer: @ict4e-hara
