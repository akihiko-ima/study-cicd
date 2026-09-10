# study-cicd

## 概要

本リポジトリは書籍を参考にした動作確認用リポジトリです。
書籍名: GitHub CI/CD実践ガイド  
著者: 野村友規　著  
[書籍リンク](https://gihyo.jp/book/2024/978-4-297-14173-8)

## コマンド

#### huskyの自動設定

`chmod +x .husky/pre-commit`も必要

```bash
git config core.hooksPath .husky
```

#### actionlint(静的解析)のチェックコマンド

- actionlint: GitHub Actionsのワークフローファイルを検査するツール

```bash
docker run --rm -v "$(pwd):$(pwd)" -w "$(pwd)" rhysd/actionlint:latest
```

#### go テストコード実行

```bash
go test go/excellent/*.go
```

## コンテナレジストリー

- アカウント名の環境変数へセット

```bash
export GHCR_USER=$(gh config get -h github.com user)
```

- コンテナイメージのビルド

```bash
docker build -t ghcr.io/${GHCR_USER}/example:latest docker/example/
```

- Container Registryへログイン

```bash
gh auth token | docker login ghcr.io -u ${GHCR_USER} --password-stdin
```

- コンテナイメージをpush

```bash
docker push ghcr.io/${GHCR_USER}/example:latest
```
