# study-cicd

#### actionlintのチェックコマンド
```bash
docker run --rm -v "$(pwd):$(pwd)" -w "$(pwd)" rhysd/actionlint:latest
```

#### go テストコード実行
```bash
go test go/excellent/*.go
```
