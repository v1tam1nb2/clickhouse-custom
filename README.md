# clickhouse-custom

検証用ClickHouseサーバー。

# ソースの構成

```
.
├── README.md
├── data
│   ├── etc
│   │   └── clickhouse-server
│   │       ├── config.d
│   │       │   ├── docker_related_config.xml
│   │       │   ├── loggin_level.xml # ログレベルの定義
│   │       │   ├── logging_off.xml  # query_thread_logなどを無効化する設定
│   │       │   ├── timezone_default.xml # タイムゾーンの設定
│   │       │   └── zstd_default.xml # データ圧縮形式をzstdを指定
│   │       └── users.d # ユーザーを作成したい場合はここに配置
└── docker-compose.yaml # 構築用の設定ファイル
```

# コンテナ構築

所定のディレクトリにソースを配置し、`docker-compose.yaml` があるディレクトリで以下を実行する。

※ WSLの場合は、WSL側の所定のディレクトリに配置する。

```shell
docker-compose up -d
```

# コンテナ内に入りclickhouse-clientを起動する方法

```shell
docker exec -it clickhouse clickhouse-client
```

抜ける場合は`exit`を実行する。

# dbeaverへの接続

ポートが8123の場合は以下の情報で接続できる。

※ ユーザーを作成した場合は、ユーザー名とパスワードも入力する。

- Host
    - localhost
- port
    - 8123

- User name
    - testuser
- Password
    - password
