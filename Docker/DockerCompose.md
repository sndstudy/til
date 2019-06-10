# DockerComposeとh

- マルチコンテナのDockerアプリを定義するツール
- 開発環境や自動テストの実行環境を構築するのに使われる
- yamlで記載する

## Composeの実行ステップ

1. Dockerfileまたは使用するイメージをDockerHubに用意する
2. docker-compose.ymlを定義する
3. `docker-compose up`を実行する
