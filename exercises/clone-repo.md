# リポジトリのクローン演習

この演習では、このリポジトリ (ict4e-hara/forktrial) をあなたのPCにクローンして、基本的な操作（ブランチ作成、コミット、プッシュ、Pull Request 作成）を行う手順を学びます。

---

## 前提
- Git がインストールされていること（バージョン確認: `git --version`）
- GitHub アカウントを持っていること（演習で Fork を使う場合）
- SSH の設定を使う場合は SSH 鍵を GitHub に登録していること

---

## 1. リポジトリをフォーク（任意だが推奨）
授業や研修で配布リポジトリを自分のアカウントにコピーするため、右上の "Fork" ボタンを押して自分の GitHub アカウントへフォークします。

（直接クローンしても演習はできますが、PR を送る練習をするならフォークしてください）

---

## 2. クローン（HTTPS）
HTTPS を使う場合の手順:

1. フォークしたリポジトリ（または元のリポジトリ）ページで "Code" ボタンを押し、"HTTPS" の URL をコピー。
2. ターミナルでクローンするディレクトリに移動して次を実行:

```bash
# 例: HTTPS を使ってクローン
git clone https://github.com/<あなたのユーザ名>/forktrial.git
cd forktrial
```

代わりに、元リポジトリをクローンする場合は URL を https://github.com/ict4e-hara/forktrial.git に置き換えてください。

---

## 3. クローン（SSH）
SSH を使う場合の手順:

1. GitHub に SSH 鍵を登録済みであることを確認します（https://github.com/settings/keys）。
2. リポジトリの "Code" で SSH の URL をコピーし、次を実行:

```bash
# 例: SSH を使ってクローン
git clone git@github.com:<あなたのユーザ名>/forktrial.git
cd forktrial
```

または元リポジトリを直接クローンするには git@github.com:ict4e-hara/forktrial.git を使用します。

---

## 4. リモートの確認
クローン後、どのリモートが設定されているか確認します:

```bash
git remote -v
```

出力例（フォークをクローンした場合）:

```
origin  https://github.com/<あなたのユーザ名>/forktrial.git (fetch)
origin  https://github.com/<あなたのユーザ名>/forktrial.git (push)
```

元リポジトリ（upstream）を追加しておくと便利です（main を同期するため）:

```bash
git remote add upstream https://github.com/ict4e-hara/forktrial.git
# 確認
git remote -v
```

---

## 5. 基本的な操作の流れ（演習）
1. ブランチを作る

```bash
git checkout -b feature/add-your-name
```

2. ファイルを作成/編集（例: exercises/your-name.md に自己紹介を書く）

3. 変更をステージしてコミット

```bash
git add exercises/your-name.md
git commit -m "feat: add your-name exercise file"
```

4. リモートへプッシュ

```bash
git push origin feature/add-your-name
```

5. GitHub 上で Pull Request を作成してマージの流れを体験

---

## 6. 確認コマンド・デバッグ
- 現在のブランチ: `git branch --show-current`
- 変更の状態: `git status`
- ログ確認: `git log --oneline --graph --decorate -n 20`
- リモートの取得: `git fetch upstream`
- main を最新にする（マージ）:

```bash
git checkout main
git fetch upstream
git merge upstream/main
```

- main を最新にする（rebase、上級者向け）:

```bash
git checkout feature/add-your-name
git fetch upstream
git rebase upstream/main
```

---

## 7. よくあるトラブルと対処
- 認証エラー（HTTPS）: パスワード入力が求められる場合は PAT（Personal Access Token）の使用を検討してください。GitHub はパスワード認証を廃止しています。
- SSH が使えない/Permission denied: SSH 鍵が登録されているか確認し、`ssh -T git@github.com` で接続テストを行ってください。
- push が拒否された: リモートの main に自分のローカルが追いついていない可能性があります。`git pull --rebase` や upstream から取り込んで解決してください。

---

## 8. 演習タスク（提出まで）
1. このリポジトリをフォークしてクローンする（または直接クローン）
2. `feature/<あなたの名前>-intro` ブランチを作成
3. `exercises/<your-github-username>.md` を作成し、名前・所属・今日の学びなどを記載
4. コミットしてプッシュ、PR を作成してレビュー／マージを体験

---

## 参考
- Git 入門: https://git-scm.com/book/ja/v2
- GitHub SSH 鍵の設定: https://docs.github.com/ja/authentication/connecting-to-github-with-ssh

---

このファイルを使って演習を進めてください。問題が出たら `git status` や `git log` の出力を教えてください。