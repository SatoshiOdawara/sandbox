## displayコマンド

**display expr**  
expr 評価する式

### コマンド仕様
#### 前提条件
- なし。

#### 処理概要
(コマンド実行時)
- display番号を採番し、exprを登録する。
- display番号を表示する。
- print exprを実行する。
- 例外発生時は display番号を削除する。

(break(watch)によるプログラム停止時)
- 表示対象（display登録済かつ有効）について下記を行う。（登録の逆順で表示）
- display番号を表示する。
- print exprを実行する

#### 事後条件
(コマンド実行後)
- display番号を採番し、exprを登録する
- 例外発生時は display番号を削除する。

(break(watch)によるプログラム停止後)
- 例外発生時は display番号を削除する。

#### 表示内容

```
(hoge.rb:10) display 
(hoge.rb:10) display  foo
1: foo = 123
(hoge.rb:10) display bar
2: bar = "abc"
(hoge.rb:10) display  
2: bar = "abc"
1: foo = 123
(hoge.rb:10) continue
Breakpoint 1,  xxx () at hoge.rb:10
2: bar = "abc"
1: foo = 123
(hoge.rb:10)
```

#### 異常系処理
|異常状態|処理内容|
|----|----|
|パラメータなし|(break(watch)によるプログラム停止時)と同様に振る舞う|
|expr 評価時に例外が発生|評価結果を表示し、display番号を削除する。（デバッガの動作を継続する）|

#### 使用API
[printコマンド](print.md)と同じ

#### 内部処理仕様
- データ構造
- データ更新内容
- シーケンス
