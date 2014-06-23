## backtraceコマンド

**backtrace**  

### コマンド仕様
#### 前提条件
- なし。

#### 処理概要
- 呼出履歴情報を基にスタックトレース情報を表示する。
ソースファイル名、行番号も表示する。

#### 事後条件
- なし

#### 表示内容

```
(hoge.rb:10) backtrace
#0  func1 () at hoge.rb:10
#1  func2 () at hoge.rb:20
#2  main () at main.rb:5
(hoge.rb:10)
```

#### 異常系処理
- なし

#### 使用API
```
mrb_value mrb_get_backtrace(mrb_state *mrb)
```
- 戻り値  
スタックトレース情報（String型のArrayオブジェクト）  
`['func1 () at hoge.rb:10', 'func2 () at hoge.rb:20', 'main () at main.rb:5']`
- 処理内容  
`mrb_state*`の呼出履歴情報を基に、スタックトレース情報を格納する

#### 内部処理仕様
- データ構造
- データ更新内容
- シーケンス
