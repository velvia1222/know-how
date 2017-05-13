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

# マッピング
| key            | action                                               |
|:---------------|:-----------------------------------------------------|
| ,fc            | カレントディレクトリを現バッファのディレクトリに移動 |
| cy             | カーソル位置の単語をヤンクした単語に置換             |
| C-Up<br>C-Down | 同じインデントに移動                                 |
| gp             | 直前にペーストしたテキストを再選択する               |
| ,temp          | 一時ファイルを開いてカレントバッファの内容を出力する |

# プラグイン使用
## unite
| key     | action                       |
|:--------|:-----------------------------|
| C-l     | キャッシュをクリアする       |
| C-r,C-w | カーソル位置の単語を入力する |

## fugitive
| key                     | action                |
|:------------------------|:----------------------|
| :Gstatus                | git status            |
| :Gwrite                 | git add               |
| :Gcommit                | git commit            |
| :Git push origin master | git push 〜           |
| :Gread                  | git checkout filename |
| :Gdiff                  | git diff              |
| :Gblame                 | git blame             |
| :Glog                   | git log               |

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
| K   | カーソル下の単語のドキュメントを開く |
