## enable displayコマンド

**enable display [dispno]**  
dispno display情報

### コマンド仕様
#### 前提条件
- なし。

#### 処理概要
- 登録済 display 情報について、指定された display 番号の display 情報を有効化する。
- 指定された番号の display 情報が存在しない場合はエラー表示する。
- display番号が指定されない場合、全display情報を有効化する。

#### 事後条件
- 登録済 display 情報について、指定された display 番号の display 情報を有効化する。

#### 表示内容

```
(hoge.rb:10) info display
Num Enb Expression
2:   n  bar
1:   n  foo
(hoge.rb:10) enable display 3
No display number 3.
(hoge.rb:10) enable display 0
No display number 0.
(hoge.rb:10) enable display -1
Arguments must be display numbers.
(hoge.rb:10) enable display a
Arguments must be display numbers.
(hoge.rb:10) enable display 0x01
Arguments must be display numbers.
(hoge.rb:10) enable display 1
(hoge.rb:10) info display
Num Enb Expression
2:   n  bar
1:   y  foo
(hoge.rb:10) enable display
(hoge.rb:10) info display
Num Enb Expression
2:   y  bar
1:   y  foo
```

#### 異常系処理
|異常状態|処理内容|
|----|----|
|指定された番号の display 情報が存在しない|`No display number x.`を表示する。（x:指定されたdisplay番号）|
|数字以外で指定された(例．'a', -1, 0x01)|`Arguments must be display numbers.`を表示する。|
※８進数表現(010)は異常と見なしてよいか --> gdbは 010 = 10 として扱う

#### 使用API
なし

#### 内部処理仕様
- データ構造
- データ更新内容
- シーケンス
