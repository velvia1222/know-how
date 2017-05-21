# Vim標準
## 文字検索
| key      | action                 |
|:---------|:-----------------------|
| f string | stringを検索           |
| F string | stringを逆方向に検索   |
| ;        | 次の文字を検索         |
| ,        | 次の文字を逆方向に検索 |

## 変換
| key | action             |
|:----|:-------------------|
| ~   | 大文字小文字の変換 |

## 抽出
| key         | action                   |
|:------------|:-------------------------|
| :v/string/d | stringを含まない行を削除 |
| :g/string/d | stringを含む行を削除     |

## quickfix
| key    | action                   |
|:-------|:-------------------------|
| :copen | quickfixウィンドウを開く |
| :cn    | 次のファイルに移動する   |
| :cN    | 前のファイルに移動する   |

## vimdiff
| key | action                            |
|:----|:----------------------------------|
| ]c  | 次の差分に移動                    |
| [c  | 前の差分に移動                    |
| dp  | 左の差分を右にマージ(diff put)    |
| do  | 右の差分を左にマージ(diff obtain) |

# マッピング
| key            | action                                               |
|:---------------|:-----------------------------------------------------|
| cy             | カーソル位置の単語をヤンクした単語に置換             |
| C-Up<br>C-Down | 同じインデントに移動                                 |
| gp             | 直前にペーストしたテキストを再選択する               |
| ,fc            | カレントディレクトリを現バッファのディレクトリに移動 |
| C-w .          | quickfixを開く（:copen)                              |
| ,temp          | 一時ファイルを開いてカレントバッファの内容を出力する |

# プラグイン使用
## unite
| key     | action                       |
|:--------|:-----------------------------|
| C-l     | キャッシュをクリアする       |
| C-r,C-w | カーソル位置の単語を入力する |

## fugitive
| key            | action                |
|:---------------|:----------------------|
| :Gstatus       | git status            |
| C-n(Gstatus中) | 次のファイルに移動    |
| C-p(Gstatus中) | 前のファイルに移動    |
| D(Gstatus中)   | git diff              |
| -(Gstatus中)   | 対象をadd、reset      |
| :Gread         | git checkout filename |
| :Gdiff         | git diff              |
| :Gblame        | git blame             |
| :Glog          | git log               |
| :Gwrite        | git add               |
| :Gcommit       | git commit            |
| :Gpush         | git push              |
| :Gpull         | git pull              |
| :Gfetch        | git fetch             |
| :Gmerge        | git merge             |
| :Gcd           | gitルートにcd         |
| :Glcd          | gitルートにlcd        |

## tcomment_vim
| key | action                   |
|:----|:-------------------------|
| gcc | コメントアウトのオンオフ |

## vim-markdown
| key  | action           |
|:-----|:-----------------|
| :Toc | 見出し一覧を表示 |

## jedi-vim
| key | action                               |
|:----|:-------------------------------------|
| C-[ | 定義へ移動（\dをリマップ）           |
| \g  | 宣言へ移動                           |
| \n  | 使用箇所を表示                       |
| K   | カーソル下の単語のドキュメントを開く |
| \R  | 変数をリネーム（\rをリマップ）       |
