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

GitLab Runnerの設定例
----

以下のように設定します。入力するのは `(★)` の行です。
ここで使用する GitLabの URLや tokenは、GitLabの `Admin Area > Runners` のページで取得しておきます。

```
$ docker exec -it gitlab-runner gitlab-runner register  (★)
Running in system-mode.

Please enter the gitlab-ci coordinator URL (e.g. https://gitlab.com/):
http://<IPアドレスまたはホスト名>:8780  (★)
Please enter the gitlab-ci token for this runner:
xxxxxxxxxxxxxxxxxxxxxx  (★)
Please enter the gitlab-ci description for this runner:
[localhost]:   (★)
Please enter the gitlab-ci tags for this runner (comma separated):
docker-compose  (★)
Registering runner... succeeded                     runner=caiccE6y
Please enter the executor: docker+machine, docker-ssh, parallels, ssh, virtualbox, docker, shell, docker-ssh+machine, kubernetes:
docker  (★)
Please enter the default Docker image (e.g. ruby:2.1):
alpine:latest  (★)
Runner registered successfully. Feel free to start it, but if it's running already the config should be automatically reloaded! 
```

PlantUMLの設定
----

GitLabの `Admin Area > Settings` ページの `PlantUML` 設定の URLとして以下を入力して、

`http://<IPアドレスまたはホスト名>:8089`

`Enable PlantUML` をチェックしてください。

GitLabの Wikiや Issueなどで、PlantUMLを利用できるようになります。

