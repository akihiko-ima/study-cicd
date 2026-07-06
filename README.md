# study-cicd

### huskyの自動設定
`chmod +x .husky/pre-commit`も必要
```bash
git config core.hooksPath .husky
```

#### actionlintのチェックコマンド
```bash
docker run --rm -v "$(pwd):$(pwd)" -w "$(pwd)" rhysd/actionlint:latest
```

#### go テストコード実行
```bash
go test go/excellent/*.go
```
