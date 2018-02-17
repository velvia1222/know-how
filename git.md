# コマンド
| command                             | action                                                        |
|:------------------------------------|:--------------------------------------------------------------|
| git branch ブランチ名               | ブランチを追加                                                |
| git checkout -b ブランチ名          | ブランチを追加して切り替え                                    |
| git add -A                          | 追加、変更、削除されたファイルをadd                           |
| git commit -a                       | 変更されたファイルを自動add＆コミット                         |
| git log                             | コミット履歴を表示                                            |
| git log --pretty=oneline            | コミット履歴を1行ごとに表示                                   |
| git log --oneline                   | コミット履歴を短縮IDで1行ごとに表示                           |
| git log -p ファイルパス             | 特定のファイルの変更履歴を見る                                |
| git show コミットID                 | コミットの詳細を見る                                          |
| git commit --amend                  | 直前のコミットコメントを修正する                              |
| git rebase -i コミットID            | 指定したコミットIDのコミットを修正                            |
| git rebase -i HEAD~n                | HEADからHEAD~nまでのコミットを修正                            |
| (続き)pickをeditに変更して保存      | editにしたコミットを過去から順に編集できる                    |
| (続き)git addやamendを行う          |                                                               |
| (続き)git rebase --continue         | 次のコミットの編集に進む                                      |
| git rm                              | gitの管理対象からファイルを削除し、ファイル自体も削除         |
| git rm -r                           | gitの管理対象からディレクトリを削除し、ディレクトリ自体も削除 |
| git rm --cached                     | gitの管理対象からのみ削除する                                 |
| git checkout ファイルパス           | ローカルの変更をファイル単位で取り消す                        |
| git checkout .                      | ローカルの変更を取り消す。新規追加は削除されない              |
| git reset --hard origin/master      | ローカルブランチをリモートブランチで上書き                    |
| git branch -d ブランチ名            | ローカルブランチを削除する                                    |
| git push --delete origin ブランチ名 | リモートブランチを削除する                                    |
