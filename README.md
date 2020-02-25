# jenkins-setup

## クライアントセットアップ

インストーラーを実行。（Mac 専用）

```
$ cd client-setup
$ bash setup.sh
```

## サーバーセットアップ

`server-setup/inventory/hosts`内のドメイン名を変更する。
ドメイン名または、IP アドレスを設定。

```
[jenkins-server]
centos-jenkins.localdomain  ← ここ
```

設定後、以下のコマンドを実行。

```
$ cd server-setup
$ playbook -i inventory/hosts playbook.yml
```
