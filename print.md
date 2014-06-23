## printコマンド

**print [expr]**  
expr 評価する式

### コマンド仕様
#### 前提条件
- なし。

#### 処理概要
- eval expr の結果を表示する。
- expr が空の場合は、前回の表示内容を表示する。
- evalで例外が発生した場合は例外内容を表示する。
- exprにローカル変数を含む場合の検討が必要。

#### 事後条件
- print番号を採番し、評価結果を保存する

#### 表示内容

```
(hoge.rb:10) print
The history is empty
(hoge.rb:10) print foo
$1 = 123
(hoge.rb:10) print bar
$2 = ”abc”
(hoge.rb:10) print
$3 = ”abc”
(hoge.rb:10) print baz
$4 = undefined method 'baz' for xxx (NoMethodError)
(hoge.rb:10) print
$5 = undefined method 'baz' for xxx (NoMethodError)
(hoge.rb:10)
```

#### 異常系処理
|異常状態|処理内容|
|----|----|
|パラメータなし<出力履歴がない>|`The history is empty`を表示する。|
|expr 評価時に例外が発生|評価結果を表示する。（デバッガの動作を継続する）|

#### 使用API
```
mrb_value mrb_debug_eval(mrb_state *mrb, const char *expr, mrb_irep *irep, mrb_code *pc)
```
- 戻り値  
exprの評価結果
- 処理内容  
指定されたコンテキスト（irep,pc）でexpr を評価する


#### 内部処理仕様
- データ構造
- データ更新内容
- シーケンス
