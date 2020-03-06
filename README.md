# jenkins-setup

## クライアントセットアップ

インストーラーを実行。（Mac 専用）

```
$ cd client-setup
$ bash setup.sh
```

## サーバーセットアップ

`server-setup/inventory/hosts` 内の設定を変更する。

```
[jenkins-server]
xxx.xxx.xxx.xxx  ← ドメイン名または、IP アドレスを設定

[jenkins-server:vars]
ansible_port=22  ← sshで接続するので、ポート番号を指定（していない場合、22で接続する）
ansible_ssh_user=ec2-user  ← Ansibleでログインするユーザー名
#ansible_ssh_pass=  ← Ansibleでログインするユーザーのパスワード（なければコメントアウトでOK）
ansible_ssh_private_key_file=~/.ssh/xxxxxx.pem  ← サーバーへの接続に使用する鍵（なければコメントアウトでOK）
```

設定後、以下のコマンドを実行。

```
$ cd server-setup

# rootユーザーで実行する場合、パスワードが必要なのでこちらを実行
$ ansible-playbook -i inventory/hosts --ask-sudo-pass playbook.yml

# パスワードが不要の場合、こちらを実行
$ ansible-playbook -i inventory/hosts playbook.yml
```

`http:<サーバーのグローバルIPアドレス>:8080` で msg 内の値が初期パスワードを入力。

```
TASK [jenkins : Password ↓] ****************************************************************************************************************************
ok: [52.199.115.193] => {
    "msg": "d75d3ea082b74381af01d19a137015a4"
}
```
