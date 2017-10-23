# ansible-isucon7q

```
git submodule update --init --recursive
cat <<EOS
[web]
<<your web server addresses>>

[db]
<<your db server addresses>>
EOS
ansible-playbook -i hosts -u root ansible/playbook.yml
```


## 複数台で動かす場合

`isucon7q-qualify/files/app/env.sh` の `ISUBATA_DB_HOST` でDBの接続先をしていしているので、
これをデータベースサーバーのIPアドレスに置き換える。

> デフォルトだとTCPが127.0.0.1しかbindしてないので、複数台構成に対応するには
> `/etc/mysql/mysql.conf.d/mysqld.cnf` で `bind-address = 127.0.0.1` になっている
> 場所を `bind-address = 0.0.0.0` に書き換える。
>
> https://github.com/isucon/isucon7-qualify#データベース初期化

