# コマンド
| command                                 | action                                                        |
|:----------------------------------------|:--------------------------------------------------------------|
| git branch ブランチ名                   | ブランチを追加                                                |
| git checkout -b ブランチ名              | ブランチを追加して切り替え                                    |
| git branch -m 旧ブランチ名 新ブランチ名 | ブランチ名を変更                                              |
| git add -A                              | 追加、変更、削除されたファイルをadd                           |
| git reset                               | addを取り消し                                                 |
| git diff --staged                       | ステージと最新コミットの差分を表示                            |
| git commit -a                           | 変更されたファイルを自動add＆コミット                         |
| git log                                 | コミット履歴を表示                                            |
| git log --pretty=oneline                | コミット履歴を1行ごとに表示                                   |
| git log --oneline                       | コミット履歴を短縮IDで1行ごとに表示                           |
| git log -p ファイルパス                 | 特定のファイルの変更履歴を見る                                |
| git show コミットID                     | コミットの詳細を見る                                          |
| git commit --amend                      | 直前のコミットコメントを修正する                              |
| git stash                               | 変更を退避する                                                |
| git stash save -u                       | untrackedも含めて変更を退避する                               |
| git stash list -p                       | stashの一覧を表示                                             |
| git stash show スタッシュID             | 変更したファイル一覧を表示                                    |
| git stash apply スタッシュID            | スタッシュを取り出す                                          |
| git stash drop スタッシュID             | スタッシュを削除                                              |
| git stash pop スタッシュID              | スタッシュを取り出して削除                                    |
| git rebase -i コミットID                | 指定したコミットIDのコミットを修正                            |
| git rebase -i HEAD~n                    | HEADからHEAD~nまでのコミットを修正                            |
| (続き)pickをeditに変更して保存          | editにしたコミットを過去から順に編集できる                    |
| (続き)git addやamendを行う              |                                                               |
| (続き)git rebase --continue             | 次のコミットの編集に進む                                      |
| git rm                                  | gitの管理対象からファイルを削除し、ファイル自体も削除         |
| git rm -r                               | gitの管理対象からディレクトリを削除し、ディレクトリ自体も削除 |
| git rm --cached                         | gitの管理対象からのみ削除する                                 |
| git checkout ファイルパス               | ローカルの変更をファイル単位で取り消す                        |
| git checkout .                          | ローカルの変更を取り消す。新規追加は削除されない              |
| git clean -df                           | Untrackedファイルとディレクトリを削除                         |
| git reset --hard origin/master          | ローカルブランチをリモートブランチで上書き                    |
| git branch -d ブランチ名                | ローカルブランチを削除する                                    |
| git push --delete origin ブランチ名     | リモートブランチを削除する                                    |
| git fetch --prune                       | リモートで削除されているブランチを自動削除                    |
