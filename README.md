利用方法
====

起動
----

```
docker-compose up -d
```

停止
----

```
docker-compose down
```

初期設定
----

一度起動することで、設定ファイル(gitlab/config/gitlab.rb)が作成されます。
これをカスタマイズします。
以下の設定をこのファイルの最後に追加します。

```
external_url 'http://<IPアドレスまたはホスト名>:8780'
mattermost_external_url 'http://<IPアドレスまたはホスト名>:8880'
```

この設定を有効にするために、以下を実行します。

```
docker exec -it gitlab gitlab-ctl reconfigure
```

GitLabを利用するには、以下のURLにアクセスします。

`http://<IPアドレスまたはホスト名>:8780`

Mattermostを利用するには、以下のURLにアクセスします。

`http://<IPアドレスまたはホスト名>:8880`

