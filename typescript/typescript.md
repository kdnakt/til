
### 非同期関数の型

- (param: string) => Promise<string>

### Option Objectパターン
  
- https://typescriptbook.jp/reference/functions/keyword-arguments-and-options-object-pattern
- AWS-CDKとかでよく見る `MyObject('name', { ... })` でパラメータをオプションオブジェクトとして渡すやつ
- デフォルト引数の位置引数は省略できない問題を解決できる
  - `myFunc(undefined, undefined, 'foo')` みたいにしなくてよくなる
  - `myFunc({name: 'foo'})`
