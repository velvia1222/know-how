# 起動方法
- ./script.sh
	- サブシェルが起動され、サブシェルでスクリプトが実行される
	- カレントシェルの環境変数を引き継ぐ(カレントの環境変数をコピーする)
	- カレントシェルのシェル変数は引き継がない
	- サブシェルでカレントから引き継がれた環境変数を変更しても、カレントの環境変数は変更されない
	- ファイルの先頭にシバン（#!/bin/bash）が必要
	- 実行権限が必要
- bash script.sh
	- シバンが不要
	- 上記以外は./script.shと同様
- . ./script.sh
	- カレントシェルでスクリプトが実行される
	- カレントシェルの環境変数やシェル変数を引き継ぐ
	- script.shで実行された設定が元のシェルに反映される
	- 実行権限が不要
- source ./script.sh
	- . ./script.shと同様

# 終了ステータス
- 明示しない場合は、最後に実行したコマンドの終了ステータスがシェルスクリプトの終了ステータスになる
- 明示的に指定する場合は、下記のように記述する

		exit 終了ステータス

# クォートと変数展開
|              | シングルクォート | ダブルクォート |
|:-------------|:-----------------|:---------------|
| 変数展開     | 行われない       | 行われる       |
| コマンド置換 | 行われない       | 行われる       |
- クォートで囲む必要のある文字
	- ; & ( ) | ^ < > ? * [ ] $ " \` { } 改行 タブ スペース
- ダブルクォート内で$を出力する際は、\でエスケープする

# コマンド置換
- $(コマンド)と\`コマンド\`の2種類ある
- バッククォートでコマンド置換を入れ子にする際は、\\でエスケープする必要がある

# 算術式展開
- exprコマンドは遅い。算術を行う際は二重括弧を使用する

		((i++))

- 算術結果を取得する場合は$をつける

		echo $((i + 2))

# ブレース展開
		mkdir test{1..10}
		touch test.{txt,csv,tsv}
- 連続した文字列に展開した後にコマンドが実行される

# グループピング
| command                 | action                             |
|:------------------------|:-----------------------------------|
| (コマンド; コマンド)    | コマンドをサブシェルで実行する     |
| { コマンド; コマンド; } | コマンドをカレントシェルで実行する |

- 中括弧を1行で使う場合、最後のコマンドに;が必須。また、中括弧の前後にスペースが必須

# シェル変数の初期化
| command     | action                                       |
|:------------|:---------------------------------------------|
| ${変数:=値} | 未使用nullの場合に値を代入する               |
| ${変数:-値} | 未使用nullの場合に値を返す                   |
| ${変数:?値} | 未使用nullの場合に値を表示して処理を終了する |
| ${変数:+値} | 未使用nullでない場合に値を返す               |
| unset 変数  | 変数を削除する                               |
- :は省略可能。:付きの場合は未使用またはnullの場合、:無しの場合は未使用の場合のみ上記の挙動となる

# パラメータ展開
| 記述          | 意味                       |
|:--------------|:---------------------------|
| ${変数#条件}  | 最短前方一致した部分を削除 |
| ${変数##条件} | 最長前方一致した部分を削除 |
| ${変数%条件}  | 最短後方一致した部分を削除 |
| ${変数%%条件} | 最長後方一致した部分を削除 |
- 条件にはワイルドカードも使用可能
- 下記記述で拡張子を削除する

		${filename%.*}

# 位置パラメータと特殊パラメータ
| 変数 | 格納値                                               |
|:-----|:-----------------------------------------------------|
| $0   | シェルスクリプト実行時のスクリプト名                 |
| $1〜 | 位置パラメータ。コマンドライン引数の値が格納される   |
| $#   | コマンドライン引数の個数                             |
| $@   | 引数全体を参照する。"$@"は"$1" "$2"と展開される      |
| $*   | 引数全体を参照する。"$*"は"$1 $2"と展開される        |
| $?   | 直前のコマンドの終了ステータスが格納される           |
| $$   | 直前のコマンドのプロセスID                           |
| $!   | 直前にバックグラウンドで実行したコマンドのプロセスID |
| $-   | シェル実行時のオプション                             |
- \*等のワイルドカードを使用した場合は、展開後の値が位置パラメータに格納される
- 10番目以降の引数は`${10}`のように中括弧で囲む必要がある

# getoptsコマンド
- オプションを順に取り出すコマンド
- 値を必要とするオプションには:を付ける
- 「command -ab -c 文字列 -d 文字列 文字列」というコマンドの場合は、以下のように使用する

		while getopts abc:d: OPT
		do
			case $OPT in
				a) コマンド
					;;
				b) コマンド
					;;
				c) 変数=文字列等
					;;
				d) 変数=文字列等
					;;
				\?) コマンド
					echo エラー！
					;;
			esac
		done
		shift 'expr $OPTIND - 1'

	- 最後のshiftコマンドにより、$1がオプション以外の最初の引数を指すようになる

# IFS
- IFSを変更することで、bashが単語を区切る際の文字を変更することができる
- デフォルトは、スペース、タブ、改行
- 変更する際は、他のコマンドに影響を与えないようにバックアップをとる

		_IFS=$IFS
		IFS=$'\n'
		処理
		IFS=$_IFS

# if文
## 構造
	if コマンド; then
		コマンド
	elif コマンド; then
		コマンド
	else
		コマンド
	fi
- ifの後のコマンドを実行し、終了ステータスが0の場合は真、そうでない場合は偽と判定する

## testコマンド
	if [ "$1" = "open" ]; then
- testコマンドは引数で指定された条件を判定し、正しければ0、そうでなければ0以外を終了ステータスとして返す
- 上記の文は以下の要素からなっている

| 文字列 | 意味         |
|:-------|:-------------|
| [      | testコマンド |
| "$1"   | 引数1        |
| =      | 引数2        |
| "open" | 引数3        |
| ]      | 引数4        |
- [コマンドとtestコマンドはほぼ一緒。[コマンドには引数に]が必須

## 演算子
| 演算子                      | 比較内容                         |
|:----------------------------|:---------------------------------|
| 文字列 = 文字列             | 文字列が等しい                   |
| 文字列 != 文字列            | 文字列が等しくない               |
| -n 文字列                   | 文字列が空文字列ではない         |
| -z 文字列                   | 文字列が空文字列                 |
| 整数 -eq 整数               | 整数が等しい                     |
| 整数 -ne 整数               | 整数が等しくない                 |
| 整数1 -lt 整数2             | 整数1が整数2より小さい           |
| 整数1 -le 整数2             | 整数1が整数2以下                 |
| 整数1 -gt 整数2             | 整数1が整数2より大きい           |
| 整数1 -ge 整数2             | 整数1が整数2以上                 |
| -e ファイル                 | ファイルが存在する               |
| -d ディレクトリ             | ディレクトリが存在する           |
| -h シンボリックリンク       | シンボリックリンクが存在する     |
| -L シンボリックリンク       | シンボリックリンクが存在する     |
| -f 通常のファイル           | 通常のファイルが存在する         |
| -r ファイル                 | ファイルが存在し、読み取り可能   |
| -w ファイル                 | ファイルが存在し、書き込み可能   |
| -x ファイル                 | ファイルが存在し、実行可能       |
| -s ファイル                 | ファイルサイズが0より大きい      |
| ファイル1 -nt ファイル2     | ファイル1がファイル2より新しい   |
| ファイル1 -ot ファイル2     | ファイル1がファイル2より古い     |
| 条件 -a 条件                | AND。両方の条件が真の場合に真    |
| 条件 -o 条件                | OR。いずれかの条件が真の場合に真 |
| !条件                       | NOT。条件の真偽を逆にする        |
| 条件1 -a \(条件2 -o 条件3\) | 条件1かつ（条件2または条件3）    |

## コマンドの条件判定
| command                                   | action                                                        |
|:------------------------------------------|:--------------------------------------------------------------|
| コマンド1 && コマンド2                    | コマンド1の終了ステータスが0の場合のみコマンド2を実行する     |
| コマンド1 &#124;&#124; コマンド2          | コマンド1の終了ステータスが0以外の場合のみコマンド2を実行する |
| if testコマンド && testコマンド           | 両方のtestコマンドが真の場合に真                              |
| if testコマンド &#124;&#124; testコマンド | いずれかのtestコマンドが真の場合に真                          |

# case文
## 構造
	case 文字列 in
		条件1)
			処理
			;;
		条件2)
			処理
			;;
		条件3|条件4)
			処理
			;;
	esac
- 条件にはワイルドカードを使用可能。最後に*)を書くとデフォルト処理になる
- 条件に|を使用することで複数の条件を記述可能

# 配列
## 構造
	変数=()
	変数=(文字列 文字列 文字列)

## 要素の追加
	変数[1]=文字列
	変数+=( 文字列 )

## 要素の取得
	$変数[1]

# for文
## 構造
	for 変数 in リスト
	do
		処理
	done
- リストには、スペースやタブ、改行で区切られた単語の羅列を指定する。ワイルドカードも指定可能
- seqコマンドを使用すると、下記のように連番を使った処理が可能

		for i in seq 1 10
		do
			処理
		done

- 引数を元にループする際は、以下のように記述する

		for p in "$@"
		do
			処理
		done

- `in リスト`の部分を省略した場合は、上記と同様の引数のループになる

# while文
## 構造
	while コマンド
	do
		処理
	done
- コマンドの終了コードが0である限りループ処理を行う

# select文
- 対話型のメニューを実現する
## 構造
	select 変数 in リスト
	do
		処理
	done

# シェル関数
## 構造
	function 関数名 ()
	{
		処理
	}
- functionまたは()のどちらかを省略可能

		function 関数名
		関数名 ()

## 使い方
	関数名

	関数名 引数1 引数2
- 呼び出す前に定義しておく必要がある
- 引数は位置パラメータ$1、$2で取得可能。ただし、特殊パラメータの$0は関数名ではなく関数を呼び出したシェルスクリプト名になる
- 明示的に指定しない場合は、最後に実行されたコマンドの終了ステータスが関数の終了ステータスになる
- 終了ステータスを明示的に指定する場合は、returnコマンドを使用する

		return 終了ステータス

- 通常はカレントシェルで動作するが、リダイレクトを使用した場合はサブシェルで動作する

		関数呼び出し > result.txt

	- サブシェルで動作

## 関数内の変数のスコープ
- 関数内で宣言した変数も、スクリプト全体がスコープとなる
- 1つのシェルスクリプト内で複数の関数を使用する場合、ある関数と他の関数で同じ変数名を使用していると同じ変数として処理される
- スコープを関数内に限定したい場合は、localコマンドを使用する

		local 変数="$1"

# ヒアドキュメント
- 複数行のテキストをコマンドの標準入力へ渡す

		cat << END
		テキスト
		END

- テキスト全体を変数展開したくない場合は、下記のようにEOF文字列をエスケープする

		cat << \END
		テキスト
		END

- 行頭のタブを無視したい場合は、下記のように-をつける

		cat <<- END
			テキスト
		END
