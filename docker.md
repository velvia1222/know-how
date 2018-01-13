# docker
| command                  | action                                   |
|:-------------------------|:-----------------------------------------|
| docker image build       | Dockerfileからイメージを作成             |
| docker image history     | イメージで実行されたコマンドの履歴を表示 |
| docker image rm          | イメージを削除                           |
| docker image prune       | 使用していないイメージを削除             |
| docker image ls          | イメージ一覧を表示                       |
| docker image pull        | イメージをレジストリから取得             |
| docker container create  | コンテナを作成                           |
| docker container start   | 停止中のコンテナを起動                   |
| docker container stop    | 実行中のコンテナを停止                   |
| docker container restart | コンテナを再起動                         |
| docker container run     | コンテナを作成して起動                   |
| docker container run -it | コンテナをバックグランドで起動           |
| docker container run -d  | コンテナをバックグランドで起動           |
| docker container run -e  | 環境変数を設定してコンテナを起動する     |
| docker container exec    | 実行中のコンテナ内でコマンドを実行       |
| docker container rm      | コンテナを削除                           |
| docker container prune   | 停止中の全コンテナを削除                 |
| docker container ls      | コンテナ一覧を表示                       |
| docker container stats   | コンテナの状況を表示                     |
| docker container top     | コンテナ内で実行しているプロセスを表示   |
| docker container port    | コンテナが使用しているポートを表示       |

#docker-compose
| command                | action                                 |
|:-----------------------|:---------------------------------------|
| docker-compose build   | docker-compose.ymlからイメージを作成   |
| docker-compose up      | コンテナを作成して起動                 |
| docker-compose start   | 停止中のコンテナを起動                 |
| docker-compose stop    | 実行中のコンテナを停止                 |
| docker-compose run     | コンテナを作成して起動                 |
| docker-compose restart | コンテナを再起動                       |
| docker-compose down    | コンテナを停止して削除                 |
| docker-compose ps      | コンテナ一覧を表示                     |
| docker-compose top     | コンテナ内で実行しているプロセスを表示 |
| docker-compose port    | コンテナが使用しているポートを表示     |
