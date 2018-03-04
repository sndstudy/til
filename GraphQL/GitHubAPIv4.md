# GitHub API v4

- [GraphQL API Explorer | GitHub Developer Guide](https://developer.github.com/v4/explorer/)
    - このサイトでGitHubのAPIを手軽に試すことができる

## 例

GitHub GraphQL API v4で自分(sndstudy)の**til**というリポジトリの作成日時を取得するGraphQL

```
query { 
	repository(owner:"sndstudy",name:"til"){
        createdAt
  }
}
```

### 説明(Google翻訳直訳)

- query
    - The query root of GitHub's GraphQL interface.
    - GitHubのGraphQLインターフェイスのクエリルート。
- repository
    - Lookup a given repository by the owner and repository name.
    - 指定されたリポジトリを所有者とリポジトリ名で検索します。
    - owner
        - リポジトリ所有者名
    - name
        - リポジトリ名
    - Repositoryという型の情報が返ってくる
        - docにtypeが記載されていた
- createdAt
    - Identifies the date and time when the object was created.
    - オブジェクトが作成された日時を識別します。
    - typeはDateTime
         - An ISO-8601 encoded UTC date string.
