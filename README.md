# コマンド仕様
## printコマンド

'''
print expr
'''

## パラメータ
- expr 評価する式

## 前提条件
- なし。

## 処理概要
- eval expr の結果を表示する。
- evalで例外が発生した場合は例外内容を表示する。
- exprにローカル変数を含む場合の検討が必要。

## 表示内容
{code}
(hoge.rb:10) print foo
$1 = 123
(hoge.rb:10) print bar
$2 = ”abc”
(hoge.rb:10) print
$3 = ”abc”
(hoge.rb:10)
{/code}

## 異常系処理
- パラメータなしの場合
ぱらめーたをしていしてください的な・・・

## 内部処理仕様
### データ構造
### データ更新仕様

