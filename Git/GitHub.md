# GitHub

## パスワードのキャッシュ

- push時に毎回パスワードを聞かれるのが面倒な場合に有効
    - [Caching your GitHub password in Git](https://help.github.com/articles/caching-your-github-password-in-git/#platform-windows)
        - Windowsの場合

## SSL認証でのエラー

- `SSL certificate problem: Invalid certificate chain`のエラー対処方法
    - `git config --global http.sslVerify false`でSSL認証を無視する
        - セキュリティが弱くなるので一時的な対処
    - セキュリティ面を考慮する場合は新たに証明書をとってくる必要がある
        - http://limitusus.hatenablog.com/entry/20120529/1338306372