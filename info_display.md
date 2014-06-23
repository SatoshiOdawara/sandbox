## info displayコマンド

**info display**  

### コマンド仕様
#### 前提条件
- なし。

#### 処理概要
登録済 display 情報について下記を行う。(登録の逆順で表示)
- display 番号を表示する。
- 有効/無効状態を表示する。
- expr を表示する。

#### 事後条件
なし

#### 表示内容

```
(hoge.rb:10) info display 
There are no display expressions.
(hoge.rb:10) display  foo
1: foo = 123
(hoge.rb:10) display bar
2: bar = "abc"
(hoge.rb:10) info display
Num Enb Expression
2:   y  bar
1:   y  foo
(hoge.rb:10) disable display 1
(hoge.rb:10) info display
Num Enb Expression
2:   y  bar
1:   n  foo
```

#### 異常系処理
|異常状態|処理内容|
|----|----|
|登録済 display 情報がない|`There are no display expressions.`を表示する|

#### 使用API
なし

#### 内部処理仕様
- データ構造
- データ更新内容
- シーケンス
