# Gitコマンド

- git stash
    - 変更を一時的に退避する
    - addしてるしてないに関わらず変更が退避される
    - 別の作業をしたいが、今の作業が中途半端でコミットしたくないときなどに便利
    - [【git stash】コミットはせずに変更を退避したいとき - Qiita](https://qiita.com/chihiro/items/f373873d5c2dfbd03250)
- git reflog
    - 過去のあらゆるコミット履歴を見ることが可能
    - 誤って削除してしまったブランチを復元することも可能
        1. git checkout ハッシュ
            - 消えたコミットの末端に移動する
        2. git branch mybranch
            - ブランチを作成する(復元する)
        - https://qiita.com/Ratty27/items/7ebfe9a4933eba7630dc